<!doctype html>
<html lang="vi">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Cute 3D Coffee Cup Designer Christmas Edition</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;600;700&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#f6f4f2;
      --card:#efe7e1;
      --accent:#6b4f3a;
      --accent-dark:#3b2a22;
      --muted:#b39a88;
      --glass:rgba(255,255,255,0.15);
      --shadow:0 12px 30px rgba(0,0,0,0.18);
      font-family:Outfit, system-ui, sans-serif;
      color:var(--accent-dark);
    }
    *{box-sizing:border-box}
    body{margin:0;background:linear-gradient(180deg,var(--bg),#efe9e4);min-height:100vh;display:flex;align-items:center;justify-content:center;padding:32px}
    .app{width:1100px;max-width:96vw;background:linear-gradient(180deg,#fffaff,#f7f2ef);border-radius:20px;padding:20px;box-shadow:var(--shadow);display:grid;grid-template-columns:480px 1fr;gap:18px}

    /* left column show area */
    .stage{background:var(--card);border-radius:14px;padding:18px;display:flex;flex-direction:column;align-items:center;gap:12px}
    .stage header{width:100%;display:flex;justify-content:space-between;align-items:center}
    .stage h3{margin:0;font-size:16px}
    .view{width:420px;height:420px;display:flex;align-items:center;justify-content:center;perspective:1200px}

    /* 3D cup wrapper */
    .cup-wrap{width:260px;height:300px;transform-style:preserve-3d;transition:transform .5s;position:relative}
    .cup-base{position:absolute;left:50%;transform:translateX(-50%);bottom:18px;width:220px;height:180px;border-radius:120px 120px 60px 60px/110px 110px 30px 30px;background:linear-gradient(180deg,#9b7c67,#5b4032);box-shadow:inset 0 -18px 30px rgba(255,255,255,0.05),0 16px 40px rgba(0,0,0,0.18)}

    /* coffee liquid */
    .coffee{position:absolute;left:50%;transform:translateX(-50%);top:44px;width:188px;height:110px;border-radius:50%/30%;background:linear-gradient(180deg,#4b2f22,#2d1b15);box-shadow:inset 0 -10px 14px rgba(0,0,0,0.25)}
    .foam{position:absolute;left:50%;transform:translateX(-50%);top:28px;width:200px;height:60px;border-radius:50%;background:linear-gradient(180deg,rgba(255,255,255,0.85),rgba(255,255,255,0.6));filter:blur(.6px);opacity:.9}

    /* cup body */
    .cup-tall{position:absolute;left:50%;transform:translateX(-50%);bottom:0;width:240px;height:260px;border-radius:30px;background:linear-gradient(180deg,#fdf8f5,#efe0d7);box-shadow:inset 0 8px 18px rgba(0,0,0,0.06);display:flex;align-items:flex-end;justify-content:center;padding-bottom:24px}
    .cup-shadow{position:absolute;left:50%;transform:translateX(-50%);bottom:-8px;width:320px;height:40px;border-radius:50%;background:radial-gradient(ellipse at center,rgba(0,0,0,0.22),transparent 40%);filter:blur(6px);}

    /* handle */
    .handle{position:absolute;right:-46px;top:86px;width:84px;height:120px;border-radius:60px;background:linear-gradient(180deg,#f6ece5,#f0dcd0);box-shadow:inset -6px 6px 12px rgba(0,0,0,0.04)}
    .handle:before{content:"";position:absolute;left:10px;top:10px;right:10px;bottom:10px;border-radius:40px;background:transparent}

    /* decorations */
    .garnish{position:absolute;left:50%;transform:translateX(-50%);top:12px;display:flex;gap:8px;align-items:center}
    .candy{width:34px;height:34px;border-radius:50%;display:grid;place-items:center;background:linear-gradient(180deg,#fff,#f3e8e1);box-shadow:0 6px 14px rgba(0,0,0,0.12)}
    .candy svg{width:20px;height:20px}

    /* sticker on cup */
    .sticker{position:absolute;left:50%;transform:translateX(-50%);bottom:92px;width:110px;height:80px;border-radius:12px;background:rgba(255,255,255,0.9);display:grid;place-items:center;font-weight:600}
    .sticker.small{width:54px;height:44px;border-radius:8px;bottom:150px}

    /* right column controls */
    .controls{padding:18px;background:linear-gradient(180deg,#fff,#fffaf8);border-radius:12px}
    .section{margin-bottom:14px}
    .label{font-size:13px;color:var(--muted);margin-bottom:6px}
    .options{display:flex;flex-wrap:wrap;gap:8px}
    .btn{padding:8px 12px;border-radius:10px;background:var(--glass);border:1px solid rgba(0,0,0,0.06);cursor:pointer;font-weight:600}
    .btn.active{background:linear-gradient(90deg,var(--accent),var(--accent-dark));color:#fff;border:none}
    .checkbox{display:flex;align-items:center;gap:8px;padding:6px 8px;border-radius:10px;background:#fff;border:1px solid rgba(0,0,0,0.04);cursor:pointer}

    /* sticker board */
    .sticker-board{display:grid;grid-template-columns:repeat(5,1fr);gap:8px;background:linear-gradient(180deg,#fffefc,#fff7f3);padding:10px;border-radius:10px}
    .sticker-thumb{height:56px;border-radius:8px;background:#fff;display:flex;align-items:center;justify-content:center;cursor:pointer;border:1px dashed rgba(0,0,0,0.06);font-size:12px}
    .sticker-thumb.active{outline:3px solid rgba(107,79,58,0.16)}

    /* name input and download row */
    .row{display:flex;gap:8px;align-items:center}
    input[type=text]{flex:1;padding:10px;border-radius:10px;border:1px solid rgba(0,0,0,0.06)}
    .download{padding:10px 14px;border-radius:10px;background:linear-gradient(90deg,var(--accent),var(--accent-dark));color:#fff;border:none;cursor:pointer}

    /* backgrounds */
    .bg-options{display:flex;gap:8px}
    .bg-swatch{width:56px;height:56px;border-radius:8px;cursor:pointer;border:2px solid transparent}
    .bg-swatch.active{outline:3px solid rgba(107,79,58,0.14)}

    /* social */
    .socials{display:flex;gap:8px;margin-top:10px}
    .socials a{display:inline-block;padding:8px 10px;border-radius:8px;background:var(--glass);text-decoration:none;color:var(--accent-dark);font-weight:600}

    /* responsive */
    @media(max-width:980px){.app{grid-template-columns:1fr;max-width:720px}.view{width:100%;height:360px}.cup-wrap{transform:scale(.92)}}
  </style>
</head>
<body>
  <div class="app">
    <div class="stage">
      <header>
        <h3>Preview</h3>
        <div style="font-size:13px;color:var(--muted)">Mery Christmas! - Designed by Ánh Tạ</div>
      </header>

      <div class="view" id="exportArea">
        <div class="cup-wrap" id="cupWrap">

          <div class="cup-shadow" id="cupShadow"></div>

          <div class="cup-tall" id="cupBody">
            <div class="sticker" id="cupSticker">Merry Christmas</div>
            <div class="coffee" id="coffee"></div>
            <div class="foam" id="foam"></div>
            <div class="garnish" id="garnish"></div>
          </div>

          <div class="cup-base"></div>
          <div class="handle"></div>
        </div>
      </div>

      <div style="width:100%;display:flex;justify-content:space-between;align-items:center">
        <div style="font-size:13px;color:var(--muted)">Stickers applied</div>
        <div style="font-size:13px;color:var(--muted)" id="appliedCount">0</div>
      </div>
    </div>

    <div class="controls">

      <div class="section">
        <div class="label">Sugar Level</div>
        <div class="options" id="sugarOptions">
          <button class="btn" data-val="0">0%</button>
          <button class="btn" data-val="30">30%</button>
          <button class="btn" data-val="50">50%</button>
          <button class="btn" data-val="70">70%</button>
          <button class="btn" data-val="100">100%</button>
        </div>
      </div>

      <div class="section">
        <div class="label">Topping</div>
        <div class="options" id="toppingOptions">
          <label class="checkbox"><input type="checkbox" value="Crispy coconut jelly"/>Crispy coconut jelly</label>
          <label class="checkbox"><input type="checkbox" value="Sea salt cheese foam"/>Sea salt cheese foam</label>
          <label class="checkbox"><input type="checkbox" value="Foamed milk"/>Foamed milk</label>
          <label class="checkbox"><input type="checkbox" value="Pudding"/>Pudding</label>
          <label class="checkbox"><input type="checkbox" value="Syrup vani"/>Syrup vani</label>
          <label class="checkbox"><input type="checkbox" value="Hazelnut"/>Hazelnut</label>
        </div>
      </div>

      <div class="section">
        <div class="label">Sticker chủ đề giáng sinh</div>
        <div class="sticker-board" id="stickerBoard"></div>
      </div>

      <div class="section">
        <div class="label">Đặt tên cho cốc coffee</div>
        <div class="row"><input type="text" id="cupNameInput" placeholder="Tên cốc của cậu"/></div>
      </div>

      <div class="section">
        <div class="label">Background để tải về</div>
        <div class="bg-options" id="bgOptions">
          <div class="bg-swatch" data-bg="bg-xmas-1" title="Xmas cozy" style="background:linear-gradient(180deg,#2e1a18,#4e352f);box-shadow:inset 0 2px 0 rgba(255,255,255,0.03)"></div>
          <div class="bg-swatch" data-bg="bg-xmas-2" title="Xmas lights" style="background:linear-gradient(180deg,#1f2b1e,#384734);"></div>
          <div class="bg-swatch" data-bg="bg-xmas-3" title="Snowy" style="background:linear-gradient(180deg,#dfeaf2,#f7fbff);"></div>
          <div class="bg-swatch" data-bg="bg-coffee-1" title="Cafe wood" style="background:linear-gradient(180deg,#c9b49a,#8e6f56);"></div>
          <div class="bg-swatch" data-bg="bg-coffee-2" title="Latte art" style="background:linear-gradient(180deg,#efe3d8,#efe0d2);"></div>
        </div>
      </div>

      <div class="section">
        <div class="label">Tải xuống và chia sẻ</div>
        <div class="row">
          <button class="download" id="downloadBtn">Download</button>
          <button class="btn" id="openPreview">Open image</button>
        </div>
        <div class="socials">
          <a id="shareFacebook" href="#">Facebook</a>
          <a id="shareInstagram" href="#">Instagram</a>
          <a id="shareThreads" href="#">Threads</a>
          <a id="shareTikTok" href="#">TikTok</a>
        </div>
      </div>

    </div>
  </div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
<script>
  // initial data
  const stickers = [];
  const stickerBoard = document.getElementById('stickerBoard');
  const garnish = document.getElementById('garnish');
  const cupSticker = document.getElementById('cupSticker');
  const appliedCount = document.getElementById('appliedCount');
  const cupNameInput = document.getElementById('cupNameInput');
  const exportArea = document.getElementById('exportArea');
  let selectedBg = 'bg-xmas-1';

  // generate 16 stickers with cute SVG icons and colors
  const stickerIcons = [
    '🎄','🍬','🍪','❄️','⭐','☕','🎁','🍫','🕯️','🍭','⛄','🔔','🧣','🧤','🍯','🍒'
  ];
  for(let i=0;i<16;i++){
    const el = document.createElement('div');
    el.className = 'sticker-thumb';
    el.dataset.index = i;
    el.innerHTML = `<div style="text-align:center"><div style="font-size:18px">${stickerIcons[i%stickerIcons.length]}</div><div style="font-size:10px;margin-top:6px">Sticker ${i+1}</div></div>`;
    el.addEventListener('click', ()=>toggleSticker(i, el));
    stickerBoard.appendChild(el);
  }

  function toggleSticker(i, el){
    const idx = stickers.indexOf(i);
    if(idx>-1){
      stickers.splice(idx,1);
      el.classList.remove('active');
    } else {
      stickers.push(i);
      el.classList.add('active');
    }
    renderStickers();
  }

  function renderStickers(){
    // clear small stickers
    document.querySelectorAll('.sticker.small').forEach(e=>e.remove());
    stickers.slice(0,6).forEach((s, i)=>{
      const node = document.createElement('div');
      node.className = 'sticker small';
      node.style.left = 50 + (i%3)*22 + '%';
      node.style.transform = 'translateX(-50%)';
      node.style.bottom = (110 + Math.floor(i/3)*30) + 'px';
      node.innerHTML = `<div style="font-size:18px">${stickerIcons[s%stickerIcons.length]}</div>`;
      document.getElementById('cupWrap').appendChild(node);
    });
    appliedCount.textContent = stickers.length;
    // if there is at least one sticker set main sticker text
    cupSticker.style.display = stickers.length? 'block' : 'none';
    if(stickers.length) cupSticker.textContent = stickerIcons[stickers[0]%stickerIcons.length] + ' ' + (cupNameInput.value || 'Merry Christmas');
  }

  // sugar buttons
  document.querySelectorAll('#sugarOptions .btn').forEach(btn=>{
    btn.addEventListener('click', ()=>{
      document.querySelectorAll('#sugarOptions .btn').forEach(b=>b.classList.remove('active'));
      btn.classList.add('active');
      const val = btn.dataset.val;
      const foam = document.getElementById('foam');
      // change foam size by sugar level to simulate more foam for sweetness
      const h = 24 + (100 - parseInt(val)) * 0.18; // smaller foam for sweeter
      foam.style.height = h + 'px';
    });
  });

  // topping checkboxes
  document.querySelectorAll('#toppingOptions input[type=checkbox]').forEach((cb, idx)=>{
    cb.addEventListener('change', ()=>{
      updateToppings();
    });
  });

  function updateToppings(){
    // remove old topping elements
    document.querySelectorAll('.topping-elm').forEach(e=>e.remove());
    const checked = Array.from(document.querySelectorAll('#toppingOptions input[type=checkbox]:checked')).map(i=>i.value);
    // simple visual additions
    checked.forEach((t,i)=>{
      const el = document.createElement('div');
      el.className = 'topping-elm';
      el.style.position = 'absolute';
      el.style.left = 50 + (i-1)*12 + '%';
      el.style.transform = 'translateX(-50%)';
      el.style.top = 50 + 'px';
      el.style.fontSize = '12px';
      el.style.padding = '6px 8px';
      el.style.borderRadius = '10px';
      el.style.background = 'rgba(255,255,255,0.9)';
      el.style.boxShadow = '0 8px 20px rgba(0,0,0,0.08)';
      el.textContent = t.split(' ')[0];
      document.getElementById('cupWrap').appendChild(el);
    });
  }

  // background selections
  document.querySelectorAll('.bg-swatch').forEach(s=>{
    s.addEventListener('click', ()=>{
      document.querySelectorAll('.bg-swatch').forEach(x=>x.classList.remove('active'));
      s.classList.add('active');
      selectedBg = s.dataset.bg;
      applyBackground(selectedBg);
    });
  });
  // set default active
  document.querySelector('.bg-swatch').classList.add('active');
  applyBackground(selectedBg);

  function applyBackground(name){
    const area = exportArea;
    // apply simple decorative backgrounds
    if(name==='bg-xmas-1'){
      area.style.backgroundImage = 'radial-gradient(circle at 20% 20%, rgba(255,255,255,0.06), transparent 10%), linear-gradient(180deg,#2c1f1b,#4b372f)';
    } else if(name==='bg-xmas-2'){
      area.style.backgroundImage = 'linear-gradient(180deg,#112619,#2b3e2f), radial-gradient(circle at 80% 20%,rgba(255,255,255,0.06),transparent 6%)';
    } else if(name==='bg-xmas-3'){
      area.style.backgroundImage = 'linear-gradient(180deg,#f7fbff,#dfeaf2)';
    } else if(name==='bg-coffee-1'){
      area.style.backgroundImage = 'linear-gradient(180deg,#e6d5c9,#c9b49a)';
    } else if(name==='bg-coffee-2'){
      area.style.backgroundImage = 'linear-gradient(180deg,#f6eadf,#efe0d2)';
    }
    area.style.backgroundRepeat = 'no-repeat';
    area.style.backgroundSize = 'cover';
  }

  // cup name change updates sticker
  cupNameInput.addEventListener('input', ()=>{
    if(stickers.length) cupSticker.textContent = stickerIcons[stickers[0]%stickerIcons.length] + ' ' + (cupNameInput.value || 'Merry Christmas');
  });

  // generate image via html2canvas and download
  const downloadBtn = document.getElementById('downloadBtn');
  const openPreview = document.getElementById('openPreview');
  let lastBlobUrl = null;

  async function renderExport(){
    // temporarily remove UI outside export area
    // use html2canvas
    const node = document.getElementById('cupWrap').parentElement; // export area
    const canvas = await html2canvas(node, {backgroundColor: null, scale:2, useCORS:true});
    return new Promise(resolve=>canvas.toBlob(b=>resolve(b)));
  }

  downloadBtn.addEventListener('click', async ()=>{
    const blob = await renderExport();
    const name = (cupNameInput.value || 'my_coffee').replace(/[^a-z0-9_]+/gi,'_');
    const url = URL.createObjectURL(blob);
    const a = document.createElement('a');
    a.href = url;
    a.download = name + '.png';
    document.body.appendChild(a);
    a.click();
    a.remove();
    URL.revokeObjectURL(url);
  });

  openPreview.addEventListener('click', async ()=>{
    const blob = await renderExport();
    if(lastBlobUrl) URL.revokeObjectURL(lastBlobUrl);
    lastBlobUrl = URL.createObjectURL(blob);
    window.open(lastBlobUrl, '_blank');
  });

  // social share buttons open preview then user can share manually
  document.getElementById('shareFacebook').addEventListener('click', async (e)=>{
    e.preventDefault();
    const blob = await renderExport();
    const url = URL.createObjectURL(blob);
    window.open('https://www.facebook.com/sharer/sharer.php?u='+encodeURIComponent(url));
  });
  document.getElementById('shareInstagram').addEventListener('click', async (e)=>{
    e.preventDefault();
    alert('Instagram web sharing is limited. After preview opens, download image and share from Instagram app.');
    const blob = await renderExport();
    const url = URL.createObjectURL(blob);
    window.open(url);
  });
  document.getElementById('shareThreads').addEventListener('click', async (e)=>{
    e.preventDefault();
    const blob = await renderExport();
    const url = URL.createObjectURL(blob);
    window.open(url);
  });
  document.getElementById('shareTikTok').addEventListener('click', async (e)=>{
    e.preventDefault();
    alert('TikTok sharing works best from the app. Download then upload in TikTok app.');
    const blob = await renderExport();
    const url = URL.createObjectURL(blob);
    window.open(url);
  });

  // initial tiny garnish elements: candy music
  function makeCandy(type){
    const d = document.createElement('div');
    d.className = 'candy';
    d.innerHTML = type === 'cane' ?
    `<svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M7 4c0 0 3 1 5 3s5 5 5 5" stroke="#c62828" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round"/><path d="M8 3c0 0 3 1 5 3" stroke="#fff" stroke-width="1.2" fill="none" stroke-linecap="round" stroke-linejoin="round"/></svg>`:
    `<svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><circle cx="12" cy="12" r="8" fill="#7b4f3a"/><circle cx="10" cy="10" r="1.8" fill="#fff"/></svg>`;
    return d;
  }
  garnish.appendChild(makeCandy('cane'));
  garnish.appendChild(makeCandy('cookie'));

  // small interactions: rotate cup on hover
  const cupWrap = document.getElementById('cupWrap');
  cupWrap.addEventListener('mouseenter', ()=>cupWrap.style.transform = 'rotateX(8deg) rotateY(-8deg)');
  cupWrap.addEventListener('mouseleave', ()=>cupWrap.style.transform = 'rotateX(0deg) rotateY(0deg)');

</script>
</body>
</html>
