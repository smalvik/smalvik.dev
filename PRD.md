# PRD: Portfolio Website — Vitaly Smirnov

## Context

**Problem:** Vitaly Smirnov is a Product Manager with a technical background (9+ years), targeting remote positions in the US market. Currently, his online presence is limited to a GitHub profile README and LinkedIn. A dedicated portfolio/business-card website will serve as a centralized hub that showcases projects, career achievements, and provides a professional first impression for US recruiters.

**Target audience:** US-based recruiters and hiring managers searching for Product Managers and Full-Stack Developers.

**Key insight from research:** Recruiters spend 3-5 seconds deciding whether to stay on a page. The site must communicate value instantly, be mobile-first, and funnel visitors toward contact action.

---

## 1. Product Vision

A minimalist, high-converting portfolio website that positions Vitaly as a Product Manager with deep technical expertise. The site dynamically showcases GitHub projects and drives recruiters to initiate contact via LinkedIn.

---

## 2. User Persona

| Attribute | Value |
|---|---|
| Name | Vitaly Smirnov |
| Role | Product Manager / Tech Lead |
| Experience | 9+ years (Nexign, Sberbank) |
| Domain | HRTech, EdTech, LMS |
| Tech Stack | Node.js, TypeScript, React, GraphQL, Docker, PostgreSQL, Next.js |
| Education | SPbPU — Applied Informatics in Economics (2013) |
| Languages | Russian (native), English (B1) |
| Location | Saint Petersburg, Russia (open to relocation) |
| Contact | Telegram: @smalvik, Email: smirnovvitalik8@mail.ru |
| GitHub | github.com/smalvik |

---

## 3. Site Structure (Pages / Sections)

Single-page application (SPA) with smooth scroll navigation between sections:

### 3.1. Hero Section
- Full-name headline: **"Vitaly Smirnov"**
- Subtitle: **"Product Manager & Full-Stack Developer"**
- One-liner value proposition: *"I build and scale HRTech/EdTech products serving 100K+ users"*
- CTA button: "Let's Connect" → scrolls to contact section
- Secondary CTA: "View Projects" → scrolls to projects
- Animated background (subtle gradient or particle effect, respects theme)
- Social links row: GitHub, LinkedIn, Telegram

### 3.2. About Me
- Professional photo (placeholder slot)
- Brief bio (3-4 sentences from CV "About me"):
  - EN: "Product Manager with a technical background. I build and scale HRTech and EdTech products from zero to 100K+ users. Focused on metrics-driven growth and user experience. I communicate product value clearly and regularly present to teams and clients."
  - RU: Оригинальный текст из резюме
- Key stats in animated counters:
  - **9+** years experience
  - **100K+** users served
  - **12** team members managed
  - **7** interns grown to next grade
- Download CV button (PDF)

### 3.3. Experience Timeline
Vertical timeline with expandable cards:

**1. Product Manager — Nexign (Apr 2023 – Present)**
- Neon HRM: LMS, onboarding, career development, knowledge base
- Clients: Megafon, Pulkovo
- Key achievements (bullet metrics):
  - Launched LMS from scratch, MVP in 3 months
  - Integrated AI for content generation — 2x faster course prep
  - Course completion rate: 60% → 90% (CJM + Lean UX)
  - NPS +10-15 points after offline access
  - Load testing for 100K users
  - RICE prioritization, data-driven decisions, Scrum

**2. Tech Lead — Nexign (Apr 2020 – Mar 2023)**
- Built dev team from scratch, mentored 7 interns
- Stack: Node.js, React, TypeScript, GraphQL, Docker
- Automated onboarding → HR load -40%, onboarding time 5-7 days
- Unified UX, reduced support tickets

**3. Developer / Instructor — Nexign (Mar 2018 – Mar 2020)**
- Built learning planning system
- Taught JS, TS, React, GraphQL, Docker at ITMO, HSE for Megafon, YaDro

