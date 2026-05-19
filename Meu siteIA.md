<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Meu Portfólio</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --royal: #1a3a8f;
      --royal-light: #2a52c9;
      --royal-dark: #0d1f52;
      --black: #0a0a0a;
      --white: #f5f5f5;
      --gray: #c8c8c8;
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--black);
      color: var(--white);
      font-family: 'DM Sans', sans-serif;
      overflow-x: hidden;
    }

    /* ── NAV ── */
    nav {
      position: fixed; top: 0; width: 100%; z-index: 100;
      display: flex; justify-content: space-between; align-items: center;
      padding: 1.2rem 5vw;
      background: rgba(10,10,10,0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid rgba(42,82,201,0.25);
    }
    .logo {
      font-family: 'Playfair Display', serif;
      font-size: 1.4rem;
      letter-spacing: 0.06em;
      color: var(--white);
    }
    .logo span { color: var(--royal-light); }
    nav ul { list-style: none; display: flex; gap: 2.5rem; }
    nav ul a {
      color: var(--gray); text-decoration: none;
      font-size: 0.85rem; letter-spacing: 0.12em; text-transform: uppercase;
      transition: color .25s;
    }
    nav ul a:hover { color: var(--royal-light); }

    /* ── HERO ── */
    #hero {
      min-height: 100vh;
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: center;
      padding: 8rem 5vw 4rem;
      position: relative;
      overflow: hidden;
      gap: 4rem;
    }

    /* geometric bg */
    #hero::before {
      content: '';
      position: absolute; inset: 0;
      background:
        radial-gradient(ellipse 60% 80% at 70% 50%, rgba(26,58,143,0.35) 0%, transparent 65%),
        radial-gradient(ellipse 40% 40% at 10% 80%, rgba(42,82,201,0.12) 0%, transparent 60%);
      pointer-events: none;
    }
    .hero-grid-lines {
      position: absolute; inset: 0; pointer-events: none; opacity: 0.04;
      background-image:
        linear-gradient(var(--white) 1px, transparent 1px),
        linear-gradient(90deg, var(--white) 1px, transparent 1px);
      background-size: 60px 60px;
    }

    .hero-text { position: relative; z-index: 2; }
    .hero-tag {
      display: inline-block;
      font-size: 0.75rem; letter-spacing: 0.2em; text-transform: uppercase;
      color: var(--royal-light);
      border: 1px solid var(--royal-light);
      padding: 0.3rem 0.9rem; border-radius: 2px;
      margin-bottom: 1.5rem;
      animation: fadeUp .7s ease both;
    }
    .hero-name {
      font-family: 'Playfair Display', serif;
      font-size: clamp(3rem, 6vw, 5.5rem);
      font-weight: 900;
      line-height: 1.05;
      margin-bottom: 1rem;
      animation: fadeUp .7s .12s ease both;
    }
    .hero-name .highlight {
      color: transparent;
      -webkit-text-stroke: 2px var(--royal-light);
    }
    .hero-subtitle {
      font-size: 1.1rem; color: var(--gray); font-weight: 300;
      line-height: 1.7; max-width: 420px;
      margin-bottom: 2.5rem;
      animation: fadeUp .7s .22s ease both;
    }
    .hero-ctas { display: flex; gap: 1rem; flex-wrap: wrap; animation: fadeUp .7s .32s ease both; }
    .btn-primary {
      background: var(--royal); color: var(--white);
      padding: .8rem 2rem; border: 2px solid var(--royal);
      font-family: 'DM Sans', sans-serif; font-size: .85rem;
      letter-spacing: .1em; text-transform: uppercase; cursor: pointer;
      text-decoration: none;
      transition: background .25s, color .25s;
      clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
    }
    .btn-primary:hover { background: var(--royal-light); border-color: var(--royal-light); }
    .btn-outline {
      background: transparent; color: var(--white);
      padding: .8rem 2rem; border: 2px solid rgba(255,255,255,0.25);
      font-family: 'DM Sans', sans-serif; font-size: .85rem;
      letter-spacing: .1em; text-transform: uppercase; cursor: pointer;
      text-decoration: none;
      transition: border-color .25s, color .25s;
      clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
    }
    .btn-outline:hover { border-color: var(--royal-light); color: var(--royal-light); }

    /* ── PHOTO FRAME ── */
    .hero-photo-wrap {
      position: relative; z-index: 2;
      animation: fadeUp .7s .1s ease both;
    }
    .photo-frame {
      position: relative;
      width: min(380px, 90%);
      margin: 0 auto;
    }
    .photo-frame::before {
      content: '';
      position: absolute;
      inset: -3px;
      background: linear-gradient(135deg, var(--royal-light), transparent 50%, var(--royal));
      border-radius: 2px;
      z-index: 0;
    }
    .photo-inner {
      position: relative; z-index: 1;
      background: #161a2e;
      overflow: hidden;
      aspect-ratio: 3/4;
      display: flex; align-items: center; justify-content: center;
    }
    .photo-placeholder {
      width: 100%; height: 100%;
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      gap: 1rem;
      background: linear-gradient(160deg, #0d1f52 0%, #161a2e 100%);
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }
    .photo-placeholder::after {
      content: '';
      position: absolute; inset: 0;
      background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%232a52c9' fill-opacity='0.06'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
    }
    .photo-icon {
      width: 80px; height: 80px;
      border-radius: 50%;
      background: rgba(42,82,201,0.2);
      border: 2px dashed var(--royal-light);
      display: flex; align-items: center; justify-content: center;
      font-size: 2rem; position: relative; z-index: 1;
    }
    .photo-hint {
      font-size: .8rem; color: var(--gray);
      letter-spacing: .08em; position: relative; z-index: 1;
      text-align: center;
    }
    .photo-actual {
      width: 100%; height: 100%;
      object-fit: cover;
      display: none;
    }
    .photo-upload-input { display: none; }

    .badge-floating {
      position: absolute;
      bottom: -16px; left: -20px;
      background: var(--royal);
      border: 2px solid var(--black);
      padding: .6rem 1.2rem;
      font-size: .8rem; letter-spacing: .12em; text-transform: uppercase;
      font-weight: 500;
      z-index: 3;
    }

    /* ── ABOUT ── */
    #about {
      padding: 8rem 5vw;
      display: grid;
      grid-template-columns: 1fr 2fr;
      gap: 6rem;
      align-items: start;
      border-top: 1px solid rgba(255,255,255,0.06);
    }
    .section-label {
      font-size: .7rem; letter-spacing: .25em; text-transform: uppercase;
      color: var(--royal-light); margin-bottom: .5rem;
    }
    .section-number {
      font-family: 'Playfair Display', serif;
      font-size: 6rem; font-weight: 900; line-height: 1;
      color: rgba(42,82,201,0.12);
      pointer-events: none; user-select: none;
      margin-top: -.5rem;
    }
    .section-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 700;
      line-height: 1.2;
      margin-bottom: 2rem;
    }
    .about-text p {
      color: var(--gray); font-size: 1rem; line-height: 1.85;
      margin-bottom: 1.4rem;
    }
    .about-text p:first-child { color: var(--white); font-size: 1.1rem; }

    .stats-row {
      display: flex; gap: 3rem; margin-top: 3rem; flex-wrap: wrap;
    }
    .stat-item { display: flex; flex-direction: column; gap: .3rem; }
    .stat-num {
      font-family: 'Playfair Display', serif;
      font-size: 2.4rem; font-weight: 700; color: var(--royal-light);
    }
    .stat-label { font-size: .78rem; letter-spacing: .12em; text-transform: uppercase; color: var(--gray); }

    /* ── EXPERIENCE ── */
    #experience {
      padding: 8rem 5vw;
      background: linear-gradient(180deg, transparent 0%, rgba(26,58,143,0.05) 50%, transparent 100%);
      border-top: 1px solid rgba(255,255,255,0.06);
    }
    .exp-header { display: flex; flex-direction: column; align-items: flex-start; margin-bottom: 5rem; }

    .timeline { position: relative; }
    .timeline::before {
      content: ''; position: absolute; left: 0; top: 0; bottom: 0;
      width: 2px;
      background: linear-gradient(to bottom, var(--royal), rgba(42,82,201,0.1));
    }

    .exp-item {
      padding-left: 3.5rem;
      padding-bottom: 4rem;
      position: relative;
      opacity: 0;
      transform: translateX(-20px);
      transition: opacity .6s ease, transform .6s ease;
    }
    .exp-item.visible { opacity: 1; transform: translateX(0); }

    .exp-dot {
      position: absolute; left: -7px; top: 6px;
      width: 16px; height: 16px;
      background: var(--royal-light);
      border: 3px solid var(--black);
      border-radius: 50%;
      box-shadow: 0 0 0 2px var(--royal);
    }
    .exp-date {
      font-size: .72rem; letter-spacing: .18em; text-transform: uppercase;
      color: var(--royal-light); margin-bottom: .5rem;
    }
    .exp-role {
      font-family: 'Playfair Display', serif;
      font-size: 1.5rem; font-weight: 700; margin-bottom: .3rem;
    }
    .exp-company {
      font-size: .9rem; color: var(--gray); margin-bottom: 1rem;
    }
    .exp-desc { color: var(--gray); font-size: .95rem; line-height: 1.8; max-width: 600px; }

    .exp-tags { display: flex; flex-wrap: wrap; gap: .5rem; margin-top: 1rem; }
    .tag {
      font-size: .7rem; letter-spacing: .1em; text-transform: uppercase;
      padding: .25rem .75rem;
      border: 1px solid rgba(42,82,201,0.4);
      color: var(--royal-light);
      background: rgba(42,82,201,0.08);
    }

    /* ── FOOTER ── */
    footer {
      border-top: 1px solid rgba(255,255,255,0.06);
      padding: 2.5rem 5vw;
      display: flex; justify-content: space-between; align-items: center;
      flex-wrap: wrap; gap: 1rem;
    }
    .footer-copy { font-size: .8rem; color: rgba(200,200,200,0.4); letter-spacing: .08em; }
    .footer-socials { display: flex; gap: 1.5rem; }
    .footer-socials a {
      font-size: .75rem; letter-spacing: .15em; text-transform: uppercase;
      color: var(--gray); text-decoration: none;
      transition: color .2s;
    }
    .footer-socials a:hover { color: var(--royal-light); }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(28px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      #hero { grid-template-columns: 1fr; padding-top: 6rem; gap: 2rem; }
      .hero-photo-wrap { order: -1; }
      .photo-frame { width: min(280px, 90%); }
      #about { grid-template-columns: 1fr; gap: 2rem; }
      .section-number { font-size: 4rem; }
    }
  </style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="logo">Seu<span>Nome</span></div>
  <ul>
    <li><a href="#hero">Início</a></li>
    <li><a href="#about">Sobre</a></li>
    <li><a href="#experience">Experiências</a></li>
  </ul>
