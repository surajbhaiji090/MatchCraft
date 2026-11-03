<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>MatchCraft – Cricket Poster Maker</title>
<meta name="theme-color" content="#7b3fe4">
<link rel="icon" id="fav" href="data:,">
<link rel="apple-touch-icon" id="ati" href="data:,">
<style>
:root{--bg:#121212;--panel:#1e1e1e;--field:#2a2a2a;--line:#333;--text:#fff;--muted:#aaa;--pink:#e6007e;--h:#ffd700}
@media (prefers-color-scheme:light){:root{--bg:#f1f1f5;--panel:#fff;--field:#f4f4f8;--line:#ddd;--text:#111;--muted:#555;--h:#b8000a}}
*{box-sizing:border-box;margin:0;padding:0;font-family:'Segoe UI',Tahoma,Verdana,sans-serif}
body{background:var(--bg);color:var(--text);padding:0 12px calc(24px + env(safe-area-inset-bottom));padding-top:env(safe-area-inset-top)}
h1{font-size:1.2rem;color:var(--h);text-align:center;padding:12px 0 8px}
.brand{display:flex;align-items:center;justify-content:center;gap:10px;padding:10px 0 6px}
.brand canvas{width:48px;height:48px;border-radius:12px;box-shadow:0 4px 12px rgba(0,0,0,.4)}
.brand h1{padding:0;text-align:left;line-height:1.1}.brand span{font-size:.72rem;color:var(--muted)}
label.ck{display:flex;gap:8px;align-items:center;color:var(--text);font-size:.9rem;font-weight:600}
#splash{position:fixed;inset:0;z-index:99;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:10px;background:linear-gradient(135deg,#ff512f,#dd2476,#7b3fe4,#4facfe);color:#fff;transition:opacity .5s}
#splash.off{opacity:0;pointer-events:none}
#splash canvas{width:160px;height:160px;border-radius:36px;box-shadow:0 14px 40px rgba(0,0,0,.4)}
#splash b{font-size:1.8rem;font-weight:900}#splash i{opacity:.85}
.tabs{display:flex;gap:8px;position:sticky;top:env(safe-area-inset-top);z-index:5;background:var(--bg);padding:6px 0 10px}
.tabs button{flex:1;padding:12px 6px;border:2px solid var(--line);border-radius:10px;background:var(--panel);color:var(--text);font-size:.85rem;font-weight:700}
.tabs button.on{background:linear-gradient(135deg,#e6007e,#ff4da6);border-color:transparent;color:#fff}
.page{display:none;max-width:520px;margin:0 auto}.page.on{display:block}
.cv{border-radius:12px;overflow:hidden;background:#000;box-shadow:0 10px 25px rgba(0,0,0,.5)}
canvas{width:100%;height:auto;display:block}
.acts{display:flex;gap:8px;margin:12px 0}
.btn{flex:1;padding:14px 6px;border:0;border-radius:10px;color:#fff;font-size:.85rem;font-weight:700;text-transform:uppercase;background:linear-gradient(135deg,#e6007e,#ff4da6)}
.btn.dl{background:linear-gradient(135deg,#00c6ff,#0072ff)}.btn.sh{background:linear-gradient(135deg,#11998e,#38ef7d)}
.btn:active{transform:scale(.97)}
details{background:var(--panel);border:1px solid var(--line);border-radius:12px;margin-bottom:10px;padding:0 14px}
summary{padding:14px 0;font-weight:700;font-size:.85rem;color:var(--pink);text-transform:uppercase;letter-spacing:1px;cursor:pointer}
details>div{padding-bottom:10px}
.row{display:flex;gap:10px}.row>.fg{flex:1;min-width:0}
.fg{margin-bottom:12px}
label{display:block;font-size:.78rem;margin-bottom:5px;color:var(--muted)}
input[type=text],input[type=file],select{width:100%;padding:12px;background:var(--field);border:1px solid var(--line);border-radius:8px;color:var(--text);font-size:16px}
input[type=file]{font-size:.75rem;padding:8px}
input[type=color]{width:100%;height:44px;padding:3px;background:var(--field);border:1px solid var(--line);border-radius:8px}
input[type=range]{width:100%;accent-color:var(--pink)}
</style>
</head>
<body>
<div id="splash"><canvas id="sp" width="320" height="320"></canvas><b>MatchCraft</b><i>Cricket Poster Maker</i></div>
<div class="brand"><canvas id="lg" width="96" height="96"></canvas><div><h1>MatchCraft</h1><span>Cricket Poster Maker</span></div></div>
<div class="tabs">
  <button class="on" data-t="A">Match Day Poster</button>
  <button data-t="B">Result Graphic</button>
</div>

<!-- ===== SIDE A : POSTER ===== -->
<div class="page on" id="pA">
  <div class="cv"><canvas id="cA" width="1080" height="1350"></canvas></div>
  <div class="acts">
    <button class="btn" data-up="A">Update</button>
    <button class="btn dl" data-dl="A">Download</button>
    <button class="btn sh" data-sh="A">Share</button>
  </div>
  <details open><summary>Text</summary><div>
    <div class="row"><div class="fg"><label>Main Title</label><input type="text" id="title" value="MATCH DAY"></div>
    <div class="fg"><label>Year / Center</label><input type="text" id="year" value="2026"></div></div>
    <div class="row"><div class="fg"><label>Team 1</label><input type="text" id="team1" value="JANAKPUR BOLTS"></div>
    <div class="fg"><label>Team 2</label><input type="text" id="team2" value="BIRATNAGAR KINGS"></div></div>
    <div class="fg"><label>Venue</label><input type="text" id="venue" value="TU INTERNATIONAL CRICKET GROUND, KIRTIPUR"></div>
    <div class="fg"><label>Date &amp; Time</label><input type="text" id="date" value="3RD NOVEMBER 2026 | 12:30 PM, TUESDAY"></div>
    <div class="row"><div class="fg"><label>Left Hashtag</label><input type="text" id="hash1" value="#JITTAIJANAKPUR"></div>
    <div class="fg"><label>Right Hashtag</label><input type="text" id="hash2" value="#BOLTSBATTALION"></div></div>
  </div></details>
  <details><summary>Colours</summary><div>
    <div class="fg"><label>Theme</label><select id="preset">
      <option value="0">Pink + Blue</option><option value="1">Red + Navy</option><option value="2">Green + Teal</option>
      <option value="3">Orange + Purple</option><option value="4">Gold + Black</option><option value="5">Sky Blue + Maroon</option><option value="custom">Custom</option></select></div>
    <div class="row"><div class="fg"><label>Left</label><input type="color" id="col-l" value="#e6007e"></div>
    <div class="fg"><label>Right</label><input type="color" id="col-r" value="#0033a0"></div></div>
    <div class="row"><div class="fg"><label>Bottom</label><input type="color" id="col-b" value="#2d1b36"></div>
    <div class="fg"><label>Bar</label><input type="color" id="col-a" value="#cc0066"></div></div>
    <div class="row"><div class="fg"><label>Date Box</label><input type="color" id="col-d" value="#ffc107"></div>
    <div class="fg"><label>Title Box</label><input type="color" id="col-t" value="#00175a"></div></div>
  </div></details>
  <details><summary>Images</summary><div>
    <div class="fg"><label class="ck"><input type="checkbox" id="wm1"> Add MatchCraft logo on poster</label></div>
    <div class="fg"><label>Player Left (PNG)</label><input type="file" id="f-p1" accept="image/*"></div>
    <div class="fg"><label>Left Player Size</label><input type="range" id="s-p1" min="50" max="140" value="100"></div>
    <div class="fg"><label>Player Right (PNG)</label><input type="file" id="f-p2" accept="image/*"></div>
    <div class="fg"><label>Right Player Size</label><input type="range" id="s-p2" min="50" max="140" value="100"></div>
    <div class="row"><div class="fg"><label>Top Left Logo</label><input type="file" id="f-tl" accept="image/*"></div>
    <div class="fg"><label>Top Right Logo</label><input type="file" id="f-tr" accept="image/*"></div></div>
    <div class="row"><div class="fg"><label>Bottom Left Logo</label><input type="file" id="f-bl" accept="image/*"></div>
    <div class="fg"><label>Bottom Right Logo</label><input type="file" id="f-br" accept="image/*"></div></div>
  </div></details>
</div>

<!-- ===== SIDE B : RESULT ===== -->
<div class="page" id="pB">
  <div class="cv"><canvas id="cB" width="800" height="1000"></canvas></div>
  <div class="acts">
    <button class="btn" data-up="B">Update</button>
    <button class="btn dl" data-dl="B">Download</button>
    <button class="btn sh" data-sh="B">Share</button>
  </div>
  <details open><summary>Match Info</summary><div>
    <div class="fg"><label>Tournament</label><input type="text" id="tournament" value="NEPAL PREMIER LEAGUE 2026"></div>
    <div class="row"><div class="fg"><label>Match No.</label><input type="text" id="matchNo" value="12TH MATCH"></div>
    <div class="fg"><label>Result Text</label><input type="text" id="resultText" value="BIK WON BY 02 RUNS"></div></div>
  </div></details>
  <details><summary>Teams</summary><div>
    <div class="row"><div class="fg"><label>Left Score</label><input type="text" id="scoreA" value="174/3"></div>
    <div class="fg"><label>Left Overs</label><input type="text" id="oversA" value="20.0 overs"></div></div>
    <div class="row"><div class="fg"><label>Right Score</label><input type="text" id="scoreB" value="172/7"></div>
    <div class="fg"><label>Right Overs</label><input type="text" id="oversB" value="20.0 overs"></div></div>
  </div></details>
  <details><summary>Images</summary><div>
    <div class="fg"><label class="ck"><input type="checkbox" id="wm2"> Add MatchCraft logo on graphic</label></div>
    <div class="fg"><label>Main Action Photo</label><input type="file" id="r-bg" accept="image/*"></div>
    <div class="row"><div class="fg"><label>Top Left Logo</label><input type="file" id="r-tl" accept="image/*"></div>
    <div class="fg"><label>Top Right Logo</label><input type="file" id="r-tr" accept="image/*"></div></div>
    <div class="row"><div class="fg"><label>Left Team Logo</label><input type="file" id="r-la" accept="image/*"></div>
    <div class="fg"><label>Right Team Logo</label><input type="file" id="r-lb" accept="image/*"></div></div>
  </div></details>
  <details><summary>Colours &amp; 3D</summary><div>
    <div class="row"><div class="fg"><label>Bottom 1</label><input type="color" id="bgc1" value="#1a237e"></div>
    <div class="fg"><label>Bottom 2</label><input type="color" id="bgc2" value="#7b1fa2"></div>
    <div class="fg"><label>Banner</label><input type="color" id="bnc" value="#e91e63"></div></div>
    <div class="row"><div class="fg"><label>Score</label><input type="color" id="scc" value="#ffd600"></div>
    <div class="fg"><label>Result</label><input type="color" id="rsc" value="#00e676"></div>
    <div class="fg"><label>Export</label><select id="scale"><option value="1">800×1000</option><option value="2" selected>1600×2000</option></select></div></div>
    <div class="fg"><label>3D Depth</label><input type="range" id="depth" min="2" max="16" value="8"></div>
  </div></details>
</div>

<script>
const $=id=>document.getElementById(id),V=id=>$(id).value;
const cvs={A:$('cA'),B:$('cB')};
let X;

/* ---------- MatchCraft logo ---------- */
function rg(g,x,y,w,h,r,f){g.beginPath();g.roundRect(x,y,w,h,r);g.fillStyle=f;g.fill()}
function lgr(g,x0,y0,x1,y1,st){const k=g.createLinearGradient(x0,y0,x1,y1);st.forEach((c,i)=>k.addColorStop(i/(st.length-1),c));return k}
function logo(g,w,h){
  g.fillStyle=lgr(g,0,0,w,h,['#ff512f','#dd2476','#7b3fe4','#4facfe']);g.fillRect(0,0,w,h);
  g.fillStyle='rgba(255,255,255,.12)';g.beginPath();g.arc(90,80,150,0,7);g.fill();g.beginPath();g.arc(450,470,170,0,7);g.fill();
  g.save();g.translate(240,236);g.rotate(-.14);
  g.shadowColor='rgba(0,0,0,.45)';g.shadowBlur=30;g.shadowOffsetY=18;rg(g,-130,-160,260,320,26,'#fff');
  g.shadowColor='transparent';g.shadowBlur=0;g.shadowOffsetY=0;
  rg(g,-112,-142,224,170,16,lgr(g,0,-142,0,28,['#00c6ff','#7b2ff7','#ff2d95']));
  g.font='900 78px "Arial Black",Arial';g.textAlign='center';g.textBaseline='middle';g.fillStyle='#7a1250';
  for(let i=7;i>0;i--)g.fillText('3D',i/2,-82+i);g.fillStyle='#fff';g.fillText('3D',0,-82);
  rg(g,-112,44,224,44,10,'#ffd600');rg(g,-80,104,160,14,7,'#d9d9ee');rg(g,-56,128,112,12,6,'#e8e8f5');
  g.restore();
  const bx=338,by=362,R=104;
  g.save();g.shadowColor='rgba(0,0,0,.5)';g.shadowBlur=26;g.shadowOffsetY=16;
  const q=g.createRadialGradient(bx-35,by-40,10,bx,by,R);q.addColorStop(0,'#ff7b7b');q.addColorStop(.55,'#d00000');q.addColorStop(1,'#5a0008');
  g.beginPath();g.arc(bx,by,R,0,7);g.fillStyle=q;g.fill();g.restore();
  g.save();g.beginPath();g.arc(bx,by,R,0,7);g.clip();
  g.strokeStyle='#fff';g.lineWidth=6;g.lineCap='round';g.setLineDash([13,10]);
  g.beginPath();g.arc(bx-R*1.05,by,R*.98,-.85,.85);g.stroke();
  g.beginPath();g.arc(bx+R*1.05,by,R*.98,Math.PI-.85,Math.PI+.85);g.stroke();
  g.setLineDash([]);g.lineWidth=3;g.strokeStyle='rgba(255,255,255,.55)';
  g.beginPath();g.arc(bx-R*1.05,by,R*.98-14,-.8,.8);g.stroke();
  g.beginPath();g.arc(bx+R*1.05,by,R*.98-14,Math.PI-.8,Math.PI+.8);g.stroke();
  g.restore()}
function stamp(g,x,y,s){g.save();g.translate(x-s/2,y-s/2);g.beginPath();g.roundRect(0,0,s,s,s*.22);g.clip();g.scale(s/512,s/512);logo(g,512,512);g.restore()}

/* ---------- tabs ---------- */
document.querySelectorAll('.tabs button').forEach(b=>b.addEventListener('click',()=>{
  document.querySelectorAll('.tabs button').forEach(x=>x.classList.toggle('on',x===b));
  ['A','B'].forEach(k=>$('p'+k).classList.toggle('on',k===b.dataset.t));
  window.scrollTo({top:0});
  draw(b.dataset.t);
}));

/* ---------- helpers ---------- */
function shade(hex,a){const n=parseInt(hex.slice(1),16);let r=n>>16,g=(n>>8)&255,b=n&255;const t=a<0?0:255,p=Math.abs(a);
  r=Math.round(r+(t-r)*p);g=Math.round(g+(t-g)*p);b=Math.round(b+(t-b)*p);return '#'+((1<<24)+(r<<16)+(g<<8)+b).toString(16).slice(1)}
function loader(inputId,store,key,cb){
  $(inputId).addEventListener('change',e=>{
    const f=e.target.files[0];if(!f){store[key]=null;cb();return}
    const u=URL.createObjectURL(f),im=new Image();
    im.onload=()=>{store[key]=im;URL.revokeObjectURL(u);cb()};
    im.onerror=()=>{store[key]=null;alert('Could not load that image.')};
    im.src=u})}
function fit(t,size,maxW){let s=size;X.font=`900 ${s}px "Arial Black",Arial`;
  while(s>12&&X.measureText(t).width>maxW){s-=2;X.font=`900 ${s}px "Arial Black",Arial`}return s}
function t3(t,x,y,size,c1,c2,side,maxW,depth,outline){
  if(!t)return;X.save();const fs=fit(t,size,maxW);
  X.textAlign='center';X.textBaseline='middle';X.lineJoin='round';
  const d=depth||Math.max(3,Math.round(fs/9));
  X.shadowColor='rgba(0,0,0,.6)';X.shadowBlur=16;X.shadowOffsetX=d/2;X.shadowOffsetY=d+4;
  X.fillStyle=side;X.fillText(t,x+d*.5,y+d);
  X.shadowColor='transparent';X.shadowBlur=0;X.shadowOffsetX=0;X.shadowOffsetY=0;
  for(let i=d;i>0;i--)X.fillText(t,x+i*.5,y+i);
  if(outline){X.lineWidth=fs/9;X.strokeStyle=outline;X.strokeText(t,x,y)}
  const g=X.createLinearGradient(0,y-fs/2,0,y+fs/2);g.addColorStop(0,c1);g.addColorStop(1,c2);
  X.fillStyle=g;X.fillText(t,x,y);
  X.lineWidth=1.2;X.strokeStyle='rgba(255,255,255,.4)';X.strokeText(t,x,y);X.restore()}
function rr(x,y,w,h,r,fill){X.beginPath();X.roundRect?X.roundRect(x,y,w,h,r):X.rect(x,y,w,h);X.fillStyle=fill;X.fill()}
function contain(im,cx,cy,mw,mh,bottom,shadow){
  const r=Math.min(mw/im.width,mh/im.height),w=im.width*r,h=im.height*r;
  X.save();if(shadow){X.shadowColor='rgba(0,0,0,.8)';X.shadowBlur=14;X.shadowOffsetY=7}
  X.drawImage(im,cx-w/2,bottom?cy-h:cy-h/2,w,h);X.restore()}

/* ---------- SIDE A : poster ---------- */
const PI={p1:null,p2:null,tl:null,tr:null,bl:null,br:null};let tm;
const sch=()=>{clearTimeout(tm);tm=setTimeout(()=>draw('A'),100)};
Object.keys(PI).forEach(k=>loader('f-'+k,PI,k,sch));
['title','year','team1','team2','venue','date','hash1','hash2','s-p1','s-p2','col-l','col-r','col-b','col-a','col-d','col-t'].forEach(i=>$(i).addEventListener('input',sch));
const PRESETS=[['#e6007e','#0033a0','#2d1b36','#cc0066','#ffc107','#00175a'],['#e10600','#0a2a66','#2a0d0d','#b00500','#ffd400','#06183d'],
['#14a44d','#05575a','#0b2b22','#0e7a38','#ffe14d','#033b3d'],['#ff7a00','#5b1fa8','#2a1540','#d65f00','#ffd23f','#3a1270'],
['#d4a017','#161616','#0b0b0b','#a67c00','#ffffff','#000000'],['#1e9bff','#7a0019','#1a0a14','#0f6fc0','#ffc107','#4a0010']];
$('preset').addEventListener('change',e=>{const p=PRESETS[e.target.value];if(!p)return;
  ['l','r','b','a','d','t'].forEach((k,i)=>$('col-'+k).value=p[i]);sch()});
['l','r','b','a','d','t'].forEach(k=>$('col-'+k).addEventListener('input',()=>$('preset').value='custom'));

function drawA(){
  const c=cvs.A,W=1080,H=1350;c.width=W;c.height=H;X=c.getContext('2d');
  const up=id=>V(id).trim().toUpperCase(),raw=id=>V(id).trim();
  const CL=V('col-l'),CR=V('col-r'),CB=V('col-b'),CA=V('col-a'),CD=V('col-d'),CT=V('col-t');
  let g=X.createLinearGradient(0,0,W,H);g.addColorStop(0,shade(CL,-.25));g.addColorStop(.5,shade(CB,.1));g.addColorStop(1,shade(CR,-.6));
  X.fillStyle=g;X.fillRect(0,0,W,H);
  X.beginPath();X.moveTo(0,0);X.lineTo(W*.55,0);X.lineTo(W*.35,H*.8);X.lineTo(0,H*.8);X.closePath();
  g=X.createLinearGradient(0,0,W/2,H/2);g.addColorStop(0,shade(CL,.15));g.addColorStop(1,shade(CL,-.2));X.fillStyle=g;X.fill();
  X.beginPath();X.moveTo(W*.55,0);X.lineTo(W,0);X.lineTo(W,H*.8);X.lineTo(W*.35,H*.8);X.closePath();
  g=X.createLinearGradient(W,0,W/2,H/2);g.addColorStop(0,CR);g.addColorStop(1,shade(CR,-.6));X.fillStyle=g;X.fill();
  X.fillStyle=CB;X.fillRect(0,H*.8,W,H*.2);X.fillStyle=CA;X.fillRect(0,H-90,W,90);
  [['p1',W*.25],['p2',W*.75]].forEach(([k,cx])=>{if(!PI[k])return;const s=V('s-'+k)/100;
    X.save();X.shadowColor='rgba(0,0,0,.6)';X.shadowBlur=30;X.shadowOffsetY=10;contain(PI[k],cx,800,480*s,600*s,true);X.restore()});
  X.save();X.shadowColor='rgba(0,0,0,.5)';X.shadowBlur=20;X.shadowOffsetY=10;rr(250,50,580,100,15,CT);X.restore();
  t3(up('title'),W/2,100,62,'#fff','#cfd6ff',shade(CT,-.6),540);
  t3(up('year'),W/2,230,90,'#fff','#ddd',shade(CL,-.65),400);
  t3('VS',W/2,350,110,'#ffd700','#b38f00','#5a4500',W-120);
  X.fillStyle=CL;X.beginPath();X.moveTo(150,750);X.lineTo(535,750);X.lineTo(500,830);X.lineTo(150,830);X.closePath();X.fill();
  X.fillStyle=shade(CR,-.45);X.beginPath();X.moveTo(545,750);X.lineTo(930,750);X.lineTo(930,830);X.lineTo(580,830);X.closePath();X.fill();
  t3(up('team1'),330,790,40,'#fff','#eee',shade(CL,-.65),320);
  t3(up('team2'),750,790,40,'#fff','#eee',shade(CR,-.8),320);
  X.fillStyle='#fff';X.textAlign='center';X.textBaseline='alphabetic';
  X.font='bold 30px Arial';X.fillText('VENUE',W/2,910);
  const vs=fit(up('venue'),36,W-120);X.font=`bold ${vs}px Arial`;X.fillText(up('venue'),W/2,960);
  X.save();X.shadowColor='rgba(0,0,0,.6)';X.shadowBlur=15;X.shadowOffsetY=8;rr(150,1010,780,80,20,CD);X.restore();
  const n=parseInt(CD.slice(1),16);X.fillStyle=(((n>>16)*299+((n>>8)&255)*587+(n&255)*114)/1000>140)?'#111':'#fff';
  X.textBaseline='middle';const ds=fit(up('date'),30,740);X.font=`bold ${ds}px Arial`;X.fillText(up('date'),W/2,1051);
  if(PI.tl)contain(PI.tl,120,100,180,100);if(PI.tr)contain(PI.tr,960,100,180,100);
  if(PI.bl)contain(PI.bl,85,790,110,110);if(PI.br)contain(PI.br,995,790,110,110);
  X.fillStyle='#fff';X.textBaseline='middle';
  let s1=fit(raw('hash1'),28,460);X.font=`bold ${s1}px Arial`;X.textAlign='left';X.fillText(raw('hash1'),60,H-45);
  let s2=fit(raw('hash2'),28,460);X.font=`bold ${s2}px Arial`;X.textAlign='right';X.fillText(raw('hash2'),W-60,H-45);
  if($('wm1').checked)stamp(X,540,H-45,72);
}

/* ---------- SIDE B : result ---------- */
const RI={bg:null,tl:null,tr:null,la:null,lb:null};let tb;
const schB=()=>{clearTimeout(tb);tb=setTimeout(()=>draw('B'),100)};
Object.keys(RI).forEach(k=>loader('r-'+k,RI,k,schB));
['tournament','matchNo','resultText','scoreA','oversA','scoreB','oversB','bgc1','bgc2','bnc','scc','rsc','depth'].forEach(i=>$(i).addEventListener('input',schB));

function plate(x,y,w,h,c1,c2,border,d){
  X.save();X.shadowColor='rgba(0,0,0,.7)';X.shadowBlur=18;X.shadowOffsetY=d+2;
  X.fillStyle=shade(c2,-.4);X.fillRect(x,y+d,w,h);
  X.shadowColor='transparent';X.shadowBlur=0;X.shadowOffsetY=0;
  let g=X.createLinearGradient(0,y,0,y+h);g.addColorStop(0,c1);g.addColorStop(1,c2);X.fillStyle=g;X.fillRect(x,y,w,h);
  g=X.createLinearGradient(0,y,0,y+h/2);g.addColorStop(0,'rgba(255,255,255,.4)');g.addColorStop(1,'rgba(255,255,255,0)');X.fillStyle=g;X.fillRect(x,y,w,h/2);
  X.lineWidth=2;X.strokeStyle=border;X.strokeRect(x+4,y+4,w-8,h-8);X.restore()}

function drawB(S=1){
  const c=cvs.B,W=800;c.width=800*S;c.height=1000*S;X=c.getContext('2d');X.setTransform(S,0,0,S,0,0);
  const d=+V('depth'),sc=V('scc'),rc=V('rsc'),bn=V('bnc');
  if(RI.bg){const s=Math.max(W/RI.bg.width,600/RI.bg.height);
    X.drawImage(RI.bg,W/2-RI.bg.width*s/2,300-RI.bg.height*s/2,RI.bg.width*s,RI.bg.height*s);
    const o=X.createLinearGradient(0,0,0,600);o.addColorStop(0,'rgba(0,0,0,0)');o.addColorStop(.75,'rgba(0,0,0,.25)');o.addColorStop(1,'rgba(0,0,0,.65)');
    X.fillStyle=o;X.fillRect(0,0,W,600);
  }else{const g=X.createLinearGradient(0,0,W,600);g.addColorStop(0,'#00c6ff');g.addColorStop(.5,'#7b2ff7');g.addColorStop(1,'#ff2d95');X.fillStyle=g;X.fillRect(0,0,W,600)}
  if(RI.tl)contain(RI.tl,80,60,120,80,false,true);if(RI.tr)contain(RI.tr,720,60,120,80,false,true);
  let g=X.createLinearGradient(0,600,0,1000);g.addColorStop(0,V('bgc1'));g.addColorStop(1,V('bgc2'));X.fillStyle=g;X.fillRect(0,600,W,400);
  g=X.createRadialGradient(400,820,20,400,820,420);g.addColorStop(0,'rgba(255,255,255,.22)');g.addColorStop(1,'rgba(255,255,255,0)');X.fillStyle=g;X.fillRect(0,600,W,400);
  plate(40,590,720,66,shade(bn,.2),shade(bn,-.2),'#ffd54f',d);
  t3(V('tournament').toUpperCase(),W/2,623,30,'#fff','#ffe9f2',shade(bn,-.6),660,Math.round(d*.6),shade(bn,-.7));
  plate(290,690,220,40,'#ffe066','#ff9800','#fff',Math.round(d*.5));
  t3(V('matchNo').toUpperCase(),W/2,711,18,'#fff','#fff3c4','#a85a00',190,Math.round(d*.4),'#7a3d00');
  const sd=shade(sc,-.6);
  t3(V('scoreA'),250,800,58,shade(sc,.4),sc,sd,300,d,'#3a1a00');
  t3(V('scoreB'),550,800,58,shade(sc,.4),sc,sd,300,d,'#3a1a00');
  t3(V('oversA'),250,845,20,'#fff','#e3f2fd','#1565c0',300,Math.round(d*.35),'#0d2b5c');
  t3(V('oversB'),550,845,20,'#fff','#e3f2fd','#1565c0',300,Math.round(d*.35),'#0d2b5c');
  t3('|',400,800,56,'#fff','#ffd6ec','#c2185b',60,Math.round(d*.5),'#5c0a2f');
  if(RI.la)contain(RI.la,105,915,110,110,false,true);if(RI.lb)contain(RI.lb,695,915,110,110,false,true);
  const res=V('resultText').toUpperCase();
  X.save();X.shadowColor=rc;X.shadowBlur=30;t3(res,W/2,950,38,shade(rc,.4),rc,shade(rc,-.6),520,d,'#06331a');X.restore();
  t3(res,W/2,950,38,shade(rc,.4),rc,shade(rc,-.6),520,d,'#06331a');
  if($('wm2').checked)stamp(X,400,52,70);
}

/* ---------- common actions ---------- */
function draw(k){k==='A'?drawA():drawB(1)}
function blobOf(k){
  if(k==='B')drawB(+V('scale'));
  return new Promise(r=>cvs[k].toBlob(b=>{if(k==='B')drawB(1);r(b)},'image/png'))}
const names={A:'matchcraft_poster.png',B:'matchcraft_result.png'};
document.querySelectorAll('[data-up]').forEach(b=>b.addEventListener('click',()=>draw(b.dataset.up)));
document.querySelectorAll('[data-dl]').forEach(b=>b.addEventListener('click',async()=>{
  const k=b.dataset.dl,blob=await blobOf(k),u=URL.createObjectURL(blob),a=document.createElement('a');
  a.href=u;a.download=names[k];document.body.appendChild(a);a.click();a.remove();setTimeout(()=>URL.revokeObjectURL(u),4000)}));
document.querySelectorAll('[data-sh]').forEach(b=>b.addEventListener('click',async()=>{
  const k=b.dataset.sh,blob=await blobOf(k),f=new File([blob],names[k],{type:'image/png'});
  try{
    if(navigator.canShare&&navigator.canShare({files:[f]}))await navigator.share({files:[f],title:'MatchCraft'});
    else{await navigator.clipboard.write([new ClipboardItem({'image/png':blob})]);alert('Image copied to clipboard.')}
  }catch(e){if(e.name!=='AbortError')alert('Share is not supported here. Use Download.')}}));

$('wm1').addEventListener('change',sch);$('wm2').addEventListener('change',schB);
stamp($('lg').getContext('2d'),48,48,96);
stamp($('sp').getContext('2d'),160,160,320);
{const f=document.createElement('canvas');f.width=f.height=192;stamp(f.getContext('2d'),96,96,192);
 const u=f.toDataURL('image/png');$('fav').href=u;$('ati').href=u}
drawA();drawB(1);
setTimeout(()=>$('splash').classList.add('off'),1300);
</script>
</body>
</html>