**4. Software Developer — Sberbank (Dec 2016 – Mar 2018)**
- Training planning for top management
- Telegram/Viber chatbot — support tickets -30-40%

### 3.4. Skills / Tech Stack
Visual grid of technology badges (similar to GitHub README but interactive):
- **Product:** Backlog Management, Stakeholder Management, RICE, CustDev, CJM, Lean UX, Scrum, Product Analytics
- **Frontend:** React, Next.js, TypeScript, JavaScript, HTML5, CSS3
- **Backend:** Node.js, GraphQL, Apollo Server, REST API
- **Infrastructure:** Docker, PostgreSQL, MongoDB, Redis, Nginx, Git
- **AI/ML:** AI integration for content generation

### 3.5. Projects (GitHub Showcase)
**Dynamic section that pulls data from GitHub API** (`api.github.com/users/smalvik/repos`).

Featured projects (manually curated, pinned):
| Repo | Description | Why it matters |
|---|---|---|
| apollo-server-4-demo | GraphQL + Apollo Server v4 | Shows modern API architecture skills |
| microservices | Microservices patterns | Demonstrates system design knowledge |
| nexign-job-offer-rest-0 | REST API demo | Practical backend skills |
| nexign-job-offer-graphql-0 | GraphQL demo | Modern API experience |
| leetcode_javascript_answers | LeetCode solutions in JS | Algorithmic thinking |
| algorithms_js | JS algorithms | CS fundamentals |

Each project card shows:
- Repository name + description (from GitHub API)
- Language badges (auto-detected)
- Stars / forks count
- Last updated date
- "View on GitHub" link
- Optional: live demo link

Filtering by technology tag (React, Node.js, GraphQL, etc.)

### 3.6. Education
- SPbPU — Applied Informatics in Economics (2013)
- College of Information Technologies — Programmer-Technician (2009)

### 3.7. Contact Section (Landing Page Best Practices)
**Goal: Convert visitors into LinkedIn connections / messages.**

- Headline: "Let's Build Something Together" / "Давайте создадим что-то вместе"
- Minimal contact form (max 3 fields based on conversion research):
  - Name
  - Email
  - Message
- CTA button: "Send Message" (not generic "Submit")
- **Primary action:** "Connect on LinkedIn" — large branded button
- **Secondary links:** GitHub, Telegram, Email
- Trust signal: "Open to remote opportunities worldwide"

**Form submission:** Apollo Client sends GraphQL mutation `sendContactMessage` to NestJS backend → NestJS validates, saves to PostgreSQL, sends email notification via Nodemailer.

### 3.8. Footer
- Copyright + year
- "Built with Next.js" badge
- Quick social links row
- Language switcher (duplicate)

---

## 4. Key Features

### 4.1. Language Switcher (EN / RU)
- **Placement:** Header, top-right corner (desktop), inside hamburger menu (mobile)
- **Labels:** "EN" / "RU" toggle buttons with native language names on hover
- **Implementation:** `next-intl` or `next-i18next` for Next.js
- **Default:** Detect browser `Accept-Language`, fallback to EN
- **Persistence:** Store preference in `localStorage`
- **SEO:** `hreflang` tags, `/en/` and `/ru/` URL prefixes
- All content fully translated (not machine-translated — manual review)

### 4.2. Dark / Light Theme Toggle
- **Placement:** Header, next to language switcher
- **Component:** MUI IconButton with `Brightness4` / `Brightness7` icons
- **Default:** Respect `prefers-color-scheme` via `useMediaQuery('(prefers-color-scheme: dark)')`
- **Persistence:** `localStorage`
- **Implementation:** MUI `ThemeProvider` + `createTheme()` with light/dark palettes
- **Colors:**
  - Dark: MUI dark palette (`background.default: #121212`, `primary.main: #90caf9`)
  - Light: MUI light palette (`background.default: #ffffff`, `primary.main: #1976d2`)