</nav>

<!-- ═══════════ HERO ═══════════ -->
<section id="hero">
  <div class="hero-grid-lines"></div>

  <div class="hero-text">
    <div class="hero-tag">Portfólio Pessoal</div>
    <h1 class="hero-name">
      Olá, sou<br>
      <span class="highlight">Seu</span> Nome
    </h1>
    <p class="hero-subtitle">
      Uma breve descrição sua — profissão, área de atuação ou o que quiser destacar logo de cara para quem visita seu site.
    </p>
    <div class="hero-ctas">
      <a href="#experience" class="btn-primary">Ver Experiências</a>
      <a href="#about" class="btn-outline">Sobre Mim</a>
    </div>
  </div>

  <div class="hero-photo-wrap">
    <div class="photo-frame">
      <div class="photo-inner">
        <!-- Clique para adicionar sua foto -->
        <label class="photo-placeholder" for="photoInput" title="Clique para adicionar sua foto">
          <div class="photo-icon">📷</div>
          <p class="photo-hint">Clique para<br>adicionar sua foto</p>
          <img class="photo-actual" id="photoActual" alt="Minha foto"/>
        </label>
        <input type="file" id="photoInput" class="photo-upload-input" accept="image/*"/>
      </div>
      <div class="badge-floating">Disponível ✦</div>
    </div>
  </div>
