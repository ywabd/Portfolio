<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>SneakersPov — UGC & Affiliate Creator</title>
  <link rel="preconnect" href="https://fonts.googleapis.com"/>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Inter:wght@300;400;500&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #0c0c0c;
      --surface: #141414;
      --surface2: #1c1c1c;
      --border: rgba(255,255,255,0.07);
      --white: #f2f2f2;
      --grey: #888;
      --grey2: #444;
      --accent: #e8ff47;
      --accent-dim: rgba(232,255,71,0.07);
      --accent-border: rgba(232,255,71,0.18);
    }
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    html { scroll-behavior: smooth; }
    body { background: var(--bg); color: var(--white); font-family: 'Inter', sans-serif; overflow-x: hidden; cursor: none; }

    /* CURSOR */
    #cur { width: 8px; height: 8px; background: var(--accent); border-radius: 50%; position: fixed; top:0;left:0; pointer-events:none; z-index:9999; }
    #cur-ring { width:32px;height:32px; border:1px solid rgba(232,255,71,0.45); border-radius:50%; position:fixed;top:0;left:0; pointer-events:none; z-index:9998; transition: transform 0.28s cubic-bezier(.23,1,.32,1); }

    /* NAV */
    nav { position:fixed;top:0;left:0;right:0;z-index:200; padding:1.1rem 2.5rem; display:flex;justify-content:space-between;align-items:center; background:rgba(12,12,12,0.92); backdrop-filter:blur(14px); border-bottom:1px solid var(--border); }
    .nav-brand { font-family:'Syne',sans-serif; font-weight:800; font-size:0.95rem; color:var(--white); text-decoration:none; }
    .nav-brand span { color:var(--accent); }
    .nav-links { display:flex; gap:2rem; }
    .nav-links a { font-size:0.72rem; letter-spacing:0.1em; text-transform:uppercase; color:var(--grey); text-decoration:none; transition:color 0.2s; }
    .nav-links a:hover { color:var(--white); }
    .nav-cta { background:var(--accent); color:#0c0c0c; padding:0.5rem 1.2rem; border-radius:3px; font-size:0.72rem; font-weight:700; letter-spacing:0.04em; text-decoration:none; transition:opacity 0.2s; }
    .nav-cta:hover { opacity:0.82; }

    /* HERO */
    .hero { min-height:100vh; display:grid; grid-template-columns:1fr 1fr; align-items:center; gap:3rem; padding:7rem 2.5rem 4rem; max-width:1160px; margin:0 auto; }
    .hero-eyebrow { display:inline-flex;align-items:center;gap:0.5rem; background:var(--accent-dim);border:1px solid var(--accent-border); padding:0.3rem 0.8rem;border-radius:2px; font-size:0.68rem;font-weight:500;letter-spacing:0.14em;text-transform:uppercase; color:var(--accent);margin-bottom:1.6rem; opacity:0;animation:up 0.6s 0.1s ease forwards; }
    .dot { width:6px;height:6px;background:var(--accent);border-radius:50%;animation:blink 1.8s infinite; }
    @keyframes blink { 0%,100%{opacity:1}50%{opacity:0.15} }
    h1 { font-family:'Syne',sans-serif; font-size:clamp(3rem,5.5vw,5.2rem); font-weight:800; line-height:1.0; letter-spacing:-0.03em; opacity:0;animation:up 0.6s 0.2s ease forwards; }
    .hl { color:var(--accent); }
    .hero-desc { margin-top:1.4rem; font-size:0.9rem;line-height:1.85;color:var(--grey);max-width:420px; opacity:0;animation:up 0.6s 0.3s ease forwards; }
    .hero-actions { display:flex;gap:0.6rem;margin-top:1.8rem;flex-wrap:wrap; opacity:0;animation:up 0.6s 0.4s ease forwards; }
    .btn { display:inline-flex;align-items:center;gap:0.4rem; padding:0.7rem 1.4rem;border-radius:3px; font-size:0.78rem;font-weight:500;letter-spacing:0.03em; text-decoration:none;transition:all 0.2s;border:none;cursor:none; }
    .btn-fill { background:var(--accent);color:#0c0c0c;font-weight:700; }
    .btn-fill:hover { opacity:0.85;transform:translateY(-1px); }
    .btn-ghost { background:transparent;color:var(--white);border:1px solid var(--border); }
    .btn-ghost:hover { border-color:rgba(255,255,255,0.18);background:rgba(255,255,255,0.04); }
    .langs { display:flex;gap:0.4rem;margin-top:1.6rem;flex-wrap:wrap; opacity:0;animation:up 0.6s 0.5s ease forwards; }
    .lang { display:flex;align-items:center;gap:0.35rem; background:var(--surface);border:1px solid var(--border); padding:0.28rem 0.65rem;border-radius:2px; font-size:0.7rem;color:var(--grey); }

    /* STATS CARD */
    .hero-right { opacity:0;animation:up 0.6s 0.35s ease forwards; }
    .stats-card { background:var(--surface);border:1px solid var(--border);border-radius:7px;overflow:hidden; }
    .sc-head { padding:1.1rem 1.4rem; border-bottom:1px solid var(--border); display:flex;align-items:center;gap:0.65rem; }
    .tt-icon { width:26px;height:26px;background:#000;border-radius:5px;display:flex;align-items:center;justify-content:center; }
    .tt-icon svg { width:14px;height:14px; }
    .sc-name { font-family:'Syne',sans-serif;font-weight:700;font-size:0.88rem; }
    .sc-sub { font-size:0.68rem;color:var(--grey);margin-top:0.1rem; }
    .badge { background:var(--accent-dim);border:1px solid var(--accent-border);color:var(--accent);font-size:0.6rem;font-weight:700;padding:0.18rem 0.45rem;border-radius:2px;letter-spacing:0.08em;text-transform:uppercase; }
    .sc-grid { display:grid;grid-template-columns:1fr 1fr;border-bottom:1px solid var(--border); }
    .sc-cell { padding:1.1rem 1.4rem;border-right:1px solid var(--border); }
    .sc-cell:nth-child(even){border-right:none;}
    .sc-cell:nth-child(3),.sc-cell:nth-child(4){border-top:1px solid var(--border);}
    .sc-num { font-family:'Space Mono',monospace;font-size:1.5rem;font-weight:700;line-height:1; }
    .sc-num.a { color:var(--accent); }
    .sc-lbl { font-size:0.65rem;color:var(--grey);letter-spacing:0.07em;text-transform:uppercase;margin-top:0.3rem; }
    .sc-foot { padding:0.9rem 1.4rem; }
    .sc-foot p { font-size:0.74rem;color:var(--grey);line-height:1.55; }
    .sc-foot strong { color:var(--white); }

    /* DIVIDER */
    .divider { height:1px;background:var(--border); }

    /* SHARED */
    .wrap { max-width:1160px;margin:0 auto;padding:0 2.5rem; }
    .pad { padding:5.5rem 0; }
    .sec-lbl { font-size:0.65rem;letter-spacing:0.16em;text-transform:uppercase;color:var(--accent);margin-bottom:0.7rem;display:flex;align-items:center;gap:0.5rem; }
    .sec-lbl::before { content:'';width:14px;height:1px;background:var(--accent); }
    h2 { font-family:'Syne',sans-serif;font-size:clamp(1.8rem,3.5vw,2.8rem);font-weight:800;letter-spacing:-0.02em;line-height:1.1; }
    .reveal { opacity:0;transform:translateY(20px);transition:opacity 0.65s ease,transform 0.65s ease; }
    .reveal.in { opacity:1;transform:none; }

    /* CONTENT GRID */
    .ct-grid { display:grid;grid-template-columns:repeat(3,1fr);gap:1px;margin-top:2.5rem;background:var(--border);border:1px solid var(--border);border-radius:7px;overflow:hidden; }
    .ct-card { background:var(--surface);padding:2rem 1.7rem;transition:background 0.2s; }
    .ct-card:hover { background:var(--surface2); }
    .ct-icon { font-size:1.5rem;margin-bottom:1rem;display:block; }
    .ct-title { font-family:'Syne',sans-serif;font-weight:700;font-size:0.95rem;margin-bottom:0.45rem; }
    .ct-desc { font-size:0.8rem;color:var(--grey);line-height:1.65; }

    /* FEED */
    .feed-bg { background:var(--surface); }
    .feed-grid { display:grid;grid-template-columns:2fr 1fr 1fr;grid-template-rows:auto auto;gap:0.6rem;margin-top:2.5rem; }
    .vid { background:var(--bg);border:1px solid var(--border);border-radius:5px;overflow:hidden;cursor:none;transition:border-color 0.2s,transform 0.2s; }
    .vid:hover { border-color:rgba(232,255,71,0.22);transform:translateY(-2px); }
    .vid.big { grid-row:span 2; }
    .vid-th { width:100%;background:var(--surface2);display:flex;align-items:center;justify-content:center;position:relative;overflow:hidden; }
    .vid.big .vid-th { aspect-ratio:9/16; }
    .vid:not(.big) .vid-th { aspect-ratio:4/5; }
    .vg { position:absolute;inset:0;background:linear-gradient(to bottom,transparent 40%,rgba(0,0,0,0.82)); }
    .vov { position:absolute;inset:0;background:rgba(12,12,12,0.5);display:flex;align-items:center;justify-content:center;opacity:0;transition:opacity 0.22s; }
    .vid:hover .vov { opacity:1; }
    .pbtn { width:40px;height:40px;border-radius:50%;background:var(--accent);color:#000;display:flex;align-items:center;justify-content:center;font-size:0.9rem; }
    .vid-meta { padding:0.8rem 0.9rem;border-top:1px solid var(--border); }
    .vid-tag { font-size:0.6rem;letter-spacing:0.09em;text-transform:uppercase;color:var(--accent);margin-bottom:0.25rem; }
    .vid-title { font-size:0.78rem;line-height:1.4;color:var(--white); }
    .vid-views { font-family:'Space Mono',monospace;font-size:0.65rem;color:var(--grey);margin-top:0.35rem; }
    .tb1{background:linear-gradient(135deg,#1c1a14,#0f0e0b);}
    .tb2{background:linear-gradient(135deg,#141618,#0a0c0e);}
    .tb3{background:linear-gradient(135deg,#18141c,#0e0a10);}
    .tb4{background:linear-gradient(135deg,#161c14,#0c100a);}
    .tb5{background:linear-gradient(135deg,#1c1414,#100a0a);}

    /* ABOUT */
    .about-grid { display:grid;grid-template-columns:1fr 1.5fr;gap:4rem;align-items:start;margin-top:2.5rem; }
    .profile-card { background:var(--surface);border:1px solid var(--border);border-radius:7px;overflow:hidden; }
    .pc-top { padding:2rem;background:linear-gradient(135deg,#181818,#111);display:flex;flex-direction:column;align-items:center;text-align:center;gap:0.7rem;border-bottom:1px solid var(--border); }
    .avatar { width:68px;height:68px;border-radius:50%;background:var(--surface2);border:2px solid var(--accent-border);display:flex;align-items:center;justify-content:center;font-size:2rem; }
    .pc-handle { font-family:'Syne',sans-serif;font-weight:800;font-size:1.05rem; }
    .pc-role { font-size:0.75rem;color:var(--grey); }
    .pc-body { padding:0; }
    .pc-row { display:flex;justify-content:space-between;align-items:center;padding:0.7rem 1.4rem;border-bottom:1px solid var(--border);font-size:0.8rem; }
    .pc-row:last-child { border-bottom:none; }
    .pc-lbl { color:var(--grey); }
    .pc-val { color:var(--white);font-weight:500;text-align:right; }
    .pc-val a { color:var(--accent);text-decoration:none; }
    .pc-val a:hover { text-decoration:underline; }
    .pc-val.av { color:var(--accent); }

    .about-right h2 { margin-bottom:1.3rem; }
    .about-right p { font-size:0.87rem;color:var(--grey);line-height:1.85;margin-bottom:0.9rem; }
    .about-right p strong { color:var(--white); }
    .skills { display:grid;grid-template-columns:1fr 1fr;gap:0.45rem;margin-top:1.4rem; }
    .skill { display:flex;align-items:center;gap:0.55rem;background:var(--surface);border:1px solid var(--border);padding:0.6rem 0.85rem;border-radius:3px;font-size:0.76rem; }
    .skill span:first-child { font-size:0.95rem; }

    /* WHY */
    .why-grid { display:grid;grid-template-columns:repeat(3,1fr);gap:1px;margin-top:2.5rem;background:var(--border);border:1px solid var(--border);border-radius:7px;overflow:hidden; }
    .why-card { background:var(--surface);padding:2.2rem 1.8rem; }
    .why-num { font-family:'Space Mono',monospace;font-size:0.65rem;color:var(--accent);letter-spacing:0.1em;margin-bottom:1rem; }
    .why-title { font-family:'Syne',sans-serif;font-weight:700;font-size:0.95rem;margin-bottom:0.5rem; }
    .why-desc { font-size:0.8rem;color:var(--grey);line-height:1.68; }

    /* CONTACT */
    .contact-wrap { padding:7rem 2.5rem;text-align:center;position:relative;overflow:hidden; }
    .contact-glow { position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:500px;height:500px;border-radius:50%;background:radial-gradient(circle,rgba(232,255,71,0.04),transparent 70%);pointer-events:none; }
    .contact-inner { position:relative;z-index:2;max-width:520px;margin:0 auto; }
    .contact-inner h2 { font-size:clamp(2.5rem,6vw,5rem);margin-bottom:0.9rem; }
    .contact-inner p { font-size:0.88rem;color:var(--grey);line-height:1.8;margin-bottom:2.2rem; }
    .c-links { display:flex;gap:0.6rem;justify-content:center;flex-wrap:wrap; }
    .c-btn { display:inline-flex;align-items:center;gap:0.55rem;padding:0.8rem 1.5rem;border-radius:3px;font-size:0.78rem;font-weight:500;text-decoration:none;border:1px solid var(--border);color:var(--white);transition:all 0.2s; }
    .c-btn:hover { border-color:var(--accent);color:var(--accent);background:var(--accent-dim); }
    .c-btn.p { background:var(--accent);color:#000;border-color:var(--accent);font-weight:700; }
    .c-btn.p:hover { opacity:0.85;color:#000; }
    .c-btn svg { width:15px;height:15px;flex-shrink:0; }

    /* FOOTER */
    footer { padding:1.4rem 2.5rem;border-top:1px solid var(--border);display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:0.5rem; }
    footer p { font-size:0.7rem;color:var(--grey2); }
    .fb { font-family:'Syne',sans-serif;font-weight:800;font-size:0.9rem;color:var(--white); }
    .fb span { color:var(--accent); }

    @keyframes up { from{opacity:0;transform:translateY(18px)} to{opacity:1;transform:none} }

    @media(max-width:900px){
      .hero{grid-template-columns:1fr;gap:2.5rem;padding-top:6.5rem;}
      .hero-right{order:-1;}
      .ct-grid,.why-grid{grid-template-columns:1fr;}
      .about-grid{grid-template-columns:1fr;}
      .feed-grid{grid-template-columns:1fr 1fr;}
      .vid.big{grid-row:auto;grid-column:span 2;}
      nav .nav-links{display:none;}
    }
    @media(max-width:580px){
      nav{padding:1rem 1.2rem;}
      .hero,.wrap,.contact-wrap{padding-left:1.2rem;padding-right:1.2rem;}
      footer{padding:1.2rem;}
      .sc-grid{grid-template-columns:1fr 1fr;}
    }
  </style>
</head>
<body>

<div id="cur"></div>
<div id="cur-ring"></div>

<nav>
  <a href="#" class="nav-brand"><span>@</span>sneakerspov</a>
  <div class="nav-links">
    <a href="#content">Content</a>
    <a href="#about">About</a>
    <a href="#contact">Contact</a>
  </div>
  <a href="mailto:abroudjiabdel7@gmail.com" class="nav-cta">Work with me</a>
</nav>

<div style="max-width:1160px;margin:0 auto;padding:0 2.5rem;">
  <div class="hero" style="padding-left:0;padding-right:0;">
    <div>
      <div class="hero-eyebrow"><span class="dot"></span> Open for collaborations</div>
      <h1>Sneakers.<br/><span class="hl">Streetwear.</span><br/>UGC.</h1>
      <p class="hero-desc">TikTok creator based in France. Honest, engaging content around sneakers, streetwear &amp; fashion hauls — from Chinese suppliers to full outfits. Real content, real audience.</p>
      <div class="hero-actions">
        <a href="mailto:abroudjiabdel7@gmail.com" class="btn btn-fill">Send me a collab ↗</a>
        <a href="https://www.tiktok.com/@sneakerspov" target="_blank" class="btn btn-ghost">View TikTok →</a>
      </div>
      <div class="langs">
        <div class="lang"><span>🇬🇧</span> English</div>
        <div class="lang"><span>🇫🇷</span> Français</div>
        <div class="lang"><span>🇪🇸</span> Español</div>
      </div>
    </div>

    <div class="hero-right">
      <div class="stats-card">
        <div class="sc-head">
          <div class="tt-icon">
            <svg viewBox="0 0 24 24" fill="white"><path d="M19.59 6.69a4.83 4.83 0 01-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 01-2.88 2.5 2.89 2.89 0 01-2.89-2.89 2.89 2.89 0 012.89-2.89c.28 0 .54.04.79.1V9.01a6.34 6.34 0 105.56 6.27V8.69a8.27 8.27 0 004.84 1.55V6.79a4.85 4.85 0 01-1.09-.1z"/></svg>
          </div>
          <div style="flex:1;">
            <div class="sc-name">@sneakerspov</div>
            <div class="sc-sub">TikTok · Sneakers & Streetwear</div>
          </div>
          <div class="badge">Creator</div>
        </div>
        <div class="sc-grid">
          <div class="sc-cell">
            <div class="sc-num">5956</div>
            <div class="sc-lbl">Followers</div>
          </div>
          <div class="sc-cell">
            <div class="sc-num a">233.8K</div>
            <div class="sc-lbl">Likes</div>
          </div>
          <div class="sc-cell">
            <div class="sc-num">44.3K</div>
            <div class="sc-lbl">Best video views</div>
          </div>
          <div class="sc-cell">
            <div class="sc-num a">EN·FR·ES</div>
            <div class="sc-lbl">Languages</div>
          </div>
        </div>
        <div class="sc-foot">
          <p><strong>Growing fast.</strong> High engagement ratio — tight community, big reach on top videos.</p>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="divider"></div>

<div id="content" class="pad" style="background:var(--bg);">
  <div class="wrap">
    <div class="sec-lbl reveal">What I create</div>
    <h2 class="reveal">Content formats</h2>
    <div class="ct-grid reveal">
      <div class="ct-card"><span class="ct-icon">📦</span><div class="ct-title">Unboxing & Haul</div><p class="ct-desc">Opening packages live — shoes, clothes, full hauls from Chinese suppliers. Honest first impressions, no filter.</p></div>
      <div class="ct-card"><span class="ct-icon">👟</span><div class="ct-title">Sneaker Review</div><p class="ct-desc">Detailed try-ons, quality checks, sizing tips. I show exactly what you get — clearly and honestly.</p></div>
      <div class="ct-card"><span class="ct-icon">🧥</span><div class="ct-title">Outfit & Styling</div><p class="ct-desc">Full streetwear looks built around your products. I show how to wear them, not just what they look like.</p></div>
      <div class="ct-card"><span class="ct-icon">🔗</span><div class="ct-title">Affiliate Content</div><p class="ct-desc">Product placement in organic videos, bio links, storefront recommendations. Experience with Oopbuy, PKGods and more.</p></div>
      <div class="ct-card"><span class="ct-icon">🎬</span><div class="ct-title">UGC (Raw Delivery)</div><p class="ct-desc">Content without watermarks, delivered directly to you for ads, e-commerce or social media use.</p></div>
      <div class="ct-card"><span class="ct-icon">🌐</span><div class="ct-title">Multilingual</div><p class="ct-desc">French, English or Spanish — three audiences, one creator. Great for brands targeting Europe and Latin America.</p></div>
    </div>
  </div>
</div>

<div class="feed-bg pad">
  <div class="wrap">
    <div class="sec-lbl reveal">Portfolio</div>
    <div style="display:flex;justify-content:space-between;align-items:flex-end;flex-wrap:wrap;gap:1rem;">
      <h2 class="reveal">Recent videos</h2>
      <a href="https://www.tiktok.com/@sneakerspov" target="_blank" class="btn btn-ghost reveal" style="margin-bottom:0;">Full profile →</a>
    </div>
    <div class="feed-grid reveal">
      
      <a href="https://vm.tiktok.com/ZNRqGYq1F/" target="_blank" class="vid big" style="text-decoration: none;">
        <div class="vid-th tb1">
          <img src="https://i.postimg.cc/ZRCh2bM3/IMG-4817.jpg" style="width: 100%; height: 100%; object-fit: cover; position: relative; z-index: 1;" alt="TikTok 1">
          <div class="vg"></div><div class="vov"><div class="pbtn">▶</div></div>
        </div>
        <div class="vid-meta">
          <div class="vid-tag">Sneakers</div>
          <div class="vid-title">Trouvailles Occasneaks 🔥</div>
          <div class="vid-views">▶ Voir sur TikTok</div>
        </div>
      </a>

      <a href="https://vm.tiktok.com/ZNRqGM7fX/" target="_blank" class="vid" style="text-decoration: none;">
        <div class="vid-th tb2">
          <img src="https://i.postimg.cc/ZRCh2bMH/IMG-4818.jpg" style="width: 100%; height: 100%; object-fit: cover; position: relative; z-index: 1;" alt="TikTok 2">
          <div class="vg"></div><div class="vov"><div class="pbtn">▶</div></div>
        </div>
        <div class="vid-meta">
          <div class="vid-tag">Sneakers · Glow</div>
          <div class="vid-title">La collection s'agrandit</div>
          <div class="vid-views">▶ Voir sur TikTok</div>
        </div>
      </a>

      <a href="https://vm.tiktok.com/ZNRqGHfgY/" target="_blank" class="vid" style="text-decoration: none;">
        <div class="vid-th tb3">
          <img src="https://i.postimg.cc/mDtGJL5V/IMG-4819.jpg" style="width: 100%; height: 100%; object-fit: cover; position: relative; z-index: 1;" alt="TikTok 3">
          <div class="vg"></div><div class="vov"><div class="pbtn">▶</div></div>
        </div>
        <div class="vid-meta">
          <div class="vid-tag">Review</div>
          <div class="vid-title">Balenciaga Runner Noire</div>
          <div class="vid-views">▶ Voir sur TikTok</div>
        </div>
      </a>

      <div class="vid">
        <div class="vid-th tb4"><span style="font-size:2.2rem;z-index:1;position:relative;">👕</span><div class="vg"></div><div class="vov"><div class="pbtn">▶</div></div></div>
        <div class="vid-meta"><div class="vid-tag">Streetwear · Outfit</div><div class="vid-title">Prochaine vidéo...</div><div class="vid-views">▶ À venir</div></div>
      </div>

      <div class="vid">
        <div class="vid-th tb5"><span style="font-size:2.2rem;z-index:1;position:relative;">🛒</span><div class="vg"></div><div class="vov"><div class="pbtn">▶</div></div></div>
        <div class="vid-meta"><div class="vid-tag">Affiliate</div><div class="vid-title">Prochaine vidéo...</div><div class="vid-views">▶ À venir</div></div>
      </div>

    </div>
  </div>
</div>

<div id="about" class="pad" style="background:var(--bg);">
  <div class="wrap">
    <div class="sec-lbl reveal">Who I am</div>
    <div class="about-grid">
      <div class="reveal">
        <div class="profile-card">
          <div class="pc-top">
            <div class="avatar">👟</div>
            <div class="pc-handle">@sneakerspov</div>
            <div class="pc-role">UGC Creator · TikTok</div>
          </div>
          <div class="pc-body">
            <div class="pc-row"><span class="pc-lbl">TikTok</span><span class="pc-val"><a href="https://www.tiktok.com/@sneakerspov" target="_blank">@sneakerspov</a></span></div>
            <div class="pc-row"><span class="pc-lbl">Niche</span><span class="pc-val">Sneakers · Streetwear</span></div>
            <div class="pc-row"><span class="pc-lbl">Linktree</span><span class="pc-val"><a href="https://linktr.ee/sneakerpov" target="_blank">linktr.ee/sneakerpov</a></span></div>
            <div class="pc-row"><span class="pc-lbl">Email</span><span class="pc-val"><a href="mailto:abroudjiabdel7@gmail.com">abroudjiabdel7@gmail.com</a></span></div>
            <div class="pc-row"><span class="pc-lbl">WhatsApp</span><span class="pc-val"><a href="https://wa.me/33767551254" target="_blank">07 67 55 12 54</a></span></div>
            <div class="pc-row"><span class="pc-lbl">Languages</span><span class="pc-val">EN · FR · ES</span></div>
            <div class="pc-row"><span class="pc-lbl">Based</span><span class="pc-val">France</span></div>
            <div class="pc-row"><span class="pc-lbl">Status</span><span class="pc-val av">✦ Available</span></div>
          </div>
        </div>
      </div>

      <div class="about-right reveal">
        <div class="sec-lbl">About me</div>
        <h2>Passionate.<br/>Motivated.<br/><span class="hl">Authentic.</span></h2>
        <p style="margin-top:1.3rem;">I'm a <strong>fashion and design enthusiast</strong> who lives and breathes streetwear culture. I've been building <strong>@sneakerspov</strong> around what I genuinely love — finding quality sneakers and clothes, often directly from Chinese suppliers, and sharing that with people who care about style.</p>
        <p>My content mixes unboxings, outfit videos, reviews and affiliate content. I'm <strong>motivated, reliable</strong> and always looking for brands or suppliers who want real content — not polished ads, but genuine videos that actually connect with people.</p>
        <p>Speaking <strong>3 languages</strong> means I can reach French, English and Spanish-speaking audiences — a real advantage for brands looking for international reach.</p>
        <div class="skills">
          <div class="skill"><span>🔥</span> Highly motivated</div>
          <div class="skill"><span>👟</span> Sneaker culture</div>
          <div class="skill"><span>🎨</span> Fashion & design</div>
          <div class="skill"><span>🌍</span> 3 languages</div>
          <div class="skill"><span>📦</span> Haul & unboxing</div>
          <div class="skill"><span>🔗</span> Affiliate ready</div>
          <div class="skill"><span>⚡</span> Fast turnaround</div>
          <div class="skill"><span>🎬</span> UGC delivery</div>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="pad" style="background:var(--surface);">
  <div class="wrap">
    <div class="sec-lbl reveal">The pitch</div>
    <h2 class="reveal">Why work with me?</h2>
    <div class="why-grid reveal">
      <div class="why-card">
        <div class="why-num">01</div>
        <div class="why-title">Growing = high engagement</div>
        <p class="why-desc">A growing account means my audience actually sees and interacts with every video. No dead followers — every view is real.</p>
      </div>
      <div class="why-card">
        <div class="why-num">02</div>
        <div class="why-title">I know the Chinese supplier market</div>
        <p class="why-desc">Experience with Oopbuy, PKGods and similar platforms. I know the products and how to present them honestly and convincingly.</p>
      </div>
      <div class="why-card">
        <div class="why-num">03</div>
        <div class="why-title">Three languages, three markets</div>
        <p class="why-desc">French, English, Spanish. One creator, three audiences. Perfect for suppliers targeting Europe and Latin America.</p>
      </div>
    </div>
  </div>
</div>

<div id="contact" class="contact-wrap">
  <div class="contact-glow"></div>
  <div class="contact-inner">
    <div class="sec-lbl reveal" style="justify-content:center;">Let's collab</div>
    <h2 class="reveal">Got a<br/><span class="hl">product?</span></h2>
    <p class="reveal">Send your shoes or clothes, I'll create the content. Unboxing, try-on, review, outfit — whatever works for your brand. DM on TikTok or email me directly.</p>
    <div class="c-links reveal">
      <a href="mailto:abroudjiabdel7@gmail.com" class="c-btn p">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
        abroudjiabdel7@gmail.com
      </a>
      <a href="https://wa.me/33767551254" target="_blank" class="c-btn">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 16.92v3a2 2 0 01-2.18 2 19.79 19.79 0 01-8.63-3.07 19.5 19.5 0 01-6-6 19.79 19.79 0 01-3.07-8.67A2 2 0 014.11 2h3a2 2 0 012 1.72 12.84 12.84 0 00.7 2.81 2 2 0 01-.45 2.11L8.09 9.91a16 16 0 006 6l1.27-1.27a2 2 0 012.11-.45 12.84 12.84 0 002.81.7A2 2 0 0122 16.92z"/></svg>
        WhatsApp
      </a>
      <a href="https://www.tiktok.com/@sneakerspov" target="_blank" class="c-btn">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M19.59 6.69a4.83 4.83 0 01-3.77-4.25V2h-3.45v13.67a2.89 2.89 0 01-2.88 2.5 2.89 2.89 0 01-2.89-2.89 2.89 2.89 0 012.89-2.89c.28 0 .54.04.79.1V9.01a6.34 6.34 0 105.56 6.27V8.69a8.27 8.27 0 004.84 1.55V6.79a4.85 4.85 0 01-1.09-.1z"/></svg>
        @sneakerspov
      </a>
      <a href="https://linktr.ee/sneakerpov" target="_blank" class="c-btn">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M10 13a5 5 0 007.54.54l3-3a5 5 0 00-7.07-7.07l-1.72 1.71"/><path d="M14 11a5 5 0 00-7.54-.54l-3 3a5 5 0 007.07 7.07l1.71-1.71"/></svg>
        Linktree
      </a>
    </div>
  </div>
</div>

<footer>
  <span class="fb"><span>@</span>sneakerspov</span>
  <p>© 2025 · UGC & Affiliate Creator · Sneakers & Streetwear</p>
  <p>abroudjiabdel7@gmail.com | 07 67 55 12 54</p>
</footer>

<script>
  const cur=document.getElementById('cur'),ring=document.getElementById('cur-ring');
  let mx=0,my=0,rx=0,ry=0;
  document.addEventListener('mousemove',e=>{mx=e.clientX;my=e.clientY;});
  (function loop(){
    cur.style.transform=`translate(${mx-4}px,${my-4}px)`;
    rx+=(mx-rx)*0.1;ry+=(my-ry)*0.1;
    ring.style.transform=`translate(${rx-16}px,${ry-16}px)`;
    requestAnimationFrame(loop);
  })();
  const obs=new IntersectionObserver(es=>es.forEach(e=>{if(e.isIntersecting)e.target.classList.add('in');}),{threshold:0.08});
  document.querySelectorAll('.reveal').forEach(el=>obs.observe(el));
</script>
</body>
</html>