- **Contrast:** WCAG AA compliant (MUI defaults meet this)
- **Transition:** CSS transitions on `background-color` and `color` properties

### 4.3. GitHub API Integration
- **NestJS backend** proxies GitHub REST API (`github.service.ts`) with in-memory caching (TTL 1 hour)
- Frontend fetches via GraphQL query `repositories(featured: true)` through Apollo Client
- Display: stars, forks, language, description, last update
- Pinned/featured repos — configured in NestJS constants
- Fallback: NestJS returns cached data if GitHub API is rate-limited
- Next.js ISR on top for SSG pages (revalidate every hour)

### 4.4. Responsive Design (Mobile-First)
- Breakpoints: 320px (mobile), 768px (tablet), 1024px (desktop), 1440px (wide)
- Touch targets: minimum 48x48px
- Hamburger menu on mobile with language switcher inside
- Contact form fields optimized for mobile (83% of traffic is mobile)

### 4.5. Animations & Micro-interactions
- Scroll-triggered fade-in for sections (Intersection Observer)
- Counter animation for stats (About section)
- Hover effects on project cards
- Smooth scroll between sections
- Subtle parallax on hero (optional, performance-aware)
- **No heavy animations** — performance > flash

### 4.6. SEO & Performance
- Lighthouse score target: 95+
- Meta tags, Open Graph, Twitter Card
- Structured data (JSON-LD: Person schema)
- Sitemap.xml, robots.txt
- Image optimization (Next.js Image component)
- Web fonts: preload, `font-display: swap`

---

## 5. Tech Stack

### Frontend
| Layer | Technology | Rationale |
|---|---|---|
| Framework | **Next.js 14+ (App Router)** | SSR/SSG, ISR for GitHub data, shows React skills |
| Language | **TypeScript** | Demonstrates TS expertise from CV |
| UI Library | **Material UI (MUI) v6** | Component library, built-in theming (dark/light), responsive grid |
| Animation | **Framer Motion** | Smooth scroll animations, page transitions |
| i18n | **next-intl** | Lightweight, App Router compatible |
| Theme | **MUI ThemeProvider** | Dark/light toggle via MUI's built-in theming system |
| Forms | **React Hook Form + Zod** | Client-side validation |
| GraphQL Client | **Apollo Client** | GraphQL integration with NestJS backend |
| Deployment | **Vercel** | Free tier, perfect Next.js integration |

### Backend
| Layer | Technology | Rationale |
|---|---|---|
| Framework | **NestJS** | Enterprise-grade Node.js framework, shows backend expertise |
| Language | **TypeScript** | Full-stack type safety |
| API | **GraphQL (Apollo Server via @nestjs/graphql)** | Type-safe API, matches CV GraphQL experience |
| ORM | **Prisma** | Type-safe DB access, auto-generated types |
| Database | **PostgreSQL** | Stores contact form submissions, analytics |
| Email | **@nestjs-modules/mailer + Nodemailer** | Contact form email delivery |
| Validation | **class-validator + class-transformer** | DTO validation |
| Deployment | **Railway** or **Render** | Free tier, easy NestJS hosting |

### Shared
| Layer | Technology | Rationale |
|---|---|---|
| Monorepo | **Turborepo** | Shared types between frontend & backend |
| GraphQL Schema | **Code-first (NestJS)** | Auto-generated schema from decorators |
| Domain | Custom domain (e.g., `smalvik.dev`) | Professional impression |
| Analytics | **Plausible** | Privacy-friendly, no cookie banner |

---

## 6. Design Guidelines (Based on Behance & Recruiter Trends)

### Visual Style
- **Minimalist & clean** — content-first, no visual noise
- **Modern dark theme as default** (Behance trend: dark = elevated, professional)
- **Typography:** Roboto (MUI default) for body; Roboto Mono for code snippets
- **Accent color:** Blue (`primary.main` in MUI theme) — trust, technology, professionalism
- **Spacing:** MUI spacing system (8px base), generous whitespace
- **Cards:** MUI Card component with elevation, rounded corners

