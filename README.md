# 🚀 Aktieagenten – Deploy-guide för Vercel

## Vad innehåller projektet?

```
aktieagenten/
├── api/
│   └── claude.js        ← Backend-proxy (håller API-nyckeln hemlig)
├── public/
│   └── index.html       ← Din app
└── vercel.json          ← Vercel-konfiguration
```

---

## Steg 1 – Skaffa ett GitHub-konto
Om du inte redan har ett, gå till **github.com** och skapa ett gratis konto.

---

## Steg 2 – Ladda upp projektet till GitHub

1. Gå till **github.com/new**
2. Namnge repot `aktieagenten`
3. Klicka **"Create repository"**
4. Ladda upp alla filer genom att dra dem till sidan, eller använd:
   ```
   git init
   git add .
   git commit -m "första versionen"
   git remote add origin https://github.com/DITT-NAMN/aktieagenten.git
   git push -u origin main
   ```

---

## Steg 3 – Skaffa ett Vercel-konto
Gå till **vercel.com** → klicka **"Sign Up"** → välj **"Continue with GitHub"**

---

## Steg 4 – Importera projektet i Vercel

1. På Vercel-dashboarden, klicka **"Add New → Project"**
2. Välj ditt `aktieagenten`-repo
3. Klicka **"Deploy"** (inga inställningar behöver ändras)

---

## Steg 5 – Lägg till din hemliga API-nyckel ⚠️

Detta är det viktigaste steget – nyckeln ska ALDRIG läggas i koden!

1. Gå till ditt projekt på Vercel
2. Klicka på **"Settings"** (överst)
3. Klicka på **"Environment Variables"** (vänster meny)
4. Fyll i:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** din nyckel (börjar med `sk-ant-...`)
5. Klicka **"Save"**
6. Gå tillbaka till **"Deployments"** och klicka **"Redeploy"**

---

## Steg 6 – Klar! 🎉

Din app är nu live på en URL som ser ut så här:
`https://aktieagenten-dittnamn.vercel.app`

---

## Hämta din Anthropic API-nyckel

1. Gå till **console.anthropic.com**
2. Logga in / skapa konto
3. Klicka **"API Keys"** i vänstermenyn
4. Klicka **"Create Key"**
5. Kopiera nyckeln och spara den säkert

---

## Vanliga problem

| Problem | Lösning |
|---|---|
| "API error 401" | API-nyckeln är fel eller saknas i Vercel |
| Appen laddas inte | Kontrollera att `vercel.json` finns i rotmappen |
| "Method not allowed" | Kontrollera att `api/claude.js` finns |

---

## Uppdatera appen senare

Varje gång du ändrar en fil och pushar till GitHub uppdateras Vercel automatiskt inom ~30 sekunder.
