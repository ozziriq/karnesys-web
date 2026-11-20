# KarneSys 3D – Webbplats (`KarneSys.karnehall.com`)

Statisk webbplats för **KarneSys 3D** i Landskrona, byggd för GitHub Pages utan externa ramverk eller byggsteg.

## Så lägger du till ett nytt inlägg i Bygglogg & Galleri

1. **Lägg in bilderna i mappen `bilder/`**  
   Spara dina foton eller bilder (t.ex. `.jpg`, `.webp`, `.png` eller `.svg`) i mappen `bilder/`, gärna med korta filnamn utan mellanslag (t.ex. `bilder/drake-1.jpg`, `bilder/drake-2.jpg`).

2. **Lägg till en post i `posts.json`**  
   Öppna `posts.json` och klistra in ett nytt block längst upp i listan `[ ... ]` (glöm inte kommatecknet mellan blocken). Använd `"images"` för flera vinklar på samma projekt (eller `"image"` + `"alt"` om du bara har en bild):

   ```json
   {
     "id": "unikt-namn-pa-projektet",
     "title": "Titel på utskriften",
     "date": "2026-11-20",
     "category": "Rollspel",
     "material": "Hyper PLA Stardust",
     "printerInfo": "0.4 mm munstycke • Creality K1 Max",
     "images": [
       {
         "src": "bilder/ditt-filnamn-1.jpg",
         "alt": "Helhetsbild framifrån"
       },
       {
         "src": "bilder/ditt-filnamn-2.jpg",
         "alt": "Närbild på detaljer"
       }
     ],
     "notes": "Korta bygganteckningar om munstycke, material eller resultat."
   }
   ```
   Filterknapparna, bildkarusellen och sorteringen (nyast först) uppdateras automatiskt utifrån `posts.json`.

3. **Förhandsgranska lokalt (valfritt)**  
   Eftersom webbläsare blockerar `posts.json` och `filaments.json` via `file://`, kör en lokal testserver i den här mappen vid behov:
   ```bash
   python -m http.server 8000
   ```
   Öppna sedan `http://localhost:8000/bygglogg.html` eller `http://localhost:8000/filament.html`.

4. **Publicera till GitHub Pages**  
   Lägg till, committa och pusha ändringarna med Git så uppdateras `https://KarneSys.karnehall.com` automatiskt.

## Filamentlager (`filaments.json`)

Sidan `filament.html` hämtar aktuellt utbud av färger och material från `filaments.json` (med fält för `brand`, `materialGroup`, `material`, `colorName`, `colorHex`, `status`, `bestFor` och `updatedAt`).

- `materialGroup` använder korta, tydliga gruppnamn för filtrering (t.ex. `PLA`, `PLA Starry`, `PETG`).
- När du köper nytt filament eller ändrar status (`I lager`, `Beställningsvara`, `Slut`) kan du uppdatera `filaments.json` direkt, eller använda Antigravity-skillen **`filament-inventory`** som uppdaterar lagret automatiskt åt dig.
