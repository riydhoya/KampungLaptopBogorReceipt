<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Kampung Laptop Bogor – Receipt</title>
<style>
:root{
  color-scheme:light;
  --bg:#F5F5F7; --card:#FFFFFF; --ink:#111111; --muted:#888888; --line:#B8B8BC;
  --font:-apple-system,BlinkMacSystemFont,"SF Pro Display","SF Pro Text","Helvetica Neue",system-ui,Arial,sans-serif;
  --D:7s;
  box-sizing:border-box;
  padding-top:env(safe-area-inset-top,0px);
}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{
  margin:0;background:var(--bg);color:var(--ink);font-family:var(--font);
  -webkit-font-smoothing:antialiased;min-height:100vh;
  display:flex;flex-direction:column;align-items:center;
  padding:36px 16px 170px;overflow-x:hidden;
}

/* ---------- PRINTER ---------- */
.stage{width:min(430px,100%);display:flex;flex-direction:column;align-items:center}
.printer{
  position:relative;z-index:2;width:100%;height:178px;border-radius:30px 30px 22px 22px;
  background:linear-gradient(180deg,#3a3a3d 0%,#2a2a2d 55%,#1d1d1f 100%);
  box-shadow:0 1px 0 rgba(255,255,255,.18) inset,0 -2px 0 rgba(0,0,0,.35) inset,
             0 24px 40px -12px rgba(0,0,0,.35),0 8px 14px rgba(0,0,0,.18);
  padding:22px 26px;color:#d9d9dc;
}
.printer.busy{animation:hum .09s linear infinite}
@keyframes hum{0%{transform:translateX(0)}50%{transform:translateX(.5px)}100%{transform:translateX(-.5px)}}
.brand{display:flex;justify-content:space-between;align-items:center}
.brand b{font-size:12px;letter-spacing:.26em;font-weight:600;color:#c9c9cd}
.led{width:9px;height:9px;border-radius:50%;background:#555;box-shadow:0 0 0 2px #1a1a1c inset}
.printer.busy .led{background:#fff;box-shadow:0 0 8px rgba(255,255,255,.9);animation:blink .5s steps(2) infinite}
@keyframes blink{50%{opacity:.25}}
.panel{margin-top:16px;display:flex;gap:10px;align-items:center}
.panel i{display:block;height:6px;border-radius:3px;background:#1a1a1c;box-shadow:0 1px 0 rgba(255,255,255,.08)}
.panel i:nth-child(1){width:46px}.panel i:nth-child(2){width:22px}.panel i:nth-child(3){width:22px}
.model{position:absolute;right:26px;top:70px;font-size:11px;color:#77777b;letter-spacing:.12em}
.slot{
  position:absolute;left:50%;bottom:16px;transform:translateX(-50%);
  width:min(350px,calc(100% - 44px));height:13px;border-radius:7px;background:#050505;
  box-shadow:0 2px 0 rgba(255,255,255,.14),0 -1px 3px rgba(0,0,0,.9) inset;
}

/* ---------- PAPER ---------- */
.feed{
  position:relative;z-index:1;margin-top:-10px;width:min(300px,82vw);
  clip-path:inset(0 -70px -120px -70px);
}
.feed::before{ /* shadow under slot */
  content:"";position:absolute;left:0;right:0;top:0;height:26px;z-index:3;pointer-events:none;
  background:linear-gradient(180deg,rgba(0,0,0,.28),rgba(0,0,0,0));
}
.paper{
  position:relative;background:#fff;padding:34px 22px 40px;transform:translateY(-102%);
  filter:drop-shadow(0 14px 18px rgba(0,0,0,.16)) drop-shadow(0 2px 3px rgba(0,0,0,.12));
  font-size:13px;line-height:1.45;font-variant-numeric:tabular-nums;
}
.paper::after{ /* torn thermal edge */
  content:"";position:absolute;left:0;right:0;top:100%;height:9px;
  background:conic-gradient(from -45deg at bottom,#fff 90deg,#0000 0) 0/18px 100%;
}
.paper.printing{animation:feed var(--D) steps(170,end) forwards,settle .5s ease-out var(--D) forwards}
@keyframes feed{from{transform:translateY(-102%)}to{transform:translateY(0)}}
@keyframes settle{0%{transform:translateY(0)}40%{transform:translateY(5px)}100%{transform:translateY(0)}}

.ln{opacity:0}
.printing .ln{animation:ink .7s ease-out both}
@keyframes ink{from{opacity:0;color:#c8c8cc}to{opacity:1}}

.c{text-align:center}
.shop{font-size:17px;font-weight:700;letter-spacing:.04em;line-height:1.25}
.sub{font-size:11px;letter-spacing:.3em;color:var(--muted);font-weight:600;margin-top:4px}
.rule{border:0;border-top:1.5px dashed var(--line);margin:14px 0}
.row{display:flex;justify-content:space-between;gap:12px}
.row span:first-child,.lbl{color:var(--muted)}
.row span:last-child{text-align:right;font-weight:600}
.lbl{font-size:11px;letter-spacing:.08em;text-transform:uppercase;margin-bottom:2px}
.item{font-weight:700;font-size:14px}
.spec{padding-left:0}
.total{display:flex;justify-content:space-between;align-items:baseline;font-weight:800;font-size:16px}
.total span:last-child{font-size:19px}
.thanks{font-weight:700;letter-spacing:.16em;font-size:13px;margin-top:2px}
.bars{height:30px;margin:14px auto 0;width:150px;
  background:repeating-linear-gradient(90deg,#111 0 2px,#fff 2px 4px,#111 4px 5px,#fff 5px 8px,#111 8px 11px,#fff 11px 12px)}

/* ---------- CONTROLS ---------- */
.bar{
  position:fixed;left:0;right:0;bottom:0;z-index:10;
  display:flex;flex-wrap:wrap;justify-content:center;gap:10px;
  padding:14px 16px calc(env(safe-area-inset-bottom,0px) + 14px);
  background:rgba(245,245,247,.82);-webkit-backdrop-filter:blur(20px) saturate(180%);backdrop-filter:blur(20px) saturate(180%);
  border-top:1px solid rgba(184,184,188,.5);
}
.btn{
  appearance:none;border:0;cursor:pointer;background:#000;color:#fff;font:600 15px/1 var(--font);
  min-height:48px;padding:0 24px;border-radius:999px;box-shadow:0 6px 16px rgba(0,0,0,.18);
  transition:transform .15s ease,opacity .2s ease;
}
.btn:active:not(:disabled){transform:scale(.96)}
.btn:disabled{opacity:.32;cursor:default;box-shadow:none}
.btn:focus-visible{outline:2px solid #000;outline-offset:3px}
@media (max-width:520px){
  .btn.main{flex:1 1 100%}
  .btn{flex:1 1 auto;padding:0 16px;font-size:14px}
}
@media (prefers-reduced-motion:reduce){.printer.busy{animation:none}}

/* ---------- PRINT / PDF ---------- */
@page{size:80mm auto;margin:0}
@media print{
  body{background:#fff;padding:0;display:block;min-height:0}
  .printer,.bar,.feed::before,.paper::after{display:none!important}
  .stage{width:80mm}
  .feed{clip-path:none;width:80mm;margin:0}
  .paper{transform:none!important;animation:none!important;filter:none;padding:8mm 6mm}
  .ln{opacity:1!important;animation:none!important}
}
</style>
</head>
<body>
<main class="stage">
  <section class="printer" id="printer" aria-label="Thermal printer">
    <div class="brand"><b>KAMPUNG LAPTOP</b><span class="led"></span></div>
    <div class="panel"><i></i><i></i><i></i></div>
    <div class="model">TP-80 THERMAL</div>
    <div class="slot"></div>
  </section>

  <section class="feed" aria-live="polite">
    <article class="paper" id="paper">
      <div class="ln c shop">KAMPUNG LAPTOP<br>BOGOR</div>
      <div class="ln c sub">SALES RECEIPT</div>
      <hr class="ln rule">
      <div class="ln row"><span>Tanggal</span><span id="date">–</span></div>
      <div class="ln row" style="margin-top:6px"><span>Nama Pembeli</span><span>Hannah</span></div>
      <div class="ln row" style="margin-top:6px"><span>No. Telepon</span><span>081234567890</span></div>
      <hr class="ln rule">
      <div class="ln lbl">Nama Barang</div>
      <div class="ln item">Macbook Air M1 2020</div>
      <div class="ln lbl" style="margin-top:12px">Spesifikasi</div>
      <div class="ln">Apple M1</div>
      <div class="ln">RAM 8 GB</div>
      <div class="ln">SSD 256 GB</div>
      <div class="ln">macOS 27</div>
      <hr class="ln rule">
      <div class="ln row"><span>Harga Jual</span><span>Rp 12.950.000</span></div>
      <div class="ln row" style="margin-top:6px"><span>Potongan Harga</span><span>Rp 750.000</span></div>
      <hr class="ln rule" style="border-top-style:solid;border-top-color:#111">
      <div class="ln total"><span>TOTAL</span><span>Rp 12.200.000</span></div>
      <hr class="ln rule">
      <div class="ln c thanks">TERIMA KASIH!</div>
      <div class="ln bars" aria-hidden="true"></div>
    </article>
  </section>
</main>

<nav class="bar" aria-label="Kontrol receipt">
  <button class="btn main" id="bPrint">Print Receipt</button>
  <button class="btn" id="bReplay" disabled>Replay Animation</button>
  <button class="btn" id="bPdf" disabled>Download PDF</button>
</nav>

<script>
(function(){
  var paper=document.getElementById('paper'), printer=document.getElementById('printer');
  var bPrint=document.getElementById('bPrint'), bReplay=document.getElementById('bReplay'), bPdf=document.getElementById('bPdf');
  var D=7, running=false;

  var now=new Date();
  document.getElementById('date').textContent =
    now.toLocaleDateString('id-ID',{day:'2-digit',month:'short',year:'numeric'})+' '+
    now.toLocaleTimeString('id-ID',{hour:'2-digit',minute:'2-digit'}).replace(':','.');

  function reset(){
    paper.classList.remove('printing');
    void paper.offsetWidth;
  }
  function start(){
    if(running) return;
    running=true;
    reset();
    var H=paper.offsetHeight;
    // each line "ink" appears as it leaves the printer slot
    paper.querySelectorAll('.ln').forEach(function(l){
      var t=D*(1-(l.offsetTop/H));
      l.style.animationDelay=Math.max(0,t).toFixed(2)+'s';
    });
    bPrint.disabled=bReplay.disabled=bPdf.disabled=true;
    printer.classList.add('busy');
    paper.classList.add('printing');
  }
  paper.addEventListener('animationend',function(e){
    if(e.animationName==='settle'){
      running=false;
      printer.classList.remove('busy');
      bReplay.disabled=false; bPdf.disabled=false;
    }
  });

  bPrint.addEventListener('click',start);
  bReplay.addEventListener('click',function(){ if(!running){ reset(); start(); }});
  bPdf.addEventListener('click',function(){ try{ window.print(); }catch(e){} });
})();
</script>
</body>
</html>
