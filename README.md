# Gyakorlati Git és VS Code Útmutató Kezdőknek

Üdvözlünk ebben a gyakorlati Git útmutatóban! Ez a tananyag úgy lett felépítve, hogy egy teljesen kezdő is lépésről lépésre végig tudjon menni rajta a Visual Studio Code (VS Code) és a **Git Graph** bővítmény segítségével.

Nem elméleti szárazanyagot találsz itt, hanem egy valós tanulási folyamatot: látni fogod a pontos lépéseket, az útközben felmerülő buktatókat, a gyakori kérdéseket és a felmerülő problémák vizuális megoldását.

---

## Előfeltételek és Előkészületek

Mielőtt belevágnál a gyakorlatba, telepítsd a szükséges eszközöket az alábbi hivatalos hivatkozásokról:

1. **Visual Studio Code (VS Code):**
   * **Leírás:** Modern, ingyenes kódszerkesztő felület.
   * **Letöltési link:** [code.visualstudio.com/download](https://code.visualstudio.com/download)

2. **Git Verziókövető Rendszer:**
   * **Leírás:** A fájlok és projektállapotok nyomon követéséért felelős alaprendszer.
   * **Letöltési link (Windows / macOS / Linux):** [git-scm.com/downloads](https://git-scm.com/downloads)

3. **Git Graph Bővítmény (VS Code Extension):**
   * **Leírás:** Vizuális grafikon nézet a VS Code-on belül, amivel láthatod a commitokat, ágakat és merge-eket.
   * **Telepítés a VS Code-on belül:** Nyisd meg a szerkesztőben a bal oldali sávon az Extensions fület (`Ctrl + Shift + X`), keress rá a `Git Graph` névre, majd kattints az **Install** gombra.
   * **Webes adatlap / Marketplace link:** [marketplace.visualstudio.com/items?itemName=mhutchie.git-graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph)

---

## 1. Modul: Az Alapok – Lokális Repó és Commitok

Ebben a modulban létrehozod az első projektet és megérted, hogyan követi a Git a fájlok változásait.

### Lépések:

1. Hozz létre egy új üres mappát a gépeden (pl. `test-git` néven).
2. Nyisd meg ezt a mappát a VS Code-ban (`File -> Open Folder`).
3. Hozz létre egy új fájlt `index.html` vagy `teszt.txt` néven, és írj bele pár sort.
4. Nyisd meg a bal oldali **Source Control** fület (Git ikon a bal sávban).

### Fájlok állapota és a mentési folyamat:

* **`U` (Untracked):** Az új fájlod mellett egy `U` betű látható. Ez azt jelenti, hogy a Git látja a fájlt, de még nem követi a változásait.
* **Stagelés (`+` gomb):** Kattints a fájl melletti `+` jelre. A fájl átkerül a *Staged Changes* szekcióba (állapota `A` lesz). Ezzel kijelölted a fájlt a következő mentésre.
* **Commit készítése:** Írj egy rövid üzenetet a fenti szövegdobozba (pl. *"Első commit - teszt fájl létrehozva"*), majd kattints a **Commit** (vagy pipa) gombra.

> **Kezdő kérdés / Gyakori elakadás:**
>
> *„Módosítottam a fájlt, de ha rámentek a commitra, nem történik semmi vagy hibaüzenetet kapok. Miért?”*
>
> **Válasz:** A Git kétlépcsős biztonsági rendszert használ: nem elég elmenteni a fájlt a szerkesztőben (`Ctrl + S`), explicit módon be kell tenned az előkészítőbe a `+` gombra kattintva (Stagelés), és csak utána tudsz commitolni!

---

## 2. Modul: Kísérletezés Veszélyek Nélkül – Az Ágak (`Branch`)

Soha ne a fő kódon (`main`) kísérletezz! Az ágak segítségével biztonságos játszóteret hozhatsz létre.

### Lépések:

1. Nyisd meg a **Git Graph** nézetet (alsó sáv vagy parancsikon).
2. Kattints jobb egérgombbal a legutolsó commitodra, és válaszd a **"Create Branch..."** opciót.
3. Nevezd el az ágat (pl. `konfliktus-teszt` vagy `kiserlet`).
4. Válts át az új ágra (Check out). Ezt a Git Graph-on duplán rákattintva, vagy a VS Code bal alsó sarkában az ág nevére kattintva teheted meg.
5. Módosítsd a fájlt ezen az ágon, stageld (`+`), és commitold (pl. *"Kísérleti sor hozzáadása"*).

*Megjegyzés:* Ha visszaváltasz a `main` ágra, a fájlból eltűnik az új sor. Ha visszaváltasz a kísérleti ágra, újra megjelenik. Ez a Git varázslata!

---

## 3. Modul: Összevonás és Konfliktuskezelés (`Merge Conflict`)

Mi történik, ha két külön ágon ugyanazt a sort módosítjuk, majd megpróbáljuk őket egyesíteni? **Konfliktus!** Ne ijedj meg, ez teljesen természetes.

### Így idézz elő és oldj meg egy konfliktust a gyakorlatban:

1. Válts vissza a **`main`** ágra.
2. Módosítsd az `index.html` fájl **3. sorát** erre: `Main ág verziója`. Commitold.
3. Válts át a **`konfliktus-teszt`** ágra.
4. Módosítsd ugyanannak a fájlnak a **3. sorát** erre: `Kísérleti ág verziója`. Commitold.
5. Válts vissza a **`main`** ágra.
6. A Git Graph-on kattints jobb klikkel a `konfliktus-teszt` ágra, és válaszd a **"Merge into current branch"** opciót.

### A Konfliktus Feloldása a VS Code Vizuális Szerkesztőjével:

A VS Code piros és kék kiemeléssel mutatja a két eltérő kódot.

* **Current Change:** A `main` ág kódja.
* **Incoming Change:** A beolvasztandó ág kódja.

**A feloldás lépései:**

1. Kattints a szöveg feletti opciók egyikére (pl. *Accept Current Change*, *Accept Incoming*, vagy szerkeszd meg kézzel a végleges sort).
2. Mentsd el a fájlt (`Ctrl + S`).
3. **KRITIKUS LÉPÉS:** A bal oldali *Source Control* panelen kattints a fájl melletti **`+` (Stage)** gombra!
4. Kattints a **Continue** (vagy *Commit*) gombra a felül megjelenő gombok közül.

> **Kezdő kérdés / Gyakori elakadás:**
>
> *„Kiválasztottam a jó kódot és elmentettem, de a Commit/Continue gomb szürke és nem enged továbblépni. Mit rontottam el?”*
>
> **Válasz:** Elmaradt a Stagelés! A Git tudni akarja, hogy explicit módon jóváhagytad-e a javítást. Amint megnyomod a fájl mellett a `+` jelet, a *Continue* gomb azonnal aktívvá válik.

---

## 4. Modul: Titokvédelem és a `.gitignore` meglepetései

Bizalmas adatokat (jelszavak, API kulcsok) a `.env` fájlban tárolunk, amit **tilos** commitolni.

### Lépések:

1. Hozz létre egy `.gitignore` nevű fájlt a projekt gyökerében.
2. Írd bele ezt a sort: `.env`
3. Hozz létre egy `.env` fájlt, és írj bele tetszőleges jelszót.
4. Megfigyelés: A `.env` fájl szürkévé válik a VS Code-ban, és a Git teljesen figyelmen kívül hagyja.
5. Commitold a `.gitignore` fájlt (pl. *".gitignore fájl hozzáadva"*).

---

## 5. Modul: Időutazás – A `Revert` és a `Reset`

Mi van, ha egy korábbi állapothoz szeretnénk visszatérni?

### A Revert kipróbálása:

1. A Git Graph-on kattints jobb gombbal a *.gitignore hozzáadása* commitra.
2. Válaszd a **Revert...** opciót.

> **Kezdő kérdés / Gyakori elakadás:**
>
> *„A Revert után hirtelen megjelent a Source Controlban a `.env` fájlom Untracked (`U`) státusszal. Miért történt ez, és hova tűnt a `.gitignore`?”*
>
> **Válasz:** A `Revert` nem visszaugrik az időben, hanem **új commitot készít, ami megfordítja a kiválasztott commit hatását**. Mivel az a commit hozta létre a `.gitignore`-t, a Revert kitörölte azt! Mivel a pajzs (tiltólista) eltűnt, a Git hirtelen meglátta a gépeden lévő `.env` fájlt.

### A Revert visszacsinálása (ha hibáztunk):

1. Kattints jobb gombbal a legfrissebb (Revert) commitra a Git Graph-on.
2. Válaszd újra a **Revert...** opciót (Revert a Revertre).
3. A `.gitignore` újraéled, a `.env` pedig azonnal eltűnik a megfigyelt fájlok közül!

---

## 6. Modul: Kísérleti Ágak Kitakarítása és Távoli Repók Klónozása (`Clone`)

### Ágak törlése:
1. Nyisd meg a Git Graph-ot.
2. Kattints jobb egérgombbal a feleslegessé vált ágcímkére (pl. `konfliktus-teszt`).
3. Válaszd a **Delete Branch** opciót.

### Távoli Repó Klónozása (`Clone`):
Amikor egy már létező külső projektet szeretnél letölteni a gépedre:

1. Nyomd meg a **`Ctrl + Shift + P`** billentyűkombinációt a VS Code-ban.
2. Írd be: **`Git: Clone`**
3. Illeszd be a távoli repó hivatkozását (pl. egy teszt link: `https://github.com/octocat/Spoon-Knife.git`).
4. Válaszd ki a céélmappát a számítógépeden.
5. Amikor megkérdezi, kattints az **Open in New Window** (vagy *Add to Workspace*) opcióra.

> **Kezdő kérdés / Gyakori elakadás:**
>
> *„Bekérte a GitHub bejelentkezésemet és leklónozta a repót a gépemre, de a saját GitHub fiókom oldalán nem jelent meg a projekt. Ez hibás működés?”*
>
> **Válasz:** Nem, ez teljesen normális! A **Clone** művelet csak a te helyi gépedre tölti le a kódot. Ha azt szeretnéd, hogy a saját online GitHub fiókodban is létrejöjjön a projekt másolata, először a GitHub felületén a **Fork** gombra kell kattintanod!
