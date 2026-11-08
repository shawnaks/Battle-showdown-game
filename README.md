# ❄️ Battle Showdown Challenge

**A turn-based browser battle where Jack takes on a snowman — with rizz, melting, and aura shields.**

![Next.js](https://img.shields.io/badge/Next.js-15.5-000000?logo=nextdotjs&logoColor=white)
![React](https://img.shields.io/badge/React-19.1-61DAFB?logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?logo=tailwindcss&logoColor=white)

---

## Overview

**Battle Showdown Challenge** is a small, self-contained fighting game built with Next.js and React. Two combatants — **Jack** and a **Snowman** — start with 100 HP each and trade blows in a strict turn-based loop. Jack is player-controlled and has a small arsenal of themed attacks and defensive options; the Snowman is fully automatic and always hits back.

The whole game lives in a single client component (`src/app/page.tsx`) and runs entirely in the browser — no backend, no database, no game engine. It's a compact example of building a complete interactive experience with React state, `setTimeout`-driven turn sequencing, and Tailwind CSS animation classes.

---

## Features

- **Turn-based combat** with a clear action → reaction rhythm (Jack acts, the Snowman retaliates).
- **Four player abilities**, each with distinct trade-offs:
  - `Rizz` — reliable 15 damage.
  - `Double Rizz` — 30 damage, but only **once per game**.
  - `Melt` — removes **30% of the Snowman's current HP**, making it strong against a healthy opponent and weaker as the fight drags on.
  - `Aura Shield` — sacrifices Jack's attack turn to halve the Snowman's next hit.
- **Animated HP bars** with smooth width transitions and live numeric readouts.
- **Visual feedback** for every event: bouncing damage arrows, a pulsing shield ring, and the loser rotating 90° on defeat.
- **Win screen** that appears after a short delay, reports the final score, and offers a one-click restart.
- **Fully responsive two-column arena** with a central `VS` badge.
- **Zero configuration** — no API keys, environment variables, or external services.

---

## Gameplay Rules

Both fighters begin at **100 HP**, and **Jack always moves first**.

| Ability | Effect | Cost / Limit |
| --- | --- | --- |
| **Rizz** | Deals **15 damage** to the Snowman | Standard attack |
| **Double Rizz** | Deals **30 damage** to the Snowman | Once per game |
| **Melt** | Deals **30% of the Snowman's current HP** (rounded) | Standard attack |
| **Aura Shield** | Halves the Snowman's next attack (12 → 6 damage) | Consumes Jack's turn |

**The Snowman** automatically counter-attacks **800 ms** after each of Jack's actions for **12 damage**, unless it has already been defeated. When a fighter's HP reaches 0, the game locks input and reveals the winner after a **1-second** pause.


---

## Tech Stack

| Layer | Technology |
| --- | --- |
| Framework | [Next.js 15.5](https://nextjs.org) (App Router) |
| UI Library | [React 19.1](https://react.dev) |
| Language | [TypeScript 5](https://www.typescriptlang.org) (strict mode) |
| Styling | [Tailwind CSS 4](https://tailwindcss.com) via `@tailwindcss/postcss` |
| Fonts | `next/font` — Geist Sans & Geist Mono |
| Bundler | Turbopack (`next dev --turbopack`, `next build --turbopack`) |
| State | React `useState` + `setTimeout` sequencing |

---

## Project Structure

> **Heads up:** the Next.js application lives in the nested `battle_showdown_challenge/` directory. The repository root only contains a README stub, so you must `cd` into the app folder before running any commands.

```
battle_showdown_challenge/
├── README.md                        # Repository-level readme (this file)
└── battle_showdown_challenge/       # The Next.js application
    ├── public/
    │   ├── jack.png                 # Jack character artwork
    │   ├── snowman.png              # Snowman character artwork
    │   └── *.svg                    # Default Next.js icons
    ├── src/
    │   └── app/
    │       ├── layout.tsx           # Root layout, font setup, metadata
    │       ├── page.tsx             # Entire game: state, logic, and UI
    │       ├── globals.css          # Tailwind import + theme variables
    │       └── favicon.ico
    ├── next.config.ts               # Next.js configuration
    ├── postcss.config.mjs           # Tailwind PostCSS plugin
    ├── tsconfig.json                # TypeScript config (`@/*` → `src/*`)
    └── package.json
```

---

## Getting Started

### Prerequisites

- **Node.js 18.18+** (Node 20+ recommended for Next.js 15)
- **npm**, or any compatible package manager (`pnpm`, `yarn`, `bun`)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/shawnaks/battle_showdown_challenge.git
cd battle_showdown_challenge

# 2. Enter the application directory
cd battle_showdown_challenge

# 3. Install dependencies
npm install
```

### Run the development server

```bash
npm run dev
```

Open **[http://localhost:3000](http://localhost:3000)** and the battle begins immediately.

### Build for production

```bash
npm run build
npm start
```

### Available scripts

| Script | Command | Description |
| --- | --- | --- |
| `dev` | `next dev --turbopack` | Starts the dev server with hot reload on port 3000 |
| `build` | `next build --turbopack` | Compiles an optimized production build |
| `start` | `next start` | Serves the production build |
---

