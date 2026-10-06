# Qaza Namaz Tracker: Publish karne ki guide

Is folder mein poori app hai. Neeche ke steps tarteeb se karein.

## Folder mein kya hai

| File | Kaam |
|---|---|
| `index.html` | Poori app (13 zabanein, calculator, tracker, backup) |
| `manifest.json` | App ka naam, icon aur rang, taake phone ise app samjhe |
| `sw.js` | App ko internet ke bagair bhi chalata hai |
| `privacy.html` | Privacy policy (Play Store ke liye zaroori) |
| `icons/` | App ke icons |

**Pehle ye zaroor karein:** `privacy.html` kholein aur `YOUR-EMAIL@example.com` ki jagah apna email likhein.

---

## Step 1: Website par lagayein (GitHub Pages, muft)

1. **github.com** par free account banayein.
2. Upar **+** → **New repository**. Naam rakhein, jaise `qaza-tracker`. **Public** chunein → **Create repository**.
3. **"uploading an existing file"** link par click karein. Is zip ke **andar ki saari files aur `icons` folder** drag karke daal dein (zip khud nahi, uske andar ka saman). Neeche **Commit changes** dabayein.
4. Repository mein **Settings** → baayein taraf **Pages**.
5. **Source**: "Deploy from a branch". **Branch**: `main`, folder `/ (root)` → **Save**.
6. 1–2 minute baad link milega: `https://AAP-KA-USERNAME.github.io/qaza-tracker/`

**Check karein:** ye link phone ke Chrome mein kholein. Menu (⋮) → **Add to Home screen** / **Install app**. App home screen par aa jayegi aur bina internet bhi chalegi.

Yahin se aap WhatsApp par link share kar sakte hain. iPhone wale Safari mein khol kar **Share → Add to Home Screen** karein.

---

## Step 2: Android app ki file banayein (PWABuilder, muft)

1. **pwabuilder.com** kholein, apni GitHub Pages wali link dalein → **Start**.
2. Report card aayega. Manifest aur service worker green hone chahiye.
3. **Package for stores** → **Android** → **Generate Package**.
   - **Package ID**: kuch aisa rakhein `io.github.aapkausername.qazatracker` (baad mein badal nahi sakte).
   - App name: `Qaza Namaz Tracker`, Short name: `Qaza Tracker`.
4. Download hone wale zip mein milega:
   - `.aab` file → ye Play Store par upload hogi
   - **signing key** file aur us ka password → **inhe hamesha sambhal kar rakhein** (Google Drive par bhi copy). Ye gum ho gayi to app update nahi kar sakenge.
   - `assetlinks.json` → is ko agle step mein lagana hai

### assetlinks.json lagana (zaroori)
Is se app ke upar browser wali address bar nahi dikhti.
1. GitHub repository mein **Add file → Create new file**.
2. Naam likhein: `.well-known/assetlinks.json`
3. PWABuilder wali `assetlinks.json` ka saara text paste karein → **Commit**.

> Note: GitHub Pages par repository ke andar ho to ye file `username.github.io/qaza-tracker/.well-known/` par hogi, jabke Android ise domain ki root par dhoondta hai. Agar app mein upar address bar nazar aaye, to sab se aasaan hal ye hai ke repository ka naam `aapkausername.github.io` rakhein (taake app root par ho), ya apna domain (.com) le lein.

---

## Step 3: Google Play Console

1. **play.google.com/console** par account banayein. **$25 ek dafa** fee. Shanakhti card se verification hoti hai.
2. **Create app**: naam `Qaza Namaz Tracker`, App, **Free**.
3. **Store listing** (neeche tayyar text hai), icon `icons/icon-512.png`, aur phone ke kam az kam 2 screenshots.
4. **App content** mein:
   - **Privacy policy**: `https://AAP-KA-USERNAME.github.io/qaza-tracker/privacy.html`
   - **Ads**: No
   - **Data safety**: "No data collected" aur "No data shared" (app sab kuch phone mein rakhti hai)
   - **Content rating**: questionnaire bharein (koi tashaddud/fahashi nahi) → Everyone
   - **Target audience**: 13+ ya 18+
5. **Closed testing** (naye personal account ke liye lazmi):
   - **Testing → Closed testing → Create track**, `.aab` upload karein.
   - Testers ki email list banayein. **Kam az kam 12 log, lagataar 14 din** opt-in rehne chahiye. Agar 12 se kam hue to 14 din dobara shuru hote hain, isliye **20–25 log** daal dein (dost, rishtedar, class fellows).
   - Testers ko link bhejein, wo "Become a tester" dabayein aur app install karein.
6. 14 din baad **Production access** ke liye apply karein, phir **Production** mein release karein. Google review mein kuch din lag sakte hain.

### Store listing ka text

**Short description (80 characters):**
Calculate and track your missed qaza prayers. Private, free, 13 languages.

**Full description:**
Qaza Namaz Tracker helps you make up missed (qaza) prayers, one step at a time.

• Simple calculator: enter your age, the age you reached puberty and how often you prayed. The app estimates how many prayers you owe.
• For sisters: average period days are subtracted, since those prayers are not made up.
• Witr optional, for Hanafi and other schools.
• Tap +1 after each qaza prayer and watch your remaining count go down.
• Daily goal ring, streaks, per-prayer progress, recent history and estimated finish date.
• 13 languages: English, Urdu, Arabic, Persian, Turkish, Indonesian, Malay, Bengali, Hindi, French, Swahili, Russian and Norwegian.
• Completely private: no account, no ads, no tracking. Everything stays on your phone.
• Works offline. Back up and restore your progress anytime.

Estimates are based on your honest best guess. For your own situation, please consult a scholar you trust.

---

## Step 4: iPhone App Store (baad mein)

- **$99 har saal** Apple Developer fee, Mac + Xcode chahiye.
- PWABuilder **iOS** package bhi banata hai, lekin Apple sirf website wali apps aksar reject karta hai. Pehle notifications (namaz ke reminders) jaise features add karne honge.
- Tab tak iPhone wale log Safari se **Add to Home Screen** kar ke app istemal kar sakte hain.

---

## App update kaise karein
1. GitHub repository mein `index.html` (ya koi file) badlein.
2. `sw.js` mein `qaza-v1` ko `qaza-v2` kar dein, taake logon ke phone purana version chhor kar naya lein.
3. Play Store wali app khud nayi website load kar legi. Naya `.aab` sirf tab chahiye jab naam, icon ya package settings badlein.

## Zaroori yaad-dihani
- Signing key aur password **kabhi mat khoyein**.
- Tarjume Claude ne kiye hain. Publish se pehle har zaban koi native bolne wala dekh le.
- Qaza ka hisaab andaza hai. App mein bhi likha hai ke apni surat-e-haal ke liye kisi mo'tabar aalim se poochein.