### Layout Principles (Recruiter-Optimized)
1. **5-second rule:** Value proposition visible without scrolling
2. **F-pattern scanning:** Key info top-left, CTA top-right
3. **Visual hierarchy:** Name → Role → Value prop → CTA
4. **Scannable content:** Bullet points, metrics in bold, short paragraphs
5. **Social proof:** Achievement metrics prominent (100K users, 7 mentored, etc.)

---

## 7. Content Strategy

### English (Primary — US recruiters)
- Professional tone, action verbs, metrics-heavy
- "Launched", "Scaled", "Reduced", "Increased" framing
- Focus on: impact, scale, technical depth

### Russian (Secondary — CIS market)
- Professional but slightly warmer tone
- Same structure, fully localized (not translated word-for-word)

---

## 8. Contact Form → LinkedIn Funnel

The contact form is NOT the primary conversion path. Based on recruiter research:

1. **Primary CTA:** "Connect on LinkedIn" button (opens LinkedIn profile in new tab)
2. **Secondary:** Contact form (name, email, message) → sends to Vitaly's email
3. **Tertiary:** Direct email link, Telegram link

The LinkedIn button should be:
- Visually prominent (branded blue, larger than form submit)
- Present in hero section AND contact section
- Text: "Connect on LinkedIn" (not just an icon)

---

## 9. Project File Structure (Turborepo Monorepo)

```
smalvik.dev/
├── turbo.json
├── package.json                     # Workspace root
├── PRD.md                           # This document
│
├── apps/
│   ├── web/                         # Next.js Frontend
│   │   ├── public/
│   │   │   ├── images/              # Photo, OG image, favicon
│   │   │   ├── cv/                  # Downloadable PDF resume (EN + RU)
│   │   │   └── fonts/
│   │   ├── src/
│   │   │   ├── app/
│   │   │   │   ├── [locale]/
│   │   │   │   │   ├── layout.tsx
│   │   │   │   │   └── page.tsx
│   │   │   │   └── layout.tsx
│   │   │   ├── components/
│   │   │   │   ├── Header.tsx              # Nav + theme toggle + lang switcher
│   │   │   │   ├── Hero.tsx
│   │   │   │   ├── About.tsx
│   │   │   │   ├── Experience.tsx          # Timeline
│   │   │   │   ├── Skills.tsx
│   │   │   │   ├── Projects.tsx            # GitHub integration
│   │   │   │   ├── ProjectCard.tsx
│   │   │   │   ├── Education.tsx
│   │   │   │   ├── Contact.tsx             # Form + LinkedIn CTA
│   │   │   │   ├── Footer.tsx
│   │   │   │   ├── ThemeToggle.tsx
│   │   │   │   └── LanguageSwitcher.tsx
│   │   │   ├── graphql/
│   │   │   │   ├── client.ts               # Apollo Client setup
│   │   │   │   ├── queries.ts              # GraphQL queries
│   │   │   │   └── mutations.ts            # GraphQL mutations
│   │   │   ├── lib/
│   │   │   │   └── constants.ts            # Featured repos, social links
│   │   │   ├── i18n/
│   │   │   │   ├── en.json
│   │   │   │   └── ru.json
│   │   │   └── styles/
│   │   │       └── globals.css
│   │   ├── next.config.ts
│   │   ├── theme.ts                  # MUI theme config (light + dark)
│   │   └── package.json
│   │
│   └── api/                          # NestJS Backend
│       ├── src/
│       │   ├── main.ts
│       │   ├── app.module.ts
│       │   ├── github/
│       │   │   ├── github.module.ts
│       │   │   ├── github.service.ts       # GitHub API integration + caching
│       │   │   └── github.resolver.ts      # GraphQL resolver
│       │   ├── contact/
│       │   │   ├── contact.module.ts
│       │   │   ├── contact.service.ts      # Email sending logic
│       │   │   ├── contact.resolver.ts     # GraphQL mutation
│       │   │   └── dto/
│       │   │       └── send-message.input.ts
│       │   └── prisma/
│       │       ├── prisma.module.ts
│       │       └── prisma.service.ts
│       ├── prisma/
│       │   └── schema.prisma               # DB schema (contact messages)
│       ├── nest-cli.json
│       └── package.json
│
└── packages/
    └── shared/                       # Shared types & utilities
        ├── src/
        │   └── types.ts              # Shared GraphQL types
        └── package.json
```

