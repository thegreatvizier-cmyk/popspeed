# Popspeed — holding page

Statická coming-soon stránka pro popspeed.co.uk. Žádný build, čistá statika.

## Soubory
- `index.html` — stránka (inline CSS, drobný JS pro formulář)
- `favicon.svg` — ikona „p."
- `og-image.png` — náhled pro sdílení (1200×630)
- `vercel.json` — clean URLs

## Nasazení na Vercel (přes Git)
1. Založ repo a pushni obsah této složky.
2. Na Vercelu: Add New → Project → naimportuj repo.
3. Framework Preset: **Other**. Build command i Output directory nech prázdné (statika).
4. Deploy.

## Doména popspeed.co.uk
V projektu → Settings → Domains přidej `popspeed.co.uk` i `www.popspeed.co.uk`.
Vercel vypíše konkrétní DNS hodnoty — řiď se jimi (ne hodnotami z paměti).
Typicky:
- apex `popspeed.co.uk` → A záznam na Vercel IP (Vercel ji ukáže), nebo ALIAS/ANAME, pokud to registrátor umí.
- `www` → CNAME na `cname.vercel-dns.com`.

## E-mailový formulář (Formspree)
1. Zaregistruj se na formspree.io a vytvoř nový formulář.
2. Zkopíruj endpoint (formát `https://formspree.io/f/YOUR_FORM_ID`).
3. V `index.html` ho vlož do konstanty `FORM_ENDPOINT` (nahoře ve `<script>`).
4. V nastavení formuláře na Formspree **vypni reCAPTCHA** (jinak AJAX odeslání
   selže), nebo doplň vlastní reCAPTCHA klíč.
5. Do „authorized domains" přidej `popspeed.co.uk`, ať formulář nejde zneužít odjinud.

První odeslaný e-mail musíš na Formspree potvrdit (ověření adresy). Spam řeší
skrytý honeypot `_gotcha`, který je už ve formuláři. Free tier má měsíční limit
počtu odeslání — aktuální hodnotu si ověř v ceníku Formspree.

Dokud zůstane `FORM_ENDPOINT` na `YOUR_FORM_ID`, formulář místo falešného „díky"
zobrazí chybu — žádné předstírání, že se někdo přihlásil.
