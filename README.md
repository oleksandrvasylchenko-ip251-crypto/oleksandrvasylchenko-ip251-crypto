
<!DOCTYPE html>
<html lang="uk">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Oleksandr Vasyldenko · Frontend Developer</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
      padding: 1.5rem;
      /* АНІМОВАНИЙ ФОН — ПЛАВНА ЗМІНА КОЛЬОРІВ */
      animation: backgroundShift 12s ease-in-out infinite alternate;
    }

    /* Анімація фону — глибокі переливи */
    @keyframes backgroundShift {
      0%   { background: #0a0e1a; }
      20%  { background: #111827; }
      40%  { background: #1a1f35; }
      60%  { background: #0f1929; }
      80%  { background: #141c2e; }
      100% { background: #080c18; }
    }

    .readme-card {
      max-width: 820px;
      width: 100%;
      background: rgba(18, 22, 30, 0.65);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border-radius: 2.5rem;
      padding: 3.5rem 4rem;
      box-shadow: 
        0 30px 80px rgba(0, 0, 0, 0.7),
        0 0 0 1px rgba(255, 255, 255, 0.05),
        inset 0 1px 0 rgba(255, 255, 255, 0.06);
      border: 1px solid rgba(255, 255, 255, 0.04);
      /* Картка трохи плаває, але текст — ні */
      animation: cardFloat 5s ease-in-out infinite alternate;
      position: relative;
    }

    /* Декоративне світіння по краях */
    .readme-card::after {
      content: '';
      position: absolute;
      inset: -1px;
      border-radius: 2.5rem;
      padding: 1px;
      background: radial-gradient(circle at 30% 20%, rgba(120, 160, 255, 0.06), transparent 70%);
      -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
      -webkit-mask-composite: xor;
      mask-composite: exclude;
      pointer-events: none;
    }

    /* Хедер — як на скріншоті */
    .readme-header {
      display: flex;
      align-items: center;
      gap: 0.75rem;
      font-size: 1rem;
      font-weight: 450;
      color: #a0aaba;
      padding-bottom: 1.2rem;
      border-bottom: 1px solid rgba(255, 255, 255, 0.05);
      margin-bottom: 2.2rem;
      flex-wrap: wrap;
    }

    .breadcrumb {
      display: flex;
      align-items: center;
      gap: 0.4rem;
      flex-wrap: wrap;
    }

    .breadcrumb .sep {
      opacity: 0.3;
      font-weight: 300;
    }

    .breadcrumb .repo-name {
      color: #d1d9e6;
      font-weight: 500;
    }

    .breadcrumb .file-name {
      color: #8e9bb3;
      background: rgba(255, 255, 255, 0.04);
      padding: 0.2rem 0.8rem;
      border-radius: 100px;
      font-size: 0.85rem;
      border: 1px solid rgba(255, 255, 255, 0.04);
    }

    /* ПРОФІЛЬ — ТЕКСТ БЕЗ АНІМАЦІЇ */
    .profile {
      padding: 1.2rem 0 1.8rem 0;
    }

    .name {
      font-size: 4.2rem;
      font-weight: 600;
      letter-spacing: -0.02em;
      line-height: 1.15;
      display: flex;
      flex-wrap: wrap;
      gap: 0.2rem 0.8rem;
      color: #ffffff;
      text-shadow: 0 2px 30px rgba(0, 0, 0, 0.4);
    }

    .name .first {
      background: linear-gradient(135deg, #f0f4ff, #b6c8ff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .name .last {
      background: linear-gradient(135deg, #d6e0ff, #8aa3ff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .title {
      font-size: 1.3rem;
      font-weight: 430;
      letter-spacing: 0.02em;
      padding-top: 0.4rem;
      border-top: 1px solid rgba(255, 255, 255, 0.04);
      display: inline-block;
      background: linear-gradient(90deg, #b0c4f0, #7f96cf);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .divider-line {
      margin: 1.6rem 0 0.8rem 0;
      height: 2px;
      background: linear-gradient(90deg, 
        rgba(255, 255, 255, 0.02) 0%, 
        rgba(255, 255, 255, 0.06) 40%, 
        rgba(255, 255, 255, 0.02) 100%);
      border-radius: 10px;
    }

    .meta-tag {
      display: flex;
      gap: 1.2rem;
      color: #6a7a9a;
      font-size: 0.8rem;
      margin-top: 0.4rem;
      opacity: 0.7;
    }

    .meta-tag span {
      display: flex;
      align-items: center;
      gap: 0.3rem;
    }

    .meta-tag .dot {
      display: inline-block;
      width: 5px;
      height: 5px;
      border-radius: 50%;
      background: #3d506e;
      margin-right: 0.2rem;
    }

    /* ТІЛЬКИ КАРТКА ПЛАВАЄ — ТЕКСТ НЕ АНІМУЄТЬСЯ */
    @keyframes cardFloat {
      0%   { transform: translateY(0px); box-shadow: 0 30px 80px rgba(0,0,0,0.6); }
      100% { transform: translateY(-6px); box-shadow: 0 40px 90px rgba(0,0,0,0.8); }
    }

    /* Адаптив */
    @media (max-width: 640px) {
      .readme-card { padding: 2rem 1.5rem; border-radius: 2rem; }
      .name { font-size: 2.8rem; }
      .title { font-size: 1rem; }
    }

    @media (max-width: 440px) {
      .name { font-size: 2.2rem; }
      .readme-header { font-size: 0.8rem; }
    }
  </style>
</head>
<body>
  <div class="readme-card">
    <!-- Хедер: Адамалстон / Файл README.md -->
    <div class="readme-header">
      <div class="breadcrumb">
        <span class="repo-name">Адамалстон</span>
        <span class="sep">/</span>
        <span class="file-name">Файл README.md</span>
      </div>
    </div>

    <!-- ОСНОВНИЙ ТЕКСТ — БЕЗ АНІМАЦІЇ -->
    <div class="profile">
      <div class="name">
        <span class="first">Oleksandr</span>
        <span class="last">Vasyldenko</span>
      </div>
      <div class="title">Frontend Developer</div>
    </div>

    <div class="divider-line"></div>
    <div class="meta-tag">
      <span><span class="dot"></span> GitHub</span>
      <span><span class="dot"></span> README.md</span>
    </div>
  </div>
</body>
</html>
---

# About me

<div align="center">

Hello, I'm **Oleksandr Vasylchenko** — Frontend Developer focused on building clean, scalable and modern web applications.

I value structure, performance and long-term maintainability.

### Frontend Developer

React / Node.js / TypeScript

Modern UI & clean architecture

Strong GitHub collaboration mindset

</div>

---

# Technologies

## Core Technologies

<p align="center">

<img src="https://skillicons.dev/icons?i=html"/>
<img src="https://skillicons.dev/icons?i=css"/>
<img src="https://skillicons.dev/icons?i=js"/>
<img src="https://skillicons.dev/icons?i=sass"/>
<img src="https://skillicons.dev/icons?i=ts"/>
<img src="https://skillicons.dev/icons?i=git"/>
<img src="https://skillicons.dev/icons?i=github"/>

</p>

---

## Frameworks & Libraries

<p align="center">

<img src="https://skillicons.dev/icons?i=react"/>
<img src="https://skillicons.dev/icons?i=nodejs"/>

</p>

---

## Team Collaboration

<div align="center">

Experienced in team development using GitHub, pull requests, code reviews and structured workflows.

</div>

---

# 🚀 Coding Activity

<div align="center">

<img width="850" src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=30&pause=1000&color=FFFFFF&center=true&vCenter=true&width=900&lines=Frontend+Developer;React+Developer;TypeScript+Developer;Node.js+Developer;Building+Modern+Web+Applications"/>

</div>

---

# 💻 Developer Life

<div align="center">

<img width="850" src="https://user-images.githubusercontent.com/74038190/212284068-5d6f0c4f-3d53-4d45-bef6-2e6d7c6f7f35.gif">

</div>

---

# ⚡ Matrix Animation

<div align="center">

<img width="850" src="https://user-images.githubusercontent.com/74038190/212744275-2e0cb7c0-7e5d-4c8e-bc0c-c6f0cf39d8e2.gif">

</div>

---

# 🔥 Current Stack

<div align="center">

<img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=28&duration=3000&pause=1000&color=00FFFF&center=true&width=900&lines=React.js;TypeScript;Node.js;HTML+%7C+CSS+%7C+JavaScript;Frontend+Developer"/>

</div>

---

# 📊 GitHub Stats

<div align="center">

<img width="49%" src="https://github-readme-stats.vercel.app/api?username=YOUR_USERNAME&show_icons=true&theme=github_dark&hide_border=true">

<img width="49%" src="https://github-readme-stats.vercel.app/api/top-langs/?username=YOUR_USERNAME&layout=compact&theme=github_dark&hide_border=true">

</div>

---

# 🏆 Achievements

<div align="center">

<img src="https://github-profile-trophy.vercel.app/?username=YOUR_USERNAME&theme=onestar&no-frame=true&column=4">

</div>

---

# 🐍 Contribution Snake

<div align="center">

<img src="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/github-contribution-grid-snake-dark.svg">

</div>

---

<div align="center">

<img src="https://komarev.com/ghpvc/?username=YOUR_USERNAME&style=for-the-badge&color=grey">

</div>
