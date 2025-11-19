<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Menu</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">
  <style>
    :root {
      --bg: #0f172a;
      --tile: #1e293b;
      --tile-hover: #2563eb;
      --text: #e2e8f0;
      --accent: #60a5fa;
      --radius: 16px;
      --shadow: 0 8px 20px rgba(0,0,0,0.25);
    }
    * { box-sizing: border-box }
    html, body {
      height: 100%; margin: 0; background: linear-gradient(120deg,#0b1220,#111827);
      font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif; color: var(--text);
    }
    .wrap {
      max-width: 1000px; margin: 0 auto; padding: 28px;
    }
    header {
      display: flex; align-items: center; justify-content: space-between; margin: 12px 0 24px;
    }
    .brand {
      display: flex; align-items: center; gap: 12px;
    }
    .brand .dot {
      width: 14px; height: 14px; border-radius: 50%;
      background: radial-gradient(circle at 35% 35%, #93c5fd, #2563eb 60%, #1e40af 100%);
      box-shadow: 0 0 20px #60a5fa80;
    }
    .brand h1 { font-size: 20px; margin: 0; font-weight: 600; letter-spacing: 0.2px }
    .grid {
      display: grid; gap: 18px;
      grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    }
    .tile {
      background: linear-gradient(180deg, #1f2937, #111827 65%);
      border-radius: var(--radius);
      padding: 18px;
      box-shadow: var(--shadow);
      border: 1px solid #334155;
      cursor: pointer;
      transition: transform .18s ease, box-shadow .18s ease, border-color .18s ease;
      display: flex; align-items: center; gap: 14px;
    }
    .tile:hover {
      transform: translateY(-2px);
      border-color: #2563eb;
      box-shadow: 0 14px 28px rgba(37,99,235,0.25);
    }
    .icon {
      width: 48px; height: 48px; border-radius: 12px;
      background: #0b1220; display: grid; place-items: center;
      border: 1px solid #334155;
    }
    .icon img { width: 28px; height: 28px }
    .meta { display: flex; flex-direction: column; gap: 4px }
    .title { font-weight: 600; color: #e5e7eb }
    .desc { font-size: 13px; color: #94a3b8 }
    .footer {
      margin-top: 26px; font-size: 12px; color: #94a3b8; text-align: center;
    }
    a.tile { text-decoration: none; color: inherit }
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="brand">
        <div class="dot"></div>
        <h1>Menu d’icônes</h1>
      </div>
    </header>

    <section class="grid" id="grid"></section>

    <p class="footer">Ajoute ou retire des tuiles dans le tableau “tiles” du script.</p>
  </div>

  <script>
    // Définis tes tuiles ici: ajoute/supprime des objets du tableau
    const tiles = [
      {
        title: "Accueil",
        desc: "Présentation générale",
        href: "pages/accueil.html",
        icon: "assets/icons/home.svg"
      },
      {
        title: "Projets",
        desc: "Mes réalisations et idées",
        href: "pages/projets.html",
        icon: "assets/icons/box.svg"
      },
      {
        title: "Contact",
        desc: "Me joindre",
        href: "pages/contact.html",
        icon: "assets/icons/mail.svg"
      }
    ];

    const grid = document.getElementById('grid');

    tiles.forEach(t => {
      const a = document.createElement('a');
      a.className = 'tile';
      a.href = t.href;

      const icon = document.createElement('div');
      icon.className = 'icon';
      const img = document.createElement('img');
      img.src = t.icon;
      img.alt = t.title;
      icon.appendChild(img);

      const meta = document.createElement('div');
      meta.className = 'meta';
      const title = document.createElement('div');
      title.className = 'title';
      title.textContent = t.title;
      const desc = document.createElement('div');
      desc.className = 'desc';
      desc.textContent = t.desc;

      meta.appendChild(title);
      meta.appendChild(desc);

      a.appendChild(icon);
      a.appendChild(meta);

      grid.appendChild(a);
    });
  </script>
</body>
</html>