### GraphQL Schema (Code-First via NestJS)

```graphql
type Query {
  repositories(featured: Boolean): [Repository!]!
  repository(name: String!): Repository
}

type Mutation {
  sendContactMessage(input: SendMessageInput!): ContactResponse!
}

type Repository {
  name: String!
  description: String
  url: String!
  language: String
  stars: Int!
  forks: Int!
  updatedAt: DateTime!
  topics: [String!]!
  featured: Boolean!
}

input SendMessageInput {
  name: String!
  email: String!
  message: String!
}

type ContactResponse {
  success: Boolean!
  message: String!
}
```

---

## 10. MVP Scope (Phase 1)

Minimum for launch:
- [x] Hero section with name, role, value proposition, CTAs
- [x] About section with bio + stats
- [x] Experience timeline (4 positions)
- [x] Skills grid
- [x] Projects section (GitHub API + featured repos)
- [x] Contact form + LinkedIn CTA
- [x] Dark / light theme toggle
- [x] EN / RU language switcher
- [x] Mobile-responsive design
- [x] Deploy to Vercel

### Phase 2 (Post-launch)
- Blog / articles section
- Case study pages (detailed project breakdowns)
- Animated project demos (GIFs / videos)
- Testimonials / recommendations
- Custom domain + email
- Analytics dashboard

---

## 11. Success Metrics

| Metric | Target |
|---|---|
| Lighthouse Performance | 95+ |
| Mobile Lighthouse | 90+ |
| Time to Interactive | < 2s |
| Contact form submissions | Track monthly |
| LinkedIn clicks | Track via analytics |
| Bounce rate | < 40% |
| Average session duration | > 1 min |

---

## 12. Verification Plan

1. **Build:** `npm run build` — no errors
2. **Lighthouse:** Run audit, all scores 90+
3. **Responsive:** Test on 320px, 768px, 1024px, 1440px
4. **Theme:** Toggle dark/light, verify contrast ratios
5. **Language:** Switch EN↔RU, verify all text translated
6. **GitHub API:** Verify repos load, check fallback on rate limit
7. **Contact form:** Submit test message, verify email delivery
8. **Accessibility:** Tab navigation, screen reader, ARIA labels
9. **SEO:** Check meta tags, OG tags, structured data, sitemap
10. **Deploy:** Push to Vercel, verify production build

---

## 13. Critical Files to Create/Modify

| File | Purpose |
|---|---|
| `/home/smalvik/github/smalvik.dev/` | Project directory |
| `package.json` | Dependencies: next, react, tailwindcss, framer-motion, next-intl, next-themes |
| `src/app/[locale]/page.tsx` | Main page with all sections |
| `src/components/*.tsx` | All UI components (listed in structure above) |
| `src/lib/github.ts` | GitHub API integration |
| `src/i18n/en.json` + `ru.json` | Full translation files |
| `src/app/api/contact/route.ts` | Contact form API handler |
| `apps/web/src/theme.ts` | MUI theme config (light + dark palettes) |

---

## 14. Immediate Next Steps

1. Create directory `~/github/smalvik.dev/`
2. Save this PRD as `PRD.md` in the project root
3. Initialize git repo
4. Create GitHub repo `smalvik/smalvik.dev`
5. Push initial commit with PRD
6. Begin implementation (Phase 1 MVP)
