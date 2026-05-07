# Read Consciously

Working Title — wird durch deinen finalen Namen ersetzt (global per Find-and-Replace). Eine wöchentliche Newsletter-Plattform für konstruktive Nachrichten und Lichtblicke. Auf Deutsch und Englisch. AI-kuratiert, redaktionell veredelt.

## Inhalt
- [Vision](#vision)
- [Was unterscheidet uns?](#was-unterscheidet-uns)
- [Inhalts-Säulen](#inhalts-säulen)
- [Architektur in drei Wellen](#architektur-in-drei-wellen)
- [Tech Stack](#tech-stack)
- [Repo-Struktur](#repo-struktur)
- [Setup](#setup)
- [AI-Pipeline](#ai-pipeline)
- [Content-Richtlinien](#content-richtlinien)
- [Roadmap](#roadmap)
- [Kosten-Übersicht](#kosten-übersicht)
- [Lizenz](#lizenz)

## Vision
Mehr und mehr Menschen leiden unter dem Doomscroll-Klima der Newsfeeds. Wir glauben, dass Journalismus auch das andere kann: zeigen, was funktioniert, wer Lösungen baut, wo Hoffnung trägt — ohne in Naivität oder Toxic Positivity zu verfallen.

**Unser Versprechen:**
- Faktenbasiert, nicht beschönigend.
- Lösungsorientiert, nicht polemisch.
- Tief, nicht oberflächlich.
- Inspirierend, nicht moralisierend.

Unsere Mission: Wöchentlich 5–8 sorgfältig kuratierte Geschichten zu liefern, die zeigen, wo Menschen gerade die Welt zum Besseren bewegen — und wie unsere Leser:innen daran anknüpfen können.

Zielgruppe: Bewusste Sinnsucher:innen, Conscious Leaders, Menschen die wissen, dass die Welt mehr braucht als Empörung.

## Was unterscheidet uns?
Es gibt bereits gute „Good News“-Newsletter (The Goodnewsletter, Good News Network, Positive News, The Optimist Daily, Reasons to Be Cheerful). Wir sind anders, weil wir:

| Andere | Wir |
|---|---|
| Kuratieren oberflächlich, klicken auf „feel good" | Solutions Journalism + Bewusstseinswandel |
| Sind passiv („Lies und freu dich") | Sind interaktiv (Likes, Kommentare, Aktion) |
| Übersetzen nicht | DE + EN parallel |
| Haben keine Community-Layer | Bauen Community von Anfang an mit ein |
| Sind statisch | AI-gestützt und durchsuchbar |

**Themen-Dimensionen:**
- Wirtschaft, die heilt (Doughnut-Ökonomie, Gemeinwohlökonomie, Kemfert)
- Klima & Regeneration (Perspective Daily, transform Magazin, RiffReporter)
- Nachbarschaft & Gemeinde (lokale Initiativen, Bürgerräte)
- Bewusstseinswandel (Eckhart Tolle, Lee Harris, Wilber, McIntosh, Spiral Dynamics)
- Demokratie & Beteiligung (Welzer, Nassehi, Göpel)
- Kultur & Beziehungen (Reckwitz, Rosa, Precht)
- Mental Health & Innere Resilienz
- Innovation mit Sinn

## Inhalts-Säulen
### Säule 1 — Lead Stories (3–5 pro Newsletter)
Mittlere bis lange Geschichten (300–800 Wörter). Mindestens eine pro Themen-Dimension. Mit konkreten Aktionsmöglichkeiten am Ende jeder Story.

### Säule 2 — Positive Shorts (3–5 pro Newsletter)
Kurze, emotional anschlussfähige Momente — wie der Sänger, der für eine weinende Frau am „Sit here if you're having a bad day“-Tisch singt. Format: Kuratierte Embed-Stories (TikTok, Reels, YouTube Shorts) + 2–3 Sätze Kontext + Quellenlink. Diese Säule ist ein Hauptdifferenzierer gegenüber Wettbewerbern.

### Säule 3 — Lichtblick der Woche
Eine Story aus den Shorts wird zum „Lichtblick der Woche“ gehoben — mit längerem Text, persönlicher Einordnung der Redaktion und Hintergrund über die Menschen dahinter.

### Säule 4 — Community-Stories (ab Welle 3)
Leser:innen reichen Geschichten aus ihrer Umgebung ein. Die Redaktion redigiert und veröffentlicht.

## Architektur in drei Wellen
Prinzip: Lieber wenig wirklich gut als alles halbgar. Jede Welle baut auf der vorigen auf.

### Welle 1 — MVP (4–6 Wochen)
Ziel: Etwas Echtes in der Welt, teilbar, mit ersten Leser:innen.
- ✅ Wöchentlicher Newsletter (DE primär, EN per Claude API übersetzt)
- ✅ Web-Feed mit Filtern (Thema, Region, Sprache)
- ✅ AI-Content-Pipeline (RSS + Claude-Klassifikation, Redaktion redigiert)
- ✅ Like-Button (anonym, ohne Login — Cookie/Fingerprint-basiert)
- ✅ Positive Shorts-Sektion

### Welle 2 — Personalisierung (Wochen 7–14)
Ziel: Tiefere Bindung durch personalisiertes Erlebnis.
- ⏳ User-Accounts (Supabase Auth via Magic Link)
- ⏳ Personalisierter Feed nach Themen
- ⏳ AI-Suche über das Story-Archiv (pgvector + RAG)
- ⏳ PWA / Push-Notifications

### Welle 3 — Community (Monat 4+)
Ziel: Aus Lesern werden Mitwirkende.
- ⏳ Kommentare (mit AI-Moderation gegen Toxicity)
- ⏳ Story-Einreichung durch Leser:innen
- ⏳ Helper-Profile / Karte lokaler Initiativen

## Tech Stack
| Layer | Tool | Kosten | Begründung |
|---|---|---:|---|
| Frontend | Next.js 15 (App Router) + Tailwind + shadcn/ui | 0€ | Branchen-Standard, AI-Code-Tools verstehen es perfekt |
| i18n | next-intl | 0€ | DE/EN von Tag 1 |
| Hosting | Vercel Hobby | 0€ | Free Tier reicht für MVP-Traffic |
| Datenbank | Supabase (Postgres) | 0€ | 500MB DB, 50k MAU im Free Tier |
| Auth | Supabase Auth | 0€ | Inklusive |
| Vector Search | pgvector (in Supabase) | 0€ | Inklusive |
| Email-Versand | Resend | 0–18€ | Free bis 3k Mails/Monat, Pro 20$ ab dann |
| Email-Templates | react-email | 0€ | Komponenten als Code, perfekt für AI-Generierung |
| AI-Layer | Anthropic Claude API | ~3–10€ | Sonnet 4.6 für Content, Haiku für Klassifikation |
| Analytics | Cloudflare Web Analytics | 0€ | Datenschutzfreundlich, kein Cookie-Banner nötig |
| Domain | INWX/Namecheap | ~1€/Monat | .de oder .com je nach Brand |
| Code-Editor | VS Code + Claude Code / Codex CLI | 0€ | gstack-Workflow möglich |
| Repo | GitHub | 0€ | Free Tier |

Phase 1 (MVP): ~4–8€/Monat  
Phase 2 (mit Resend Pro): ~25€/Monat  
Klar unter dem 30€-Budget.

## Repo-Struktur
```text
goodnewsletter/
├── README.md
├── CLAUDE.md
├── .env.example
├── .gitignore
├── package.json
├── next.config.ts
├── tailwind.config.ts
├── tsconfig.json
├── middleware.ts
├── docs/
│   ├── VISION.md
│   ├── THEMES.md
│   ├── COMPETITIVE_ANALYSIS.md
│   ├── PRODUCT_REQUIREMENTS.md
│   ├── CONTENT_GUIDELINES.md
│   ├── ARCHITECTURE.md
│   └── ROADMAP.md
├── supabase/
│   ├── migrations/
│   │   └── 0001_initial_schema.sql
│   └── seed.sql
├── src/
│   ├── app/
│   │   ├── [locale]/
│   │   │   ├── page.tsx
│   │   │   ├── feed/page.tsx
│   │   │   ├── shorts/page.tsx
│   │   │   ├── search/page.tsx
│   │   │   ├── story/[slug]/page.tsx
│   │   │   ├── submit/page.tsx
│   │   │   └── layout.tsx
│   │   ├── api/
│   │   │   ├── newsletter/route.ts
│   │   │   ├── like/route.ts
│   │   │   └── search/route.ts
│   │   ├── globals.css
│   │   └── layout.tsx
│   ├── components/
│   │   ├── layout/
│   │   ├── story/
│   │   └── shorts/
│   ├── lib/
│   │   ├── supabase/
│   │   ├── claude/
│   │   ├── i18n/
│   │   └── utils.ts
│   ├── messages/
│   │   ├── de.json
│   │   └── en.json
│   └── emails/
│       └── weekly-newsletter.tsx
└── scripts/
    └── ai-pipeline/
        ├── sources.ts
        ├── curate.ts
        ├── embed.ts
        └── translate.ts
```

## Setup
### Voraussetzungen
- Node.js 20+ (nvm install 20)
- pnpm (npm install -g pnpm)
- Git
- VS Code mit Claude Code oder Codex CLI

### Schritt 1: Repo initialisieren
```bash
git clone https://github.com/<dein-username>/goodnewsletter.git
cd goodnewsletter
pnpm install
```

### Schritt 2: Accounts anlegen (alle Free Tier)
- [Supabase](https://supabase.com/) — neues Projekt erstellen
- [Resend](https://resend.com/) — API-Key erstellen, Domain verifizieren
- [Anthropic Console](https://console.anthropic.com/) — API-Key erstellen, $5–10 Guthaben aufladen
- [Vercel](https://vercel.com/) — Account verbinden mit GitHub
- [Cloudflare](https://cloudflare.com/) — Domain übertragen + Web Analytics aktivieren

### Schritt 3: Environment-Variablen
```bash
cp .env.example .env.local
# Werte aus den Account-Dashboards einfügen:
# - NEXT_PUBLIC_SUPABASE_URL
# - NEXT_PUBLIC_SUPABASE_ANON_KEY
# - SUPABASE_SERVICE_ROLE_KEY
# - ANTHROPIC_API_KEY
# - RESEND_API_KEY
# - NEXT_PUBLIC_SITE_URL
```

### Schritt 4: Datenbank-Schema einspielen
```bash
brew install supabase/tap/supabase
supabase login
supabase link --project-ref <dein-project-ref>
supabase db push
```

### Schritt 5: Lokal starten
```bash
pnpm dev
# → http://localhost:3000
```

### Schritt 6: AI-Pipeline manuell testen
```bash
pnpm tsx scripts/ai-pipeline/curate.ts
# Aggregiert RSS-Feeds, klassifiziert, schreibt Kandidaten in Supabase
```

### Schritt 7: Deployen
```bash
git push origin main
# Vercel deployt automatisch
```

## AI-Pipeline
Ablauf (wöchentlich, Sonntags 06:00 Uhr via Vercel Cron):

1. **RSS-Aggregation** (`sources.ts`)  
   11 Feeds werden geladen — die letzten 7 Tage.
2. **Klassifikation** (Claude Haiku 4.5)  
   Jeder Eintrag wird auf `is_goodnews`, `theme`, `region`, `confidence` geprüft. Threshold: ≥0.7.
3. **Story-Generierung** (Claude Sonnet 4.6)  
   Top 30 Kandidaten werden zu strukturierten Stories umgeschrieben (`title`, `summary`, `body_markdown`, `actions`).
4. **Übersetzung** (Claude Haiku, optional)  
   DE → EN für internationale Reichweite.
5. **Redaktion** (menschliche Schicht)  
   Du erhältst eine Liste mit Status `review`. Du redigierst, wählst die finalen 5, setzt auf `published`.
6. **Newsletter-Versand** (Resend)  
   React-Email-Template wird mit den 5 Stories + 3–5 Positive Shorts gefüllt. Versand an Subscribers.

Geschätzte Kosten pro Woche: ~$0.60 (≈ 0,55€). Pro Monat ≈ 2,40€.

## Content-Richtlinien
### Solutions-Journalism-Standards
Jede Story muss enthalten:
- Was ist das Problem? Kontext, ohne zu lange zu verweilen
- Was ist die Lösung? Wer macht was, wie, warum
- Welche Wirkung wurde gemessen? Zahlen, Zeitraum, Quelle
- Welche Limitationen gibt es? Was funktioniert nicht, was bleibt offen
- Wie kann ich anknüpfen? Konkrete Aktion: spenden, mitmachen, weiterlesen

### Tonalität
- Klar, nicht kitschig. Keine Worte wie „magisch", „wundervoll", „unglaublich".
- Editorial, nicht boulevardesk. Wir sind näher an Hohe Luft als an BILD.
- Hoffnungsvoll, nicht moralisierend. Wir zeigen, was funktioniert. Wir predigen nicht.
- Faktentreu. Quellen, Zahlen, Belege immer.

### Was wir NICHT veröffentlichen
- „Cute animal“-Stories ohne Tiefe
- Promi-Wohltätigkeit ohne strukturelle Wirkung
- Greenwashing-PR von Unternehmen
- Stories ohne überprüfbare Quelle
- Toxic Positivity („Alles wird gut, wenn du nur positiv denkst")

## Roadmap
### Welle 1 — MVP (Wochen 1–6)
| Woche | Meilenstein |
|---:|---|
| 1 | Repo-Setup, Supabase, Vercel, Domain, Brand-Identität |
| 2 | Datenbank-Schema, Auth-Flow (vorbereitet), Basis-Layout |
| 3 | AI-Pipeline (RSS + Klassifikation), erste 20 Stories generieren |
| 4 | Newsletter-Template (react-email), Resend-Integration, Anmeldeformular |
| 5 | Web-Feed, Like-Button, Positive Shorts-Sektion |
| 6 | Soft-Launch an Freundeskreis, erste Iteration, Feedback einholen |

### Welle 2 — Personalisierung (Wochen 7–14)
| Wochen | Meilenstein |
|---:|---|
| 7–8 | User-Accounts via Supabase Magic Link |
| 9–10 | Personalisierter Feed nach Themen-Präferenzen |
| 11–12 | AI-Suche mit pgvector + RAG |
| 13–14 | PWA / Push-Notifications |

### Welle 3 — Community (Monat 4+)
| Monat | Meilenstein |
|---:|---|
| 4 | Kommentar-Funktion mit AI-Moderation |
| 5 | Story-Einreichung durch Leser:innen |
| 6 | Helper-Profile / Karte lokaler Initiativen |

## Kosten-Übersicht
### Phase 1 (MVP, 0–500 Subscriber)
| Posten | Kosten |
|---|---:|
| Supabase Free | 0€ |
| Resend Free (3.000 Mails/Monat) | 0€ |
| Vercel Hobby | 0€ |
| Anthropic API (~1 Run/Woche) | ~3€ |
| Cloudflare Web Analytics | 0€ |
| Domain | ~1€ |
| Total | ~4–5€/Monat |

### Phase 2 (500–5.000 Subscriber)
| Posten | Kosten |
|---|---:|
| Supabase Free (noch genug) | 0€ |
| Resend Pro (50.000 Mails/Monat) | 18€ |
| Vercel Hobby | 0€ |
| Anthropic API | ~6€ |
| Cloudflare | 0€ |
| Domain | ~1€ |
| Total | ~25€/Monat |

### Phase 3 (5.000+ Subscriber)
| Posten | Kosten |
|---|---:|
| Supabase Pro | 25€ |
| Resend Pro | 18€ |
| Vercel Pro | 20€ |
| Anthropic API | ~15€ |
| Cloudflare | 0€ |
| Domain | ~1€ |
| Total | ~80€/Monat (aber dann ist Monetisierung möglich) |

## Nächste Schritte für dich
- Brand-Name finalisieren und in der README per Find-and-Replace ersetzen
- Domain prüfen und kaufen (INWX oder Namecheap, ~12€/Jahr)
- GitHub-Repo erstellen und diese README + CLAUDE.md committen
- Supabase- und Resend-Accounts anlegen
- Zurück zu mir kommen für die Generierung der Konzept-Dokumente in `/docs` und des Code-Skeletts

## Lizenz
MIT — siehe [LICENSE](LICENSE).

Letztes Update: Mai 2026  
Status: Pre-MVP, Konzept-Phase  
Maintainer: (dein Name hier)