</section>

<!-- ═══════════ ABOUT ═══════════ -->
<section id="about">
  <div class="about-left">
    <div class="section-label">Conheça-me</div>
    <div class="section-number">02</div>
  </div>

  <div class="about-text">
    <h2 class="section-title">Sobre<br>Mim</h2>

    <p>
      Escreva aqui sua apresentação principal — quem você é, o que faz e o que te move. Esta é sua chance de causar uma boa primeira impressão com um texto autêntico e direto.
    </p>
    <p>
      Continue contando sua história: de onde veio, quais valores guiam seu trabalho, o que te diferencia dos demais. Seja pessoal e genuíno — as pessoas se conectam com histórias reais.
    </p>
    <p>
      Adicione aqui mais um detalhe relevante: sua área de especialidade, seus objetivos atuais, ou uma curiosidade que diga algo sobre você além do currículo.
    </p>

    <div class="stats-row">
      <div class="stat-item">
        <span class="stat-num">5+</span>
        <span class="stat-label">Anos de Exp.</span>
      </div>
      <div class="stat-item">
        <span class="stat-num">20+</span>
        <span class="stat-label">Projetos</span>
      </div>
      <div class="stat-item">
        <span class="stat-num">10+</span>
        <span class="stat-label">Clientes</span>
      </div>
    </div>
  </div>
