# te-amo
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Tú & Yo — Lo que fuimos</title>

  <!-- Fuentes (opcional) -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&family=Playfair+Display:wght@600&display=swap" rel="stylesheet">

  <meta name="theme-color" content="#0e2a47">
  <style>
    :root{
      --bg: #0b1f36;          /* azul noche */
      --bg-2:#0e2a47;         /* azul profundo */
      --ink:#eef6ff;          /* blanco azulado */
      --muted:#9fc3ff;        /* azul suave */
      --accent:#69b3ff;       /* azul cielo */
      --heart:#ff6b9a;        /* toque romántico */
      --card:#102b4d;         /* cartas */
      --glass: rgba(255,255,255,.06);
      --shadow: 0 10px 30px rgba(0,0,0,.35);
      --radius: 16px;
    }
    *{box-sizing:border-box}
    html,body{margin:0;height:100%;background:linear-gradient(180deg,var(--bg),var(--bg-2));color:var(--ink);font-family:Poppins,system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif}
    a{color:var(--accent)}
    .wrap{max-width:960px;margin:0 auto;padding:24px}
    /* Hero */
    header.hero{
      position:relative;
      min-height:92vh;
      display:grid;
      place-items:center;
      text-align:center;
      overflow:hidden;
      border-bottom:1px solid rgba(255,255,255,.08);
    }
    .stars{position:absolute;inset:0;pointer-events:none;opacity:.5}
    .star{position:absolute;width:2px;height:2px;background:radial-gradient(#fff,transparent);border-radius:50%;animation: twinkle 3.5s infinite ease-in-out}
    @keyframes twinkle{50%{transform:scale(1.4);opacity:.7}}
    .floating-hearts{position:absolute;inset:0;pointer-events:none}
    .heart{
      position:absolute;
      width:14px;height:14px;
      transform:rotate(45deg);
      background:var(--heart);
      box-shadow:var(--shadow);
      animation:floatUp 8s linear infinite;
      opacity:.15;
    }
    .heart::before,.heart::after{
      content:"";
      position:absolute;
      width:14px;height:14px;
      background:var(--heart);
      border-radius:50%;
    }
    .heart::before{left:-7px}
    .heart::after{top:-7px}
    @keyframes floatUp{
      0%{transform:translateY(40vh) rotate(45deg);opacity:.0}
      20%{opacity:.25}
      100%{transform:translateY(-60vh) rotate(45deg);opacity:0}
    }
    h1{
      font-family:"Playfair Display",serif;
      font-size:clamp(40px,7vw,72px);
      line-height:1.05;
      margin:0 0 10px;
      letter-spacing:.3px;
      background:linear-gradient(180deg,#fff,var(--muted));
      -webkit-background-clip:text;background-clip:text;color:transparent
    }
    .subtitle{
      color:var(--muted);
      font-weight:300;
      font-size:clamp(16px,2.5vw,18px)
    }
    .badge{
      display:inline-flex;gap:8px;align-items:center;
      padding:8px 12px;border:1px solid rgba(255,255,255,.12);
      background:var(--glass);
      border-radius:999px;color:var(--muted);backdrop-filter:blur(6px)
    }
    .cta{
      margin-top:22px;display:inline-flex;gap:10px;align-items:center;
      background:linear-gradient(135deg,var(--accent),#7fd0ff);
      color:#06223d;text-decoration:none;font-weight:700;
      padding:12px 18px;border-radius:999px;box-shadow:var(--shadow);
      transition:transform .15s ease, filter .2s ease;
    }
    .cta:hover{transform:translateY(-2px)}
    .soft{opacity:.7}
    /* Secciones */
    section{padding:64px 0;border-top:1px solid rgba(255,255,255,.06)}
    h2{
      font-family:"Playfair Display",serif;
      font-size:clamp(28px,4.8vw,42px);margin:0 0 14px
    }
    p.lead{color:var(--muted);margin-top:0;max-width:65ch}
    .card{
      background:linear-gradient(180deg,var(--card),rgba(16,43,77,.7));
      border:1px solid rgba(255,255,255,.08);
      border-radius:var(--radius);
      box-shadow:var(--shadow);
    }
    /* Línea de tiempo */
    .timeline{display:grid;gap:16px;margin-top:20px}
    .milestone{
      display:grid;gap:8px;padding:16px 18px;position:relative
    }
    .milestone::before{
      content:"";position:absolute;left:10px;top:0;bottom:0;width:2px;background:linear-gradient(var(--accent),transparent)
    }
    .dot{
      width:12px;height:12px;border-radius:50%;background:var(--accent);box-shadow:0 0 0 3px rgba(105,179,255,.2)
    }
    .row{display:flex;gap:12px;align-items:flex-start}
    .when{font-size:12px;color:var(--muted);letter-spacing:.3px}
    .what{font-weight:600}
    /* Top momentos (scroll-snap) */
    .snap{
      display:grid;gap:12px
    }
    .rail{
      display:flex;gap:14px;overflow:auto;padding-bottom:4px;scroll-snap-type:x mandatory
    }
    .momento{
      min-width:260px;scroll-snap-align:center;padding:16px
    }
    .momento img{
      width:100%;height:160px;object-fit:cover;border-radius:12px;border:1px solid rgba(255,255,255,.08)
    }
    /* Lista con reveal */
    .list{display:grid;gap:10px;margin-top:16px}
    details{
      background:var(--glass);border:1px solid rgba(255,255,255,.08);
      padding:14px 16px;border-radius:12px
    }
    summary{cursor:pointer;outline:none}
    summary::-webkit-details-marker{display:none}
    /* Carta plegable */
    .letter{padding:22px}
    .letter p{margin:0 0 14px}
    .muted{color:var(--muted)}
    /* Barra música */
    .player{
      position:fixed;right:16px;bottom:16px;z-index:5;
      background:var(--glass);backdrop-filter:blur(8px);
      border:1px solid rgba(255,255,255,.12);
      border-radius:999px;display:flex;align-items:center;gap:10px;
      padding:10px 14px;color:var(--ink);box-shadow:var(--shadow)
    }
    .btn{cursor:pointer;border:0;background:transparent;color:inherit;font:inherit}
    .btn:active{transform:scale(.98)}
    .dotgrid{display:flex;gap:2px}
    .dotgrid span{width:6px;height:6px;background:var(--accent);border-radius:50%;opacity:.6;animation:beat 1.2s infinite ease-in-out}
    .dotgrid span:nth-child(2){animation-delay:.2s}
    .dotgrid span:nth-child(3){animation-delay:.4s}
    @keyframes beat{50%{transform:translateY(-2px);opacity:1}}
    /* Footer */
    footer{padding:40px 0;text-align:center;color:var(--muted)}
    /* Responsive */
    @media (min-width:860px){
      .grid-2{display:grid;grid-template-columns:1.1fr .9fr;gap:22px;align-items:start}
      .grid-3{display:grid;grid-template-columns:repeat(3,1fr);gap:14px}
    }
    /* Botón sorpresa */
    .surprise{
      display:inline-flex;align-items:center;gap:10px;margin-top:12px;
      padding:12px 16px;border-radius:12px;border:1px dashed rgba(255,255,255,.18);
      background:rgba(255,255,255,.03);cursor:pointer
    }
    .confetti{position:fixed;inset:0;pointer-events:none}
  </style>
</head>
<body>
  <div class="wrap">
    <header class="hero">
      <!-- Fondo dinámico -->
      <div class="stars" id="stars"></div>
      <div class="floating-hearts" id="hearts"></div>
      <div>
        <span class="badge">
          <!-- EDITA AQUÍ: nombres o apodos -->
          <span>Shay & Willy</span>
          <span class="soft">•</span>
          <span>2022<span class="soft"> comenzo</span>–2025<span class="soft"> continuara.</span></span>
        </span>
        <h1>Lo que fuimos</h1>
        <p class="subtitle">y aun somos....</p>
        <p class="subtitle">Pequeño homenaje a tres años que valieron la pena.</p>
        <a href="galeria.html" class="btn">Ver Recuerdos</a>
      </div>
    </header>
    <section id="timeline">
      <div class="grid-2">
        <div>
          <h2>Nuestra línea de tiempo</h2>
          <p class="lead">
            <!-- EDITA AQUÍ -->
            No todo fue perfecto, pero fue real. Estos son los hitos que me hacen sonreír cuando pienso en nosotros.
          </p>
          <div class="timeline card">
            <!-- EDITA AQUÍ: agrega/quita milestones -->
            <div class="milestone">
              <div class="row"><span class="dot"></span><div>
                <div class="when">Enero 20, 2022</div>
                <div class="what">La primera salida “sin querer queriendo”.</div>
                <div class="muted">Las conversaciones no se acababan.</div>
              </div></div>
            </div>
            <div class="milestone">
              <div class="row"><span class="dot"></span><div>
                <div class="when">Mayo 2022</div>
                <div class="what">Tu mensaje que cambió el tono.</div>
                <div class="muted">“Vamos a intentarlo bien”.</div>
              </div></div>
            </div>
            <div class="milestone">
              <div class="row"><span class="dot"></span><div>
                <div class="when">Octubre 2023</div>
                <div class="what">Nuestro viaje corto, mil recuerdos.</div>
                <div class="muted">Esa foto tuya riéndote… todavía me gana.</div>
              </div></div>
            </div>
            <div class="milestone">
              <div class="row"><span class="dot"></span><div>
                <div class="when">Abril 2024</div>
                <div class="what">Aprendimos a estar en equipo.</div>
                <div class="muted">Incluso cuando el mundo pesaba.</div>
              </div></div>
            </div>
          </div>
          <button class="surprise" id="btnSurprise" aria-label="Sorpresa">
            🎁 Abrir sorpresa
          </button>
        </div>
        <div>
          <h2>Top 5 momentos</h2>
          <p class="lead">Desliza para ver. (Prometo que son “solo los necesarios”).</p>
          <div class="snap card">
            <div class="rail" id="rail">
              <!-- EDITA AQUÍ: reemplaza src por tus imágenes (pueden ser fotos o neutras) -->
              <div class="momento">
                <img src="https://images.unsplash.com/photo-1516570161787-2fd917215a3d?q=80&w=1200&auto=format&fit=crop" alt="Recuerdo 1">
                <h3>Risa que contagia</h3>
                <p class="muted">Cuando no podíamos dejar de reír.</p>
              </div>
              <div class="momento">
                <img src="https://images.unsplash.com/photo-1520975916090-3105956dac38?q=80&w=1200&auto=format&fit=crop" alt="Recuerdo 2">
                <h3>El plan sencillo</h3>
                <p class="muted">Papas, pelis y cero pose. Lo nuestro.</p>
              </div>
              <div class="momento">
                <img src="https://images.unsplash.com/photo-1480280866816-05d9513c9c8f?q=80&w=1200&auto=format&fit=crop" alt="Recuerdo 3">
                <h3>El paseo corto</h3>
                <p class="muted">Ese atardecer aún me hace bien.</p>
              </div>
              <div class="momento">
                <img src="https://images.unsplash.com/photo-1500530855697-b586d89ba3ee?q=80&w=1200&auto=format&fit=crop" alt="Recuerdo 4">
                <h3>Equipo</h3>
                <p class="muted">Nos cuidamos bonito.</p>
              </div>
              <div class="momento">
                <img src="https://images.unsplash.com/photo-1496171367470-9ed9a91ea931?q=80&w=1200&auto=format&fit=crop" alt="Recuerdo 5">
                <h3>Tu mirada</h3>
                <p class="muted">Lo que no dije, igual lo sentiste.</p>
              </div>
            </div>
          </div>
          <div style="height:10px"></div>
          <h2>Las pequeñas cosas</h2>
          <div class="list">
            <!-- EDITA AQUÍ: micro-memorias (ligeras, cero drama) -->
            <details class="card"><summary>Cómo decías “ya voy” y llegabas 10 min después</summary></details>
            <details class="card"><summary>Tu forma de arreglar las cosas con comida</summary></details>
            <details class="card"><summary>Ese playlist que juras que no te gustaba (y sí)</summary></details>
            <details class="card"><summary>Tu risa cuando te ganaba en algo</summary></details>
          </div>
        </div>
      </div>
    </section>
    <section id="carta">
      <div class="grid-2">
        <div class="card letter">
          <h2>Una mini carta (sin drama)</h2>
          <p>
            <!-- EDITA AQUÍ -->
            Feliz cumpleaños, Willy. Gracias por lo que fuimos. Me quedo con lo bueno:
            las risas, la complicidad y la paz de saber que lo intentamos.
          </p>
          <p class="muted">
            Si alguna vez quieres hablar, aquí estoy. Sin prisa, sin presión.
          </p>
          <p class="muted">— S.</p>
        </div>
        <div class="card letter">
          <h2>Cómo navegar</h2>
          <p class="muted">Desliza los “Top momentos”, toca las viñetas para abrir, y si quieres música, dale al botón de play abajo.</p>
          <p class="muted">Si algo te saca una sonrisa hoy, ya valió la pena.</p>
        </div>
      </div>
    </section>
    <footer>
      <small>Hecho con cariño • <span style="color:var(--heart)">♥</span> •
        <!-- EDITA AQUÍ: ciudad/fecha si quieres -->
        Barranquilla, 2025
      </small>
    </footer>
  </div>
  <!-- Música (opcional): pon tu archivo MP3 o un enlace directo -->
  <!-- Reemplaza src="mi-cancion.mp3" por tu canción. Si no usas música, déjalo así. -->
  <audio id="song" src="" preload="none"></audio>

  <!-- Player flotante -->
  <div class="player" role="region" aria-label="Reproductor">
    <button class="btn" id="togglePlay" aria-label="Reproducir/Pausar">▶︎</button>
    <div class="dotgrid" aria-hidden="true"><span></span><span></span><span></span></div>
    <span class="soft">Música</span>
  </div>

  <canvas class="confetti" id="confetti"></canvas>

  <script>
    // === Estrellas y corazones flotantes ===
    const stars = document.getElementById('stars');
    const hearts = document.getElementById('hearts');

    function rand(min,max){return Math.random()*(max-min)+min}

    for(let i=0;i<80;i++){
      const s=document.createElement('span')
      s.className='star'
      s.style.left=rand(0,100)+'%';
      s.style.top=rand(0,100)+'%';
      s.style.animationDelay=rand(0,3)+'s';
      stars.appendChild(s)
    }
    for(let i=0;i<24;i++){
      const h=document.createElement('span')
      h.className='heart'
      h.style.left=rand(0,100)+'%';
      h.style.bottom=rand(-20,20)+'vh';
      h.style.animationDelay=rand(0,8)+'s';
      h.style.opacity = .12 + Math.random() * .12;
      hearts.appendChild(h)
    }

    // === Player simple ===
    const song = document.getElementById('song');
    const btnPlay = document.getElementById('togglePlay');

    btnPlay.addEventListener('click', async ()=>{
      try{
        if(song.paused){
          await song.play();
          btnPlay.textContent='❚❚';
        }else{
          song.pause();
          btnPlay.textContent='▶︎';
        }
      }catch(e){ alert('Agrega una canción al <audio> para usar el player.'); }
    });

    // === Sorpresa (confetti sutil) ===
    const btnSurprise = document.getElementById('btnSurprise');
    const canvas = document.getElementById('confetti');
    const ctx = canvas.getContext('2d');
    let pieces=[]; let w,h; let running=false;

    function resize(){w=canvas.width=innerWidth;h=canvas.height=innerHeight}
    addEventListener('resize',resize); resize();

    function makePiece(){
      const colors=['#69b3ff','#7fd0ff','#ff6b9a','#9fc3ff','#eef6ff'];
      return{
        x:Math.random()*w,
        y:-20,
        size:4+Math.random()*6,
        speed:1+Math.random()*2,
        rot:Math.random()*Math.PI,
        color:colors[(Math.random()*colors.length)|0]
      }
    }
    function frame(){
      if(!running) return;
      ctx.clearRect(0,0,w,h);
      pieces.forEach(p=>{
        p.y+=p.speed; p.rot+=.05;
        ctx.save(); ctx.translate(p.x,p.y); ctx.rotate(p.rot);
        ctx.fillStyle=p.color; ctx.fillRect(-p.size/2,-p.size/2,p.size,p.size);
        ctx.restore();
      });
      pieces = pieces.filter(p=>p.y<h+20);
      if(pieces.length>0) requestAnimationFrame(frame); else running=false;
    }
    btnSurprise.addEventListener('click',()=>{
      for(let i=0;i<160;i++) pieces.push(makePiece());
      if(!running){running=true;requestAnimationFrame(frame)}
    });

    // Accesibilidad: scroll suave en el CTA principal
    document.querySelectorAll('a[href^="#"]').forEach(a=>{
      a.addEventListener('click',e=>{
        const id=a.getAttribute('href').slice(1);
        const el=document.getElementById(id);
        if(el){ e.preventDefault(); el.scrollIntoView({behavior:'smooth',block:'start'}); }
      })
    });
  </script>
</body>
</html>
