# Adat-szerver Dokumentáció

## Leírás
Ez az egyszerű Node.js + Express alapú szerver egy JSON fájlból szolgáltat adatokat HTTP GET kérésekre. A szerver célja, hogy a `data.json` fájlban tárolt hardvertermékek adatait elérhetővé tegye API-n keresztül.

## Telepítés

1. Győződj meg róla, hogy Node.js telepítve van.
2. Hozd létre a projekt könyvtárat, majd inicializáld:

```bash
npm init -y
```

3. Telepítsd a szükséges csomagokat:

```bash
npm install express
```

4. Helyezd el a `data.json` fájlt a `src` mappában a következő tartalommal:

```json
[
  { "id": 1, "nev": "Processzor", "tipus": "Intel Core i5-12400F", "ar": 65000, "keszlet": 12, "kategoriа": "CPU" },
  { "id": 2, "nev": "Videókártya", "tipus": "NVIDIA RTX 3060", "ar": 145000, "keszlet": 5, "kategoriа": "GPU" },
  { "id": 3, "nev": "Alaplap", "tipus": "MSI B660M-A DDR4", "ar": 42000, "keszlet": 8, "kategoriа": "Motherboard" },
  { "id": 4, "nev": "RAM", "tipus": "Kingston Fury 16GB DDR4", "ar": 28000, "keszlet": 20, "kategoriа": "Memória" },
  { "id": 5, "nev": "SSD", "tipus": "Samsung 980 500GB NVMe", "ar": 27000, "keszlet": 15, "kategoriа": "Tárhely" }
]
```

5. Helyezd el a szerver kódot `index.js` vagy `server.js` fájlba:

```js
import express from "express";
import { readFileSync } from "fs";

const app = express();
const PORT = 3000;

app.get("/adatok", (req, res) => {
  const raw = readFileSync("./src/data.json", "utf-8");
  const json = JSON.parse(raw);
  res.json(json);
});

app.listen(PORT, () => {
  console.log(`Szerver fut: http://localhost:${PORT}`);
});
```

## Használat

1. Indítsd el a szervert:

```bash
node index.js
```

2. Nyisd meg a böngészőt vagy használd a `curl`-t a JSON adatok lekéréséhez:

```
http://localhost:3000/adatok
```

3. A szerver válasza egy JSON tömb lesz a hardver termékekről:

```json
[
  { "id": 1, "nev": "Processzor", "tipus": "Intel Core i5-12400F", "ar": 65000, "keszlet": 12, "kategoriа": "CPU" },
  ...
]
```

## Megjegyzés
  -Postman test képek mellékeéve.
  -Chat gpt használt promtok: 
    - [ { "id": 1, "nev": "Péter", "kor": 17 }, { "id": 2, "nev": "Anna", "kor": 19 }, { "id": 3, "nev": "Laci", "kor": 16 } ] ird át és bövisd
    - csinálj egy md fáljba dokumentáciot
  