</section>

<!-- ═══════════ EXPERIENCE ═══════════ -->
<section id="experience">
  <div class="exp-header">
    <div class="section-label">Trajetória</div>
    <h2 class="section-title">Minhas<br>Experiências</h2>
  </div>

  <div class="timeline">

    <div class="exp-item">
      <div class="exp-dot"></div>
      <div class="exp-date">2022 — Presente</div>
      <h3 class="exp-role">Cargo Atual / Função</h3>
      <div class="exp-company">Nome da Empresa ou Organização</div>
      <p class="exp-desc">
        Descreva aqui suas principais responsabilidades e realizações neste cargo. Mencione projetos relevantes, resultados alcançados e habilidades utilizadas.
      </p>
      <div class="exp-tags">
        <span class="tag">Habilidade 1</span>
        <span class="tag">Habilidade 2</span>
        <span class="tag">Habilidade 3</span>
      </div>
    </div>

    <div class="exp-item">
      <div class="exp-dot"></div>
      <div class="exp-date">2019 — 2022</div>
      <h3 class="exp-role">Cargo Anterior</h3>
      <div class="exp-company">Nome da Empresa ou Organização</div>
      <p class="exp-desc">
        Fale sobre o que você fez neste período, como cresceu profissionalmente e quais desafios superou. Inclua conquistas concretas sempre que possível.
      </p>
      <div class="exp-tags">
        <span class="tag">Habilidade 4</span>
        <span class="tag">Habilidade 5</span>
        <span class="tag">Habilidade 6</span>
      </div>
    </div>

    <div class="exp-item">
      <div class="exp-dot"></div>
      <div class="exp-date">2016 — 2019</div>
      <h3 class="exp-role">Início da Carreira</h3>
      <div class="exp-company">Nome da Empresa ou Organização</div>
      <p class="exp-desc">
        Conte como começou sua trajetória, onde estudou ou estagiou, e quais fundamentos construiu nesta fase inicial da sua vida profissional.
      </p>
      <div class="exp-tags">
        <span class="tag">Habilidade 7</span>
        <span class="tag">Formação</span>
        <span class="tag">Habilidade 8</span>
      </div>
    </div>

  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-copy">© 2026 · Seu Nome · Todos os direitos reservados</div>
  <div class="footer-socials">
    <a href="#">LinkedIn</a>
    <a href="#">GitHub</a>
    <a href="#">Contato</a>
  </div>
</footer>

<script>
  // Photo upload
  const input = document.getElementById('photoInput');
  const img   = document.getElementById('photoActual');
  input.addEventListener('change', e => {
    const file = e.target.files[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = ev => {
      img.src = ev.target.result;
      img.style.display = 'block';
      img.previousElementSibling.style.display = 'none'; // hide icon+hint
      document.querySelector('.photo-placeholder').style.cursor = 'default';
    };
    reader.readAsDataURL(file);
  });

  // Scroll-triggered experience items
  const items = document.querySelectorAll('.exp-item');
  const obs = new IntersectionObserver(entries => {
    entries.forEach((e, i) => {
      if (e.isIntersecting) {
        setTimeout(() => e.target.classList.add('visible'), i * 150);
        obs.unobserve(e.target);
      }
    });
  }, { threshold: 0.15 });
  items.forEach(el => obs.observe(el));
</script>
</body>
</html>
