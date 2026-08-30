<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Desa Kudungga — Portal Resmi Desa</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,600;9..144,700;9..144,900&family=Plus+Jakarta+Sans:wght@400;500;600;700;800&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.0/chart.umd.min.js"></script>
<style>
:root{
  --green-dark:#0E3F41;
  --green:#146B6E;
  --green-mid:#2C8C86;
  --green-light:#DCEFEC;
  --gold:#C9A227;
  --gold-light:#F3E6B8;
  --paper:#FFFFFF;
  --paper-dark:#EAF0EF;
  --soil:#0B2C2D;
  --soil-light:#1E4547;
  --white:#FFFFFF;
  --ink:#1E2624;
  --ink-soft:#5C6B69;
  --radius:14px;
  --shadow:0 6px 20px rgba(14,63,65,.08);
  --shadow-lg:0 14px 40px rgba(14,63,65,.16);
  --tumpal:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='22' height='13'%3E%3Cpolygon points='0,13 11,0 22,13' fill='%23C9A227'/%3E%3C/svg%3E");
  --vine:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='44' height='16'%3E%3Cpath d='M0 9 Q11 1 22 9 T44 9' stroke='%23C9A227' stroke-width='1.6' fill='none'/%3E%3Ccircle cx='11' cy='4' r='1.6' fill='%230E3F41'/%3E%3Ccircle cx='33' cy='14' r='1.6' fill='%230E3F41'/%3E%3C/svg%3E");
}
*{box-sizing:border-box;}
html{scroll-behavior:smooth;}
body{
  margin:0;
  background:var(--paper);
  color:var(--ink);
  font-family:'Plus Jakarta Sans',sans-serif;
  line-height:1.55;
}
h1,h2,h3,h4{
  font-family:'Fraunces',serif;
  color:var(--green-dark);
  margin:0 0 .4em 0;
  letter-spacing:-.01em;
}
.mono{font-family:'JetBrains Mono',monospace;}
a{color:inherit;}
img,svg{display:block;max-width:100%;}
button{font-family:inherit;cursor:pointer;}
.container{max-width:1180px;margin:0 auto;padding:0 24px;}
.eyebrow{
  text-transform:uppercase;
  letter-spacing:.14em;
  font-size:.72rem;
  font-weight:700;
  color:var(--gold);
  margin-bottom:.5em;
  display:block;
}
.section-head{max-width:640px;margin-bottom:34px;padding-bottom:16px;}
.section-head::after{
  content:'';display:block;width:100%;max-width:220px;height:16px;margin-top:14px;
  background-image:var(--vine);background-repeat:repeat-x;background-size:44px 16px;
}
.section{padding:64px 0;border-bottom:1px solid var(--paper-dark);}
.section:target,.section.active{display:block;}
.pill{
  display:inline-flex;align-items:center;gap:6px;
  background:var(--green-light);color:var(--green-dark);
  font-size:.75rem;font-weight:700;padding:4px 12px;border-radius:99px;
}

/* ===== HEADER / NAV ===== */
.topbar{background:var(--green-dark);color:var(--gold-light);font-size:.78rem;}
.topbar .container{display:flex;justify-content:space-between;align-items:center;padding:7px 24px;flex-wrap:wrap;gap:6px;}
.topbar a{text-decoration:none;color:var(--gold-light);opacity:.9;}
.topbar a:hover{opacity:1;}
header.mainnav{
  position:sticky;top:0;z-index:50;
  background:rgba(243,239,226,.94);
  backdrop-filter:blur(6px);
  border-bottom:1px solid var(--paper-dark);
}
.mainnav .container{display:flex;align-items:center;justify-content:space-between;padding:12px 24px;}
.brand{display:flex;align-items:center;gap:12px;text-decoration:none;}
.brand .crest{
  width:44px;height:44px;border-radius:50%;
  background:var(--green-dark);
  display:flex;align-items:center;justify-content:center;color:var(--gold-light);font-family:'Fraunces',serif;font-weight:700;font-size:1.15rem;
  box-shadow:0 0 0 3px var(--gold),inset 0 0 0 2px rgba(255,255,255,.15);
}
.brand .name{font-family:'Fraunces',serif;font-weight:700;font-size:1.15rem;color:var(--green-dark);line-height:1.1;}
.brand .sub{font-size:.72rem;color:var(--ink-soft);letter-spacing:.04em;}
nav.tabs{display:flex;gap:2px;flex-wrap:wrap;}
nav.tabs button{
  background:none;border:none;padding:9px 12px;border-radius:8px;
  font-size:.82rem;font-weight:600;color:var(--ink-soft);
  display:flex;align-items:center;gap:6px;transition:.15s;
}
nav.tabs button:hover{background:var(--paper-dark);}
nav.tabs button.active{background:var(--green-dark);color:var(--white);}
nav.tabs svg{width:16px;height:16px;flex-shrink:0;}
.hamburger{display:none;background:none;border:2px solid var(--green-dark);border-radius:8px;padding:8px 10px;}
.hamburger div{width:20px;height:2px;background:var(--green-dark);margin:4px 0;}

@media(max-width:980px){
  nav.tabs{display:none;position:absolute;top:100%;left:0;right:0;background:var(--paper);flex-direction:column;padding:8px;border-bottom:1px solid var(--paper-dark);box-shadow:var(--shadow);}
  nav.tabs.open{display:flex;}
  nav.tabs button{justify-content:flex-start;padding:12px;}
  .hamburger{display:block;}
  .mainnav{position:sticky;}
}

/* ===== HERO ===== */
.hero{
  position:relative;background:var(--green-dark);color:var(--white);
  padding:64px 0 0 0;overflow:hidden;
}
.hero .container{position:relative;z-index:2;display:grid;grid-template-columns:1.15fr .85fr;gap:40px;align-items:end;padding-bottom:0;}
.hero h1{color:var(--white);font-size:clamp(2rem,4.2vw,3.4rem);font-weight:700;margin-bottom:.3em;}
.hero p.lead{color:var(--green-light);font-size:1.05rem;max-width:480px;margin-bottom:26px;}
.hero-actions{display:flex;gap:12px;flex-wrap:wrap;margin-bottom:40px;}
.btn{
  border:none;border-radius:9px;padding:12px 20px;font-weight:700;font-size:.9rem;
  display:inline-flex;align-items:center;gap:8px;text-decoration:none;transition:.15s;
}
.btn-gold{background:var(--gold);color:var(--soil);}
.btn-gold:hover{background:var(--gold-light);}
.btn-outline{background:transparent;border:1.5px solid rgba(255,255,255,.5);color:var(--white);}
.btn-outline:hover{border-color:var(--white);}
.btn-green{background:var(--green);color:var(--white);}
.btn-green:hover{background:var(--green-mid);}
.btn-sm{padding:8px 14px;font-size:.8rem;}

.board{
  position:relative;background:var(--soil);border-radius:16px 16px 0 0;padding:34px 26px 0 26px;
}
.board::before{
  content:'';position:absolute;top:0;left:0;right:0;height:13px;
  background-image:var(--tumpal);background-repeat:repeat-x;background-size:22px 13px;
  border-radius:16px 16px 0 0;
}
.board .eyebrow{color:var(--gold-light);}
.board-title{font-family:'Fraunces',serif;color:var(--gold-light);font-size:1.3rem;margin-bottom:16px;}
.board-stats{display:grid;grid-template-columns:1fr 1fr;gap:14px 20px;padding-bottom:22px;}
.board-stat .num{font-family:'JetBrains Mono',monospace;font-size:1.7rem;font-weight:700;color:var(--white);}
.board-stat .lbl{font-size:.72rem;color:var(--gold-light);text-transform:uppercase;letter-spacing:.06em;}
.hero-ribbon{background:var(--gold);color:var(--soil);}
.hero-ribbon .container{display:flex;gap:26px;overflow-x:auto;padding:12px 24px;font-size:.82rem;font-weight:700;white-space:nowrap;}

/* ===== CARDS / GRIDS ===== */
.grid{display:grid;gap:22px;}
.grid-2{grid-template-columns:repeat(2,1fr);}
.grid-3{grid-template-columns:repeat(3,1fr);}
.grid-4{grid-template-columns:repeat(4,1fr);}
@media(max-width:900px){.grid-2,.grid-3,.grid-4{grid-template-columns:1fr 1fr;}}
@media(max-width:620px){.grid-2,.grid-3,.grid-4{grid-template-columns:1fr;}.hero .container{grid-template-columns:1fr;}}

.card{background:var(--white);border-radius:var(--radius);padding:22px;box-shadow:var(--shadow);border:1px solid var(--paper-dark);}
.card h3{font-size:1.05rem;}
.tag{display:inline-block;font-size:.68rem;font-weight:700;text-transform:uppercase;letter-spacing:.05em;padding:3px 9px;border-radius:99px;margin-bottom:8px;}
.tag-berita{background:#DCEFEC;color:var(--green-dark);}
.tag-pengumuman{background:var(--gold-light);color:var(--soil);}
.news-date{font-size:.75rem;color:var(--ink-soft);font-family:'JetBrains Mono',monospace;}

.stat-card{background:var(--white);border-radius:var(--radius);padding:20px;text-align:center;box-shadow:var(--shadow);border:1px solid var(--paper-dark);}
.stat-card .num{font-family:'JetBrains Mono',monospace;font-weight:700;font-size:1.9rem;color:var(--green-dark);}
.stat-card .lbl{font-size:.78rem;color:var(--ink-soft);}

table{width:100%;border-collapse:collapse;font-size:.88rem;}
th,td{text-align:left;padding:10px 12px;border-bottom:1px solid var(--paper-dark);}
th{background:var(--paper-dark);font-size:.72rem;text-transform:uppercase;letter-spacing:.04em;color:var(--soil);}
td.num,th.num{text-align:right;font-family:'JetBrains Mono',monospace;}
tr.total td{font-weight:700;background:#FBF8EF;}
.progress-bar{background:var(--paper-dark);border-radius:99px;height:8px;overflow:hidden;margin-top:4px;}
.progress-bar span{display:block;height:100%;background:var(--green);border-radius:99px;}

form.stack{display:flex;flex-direction:column;gap:14px;}
.field label{display:block;font-size:.8rem;font-weight:700;margin-bottom:5px;color:var(--soil);}
.field input,.field select,.field textarea{
  width:100%;padding:10px 12px;border:1.5px solid var(--paper-dark);border-radius:8px;
  font-family:inherit;font-size:.9rem;background:var(--white);color:var(--ink);
}
.field input:focus,.field select:focus,.field textarea:focus{outline:2px solid var(--green-mid);outline-offset:1px;border-color:var(--green);}
.field textarea{resize:vertical;min-height:90px;}
.form-note{font-size:.8rem;color:var(--ink-soft);}
.status-msg{padding:10px 14px;border-radius:8px;font-size:.85rem;font-weight:600;display:none;}
.status-msg.ok{display:block;background:#DCEFEC;color:var(--green-dark);}
.status-msg.err{display:block;background:#F4D9D0;color:#7A2E1D;}

.tabgroup{display:flex;gap:8px;margin-bottom:22px;flex-wrap:wrap;}
.tabgroup button{
  background:var(--white);border:1.5px solid var(--paper-dark);padding:9px 16px;border-radius:99px;
  font-weight:700;font-size:.82rem;color:var(--ink-soft);
}
.tabgroup button.active{background:var(--green-dark);border-color:var(--green-dark);color:var(--white);}

.gallery-item{border-radius:var(--radius);overflow:hidden;background:var(--white);box-shadow:var(--shadow);border:1px solid var(--paper-dark);}
.gallery-thumb{
  height:150px;display:flex;align-items:center;justify-content:center;font-size:2.4rem;color:var(--white);position:relative;
}
.gallery-thumb .gtag{position:absolute;top:10px;left:10px;background:rgba(0,0,0,.35);color:#fff;font-size:.68rem;font-weight:700;padding:3px 9px;border-radius:99px;text-transform:uppercase;letter-spacing:.04em;}
.gallery-body{padding:14px;}
.gallery-body h4{font-size:.94rem;margin-bottom:4px;font-family:'Fraunces',serif;color:var(--green-dark);}
.gallery-body .gmeta{font-size:.72rem;color:var(--ink-soft);display:block;margin-bottom:6px;}
.gallery-body .gdesc{font-size:.82rem;color:var(--ink);margin:0;line-height:1.45;}

.doc-row{display:flex;align-items:center;gap:14px;padding:14px;border:1px solid var(--paper-dark);border-radius:10px;background:var(--white);margin-bottom:10px;}
.doc-icon{width:38px;height:38px;border-radius:8px;background:var(--paper-dark);display:flex;align-items:center;justify-content:center;flex-shrink:0;font-size:1.1rem;}
.doc-meta{flex:1;}
.doc-meta h4{font-size:.9rem;margin-bottom:2px;}
.doc-meta span{font-size:.74rem;color:var(--ink-soft);}

.umkm-card{background:var(--white);border-radius:var(--radius);overflow:hidden;box-shadow:var(--shadow);border:1px solid var(--paper-dark);display:flex;flex-direction:column;}
.umkm-thumb{height:130px;display:flex;align-items:center;justify-content:center;font-size:2.4rem;}
.umkm-body{padding:16px;flex:1;display:flex;flex-direction:column;gap:6px;}
.umkm-price{font-family:'JetBrains Mono',monospace;font-weight:700;color:var(--gold);}
.umkm-owner{font-size:.78rem;color:var(--ink-soft);}

.orgchart{display:flex;flex-direction:column;align-items:center;gap:10px;}
.org-box{background:var(--white);border:1.5px solid var(--green);border-radius:10px;padding:10px 18px;font-size:.85rem;font-weight:700;text-align:center;color:var(--green-dark);box-shadow:var(--shadow);}
.org-row{display:flex;gap:14px;flex-wrap:wrap;justify-content:center;}
.org-line{width:2px;height:16px;background:var(--green);}

.map-wrap{display:grid;grid-template-columns:1.4fr 1fr;gap:24px;}
@media(max-width:800px){.map-wrap{grid-template-columns:1fr;}}
.map-region{cursor:pointer;transition:.15s;stroke:var(--white);stroke-width:2;}
.map-region:hover,.map-region.selected{filter:brightness(1.12);stroke:var(--gold);stroke-width:3;}
.map-info{background:var(--white);border-radius:var(--radius);padding:20px;box-shadow:var(--shadow);border:1px solid var(--paper-dark);min-height:220px;}

.social-row{display:flex;gap:12px;flex-wrap:wrap;}
.social-btn{
  display:flex;align-items:center;gap:10px;padding:12px 18px;border-radius:10px;background:var(--white);
  box-shadow:var(--shadow);border:1px solid var(--paper-dark);font-weight:700;font-size:.88rem;text-decoration:none;color:var(--ink);
}
.social-btn .ic{width:30px;height:30px;border-radius:50%;display:flex;align-items:center;justify-content:center;color:#fff;font-size:.95rem;}

footer{background:var(--soil);color:var(--white);position:relative;padding-top:13px;}
footer::before{
  content:'';display:block;height:13px;
  background-image:var(--tumpal);background-repeat:repeat-x;background-size:22px 13px;
}
footer .container{padding:44px 24px 26px;display:grid;grid-template-columns:1.4fr 1fr 1fr 1fr;gap:32px;color:var(--white);}
footer .container p{color:var(--white);}
@media(max-width:800px){footer .container{grid-template-columns:1fr 1fr;}}
footer h4{color:var(--gold-light);font-size:.85rem;text-transform:uppercase;letter-spacing:.06em;margin-bottom:14px;}
footer a{text-decoration:none;color:var(--paper);opacity:.85;font-size:.86rem;display:block;margin-bottom:8px;}
footer a:hover{opacity:1;text-decoration:underline;}
.foot-bottom{border-top:1px solid rgba(255,255,255,.12);text-align:center;padding:16px;font-size:.76rem;color:var(--green-light);}

.admin-toggle{position:fixed;bottom:20px;right:20px;z-index:60;}
.admin-panel{background:var(--soil);color:var(--paper);padding:10px 16px;border-radius:10px;font-size:.78rem;box-shadow:var(--shadow-lg);display:flex;align-items:center;gap:10px;}
.hidden{display:none !important;}
.chart-wrap{background:var(--white);border-radius:var(--radius);padding:18px;box-shadow:var(--shadow);border:1px solid var(--paper-dark);}
.badge-req{font-size:.68rem;background:#F4D9D0;color:#7A2E1D;padding:2px 8px;border-radius:99px;font-weight:700;}
.badge-proses{font-size:.68rem;background:var(--gold-light);color:var(--soil);padding:2px 8px;border-radius:99px;font-weight:700;}
.badge-selesai{font-size:.68rem;background:var(--green-light);color:var(--green-dark);padding:2px 8px;border-radius:99px;font-weight:700;}
</style>
</head>
<body>

<div class="topbar">
  <div class="container">
    <span>📍 Jl. Poros Mahakam No. 1, Kec. Muara Kaman, Kab. Kutai Kartanegara, Kaltim &nbsp;|&nbsp; 📞 (0541) 123-456</span>
    <span><a href="#ppid">PPID</a> &nbsp;·&nbsp; <a href="#layanan">Layanan Online</a> &nbsp;·&nbsp; <a href="#" id="adminLoginLink">Masuk Admin</a></span>
  </div>
</div>

<header class="mainnav">
  <div class="container">
    <a href="#beranda" class="brand">
      <div class="crest">K</div>
      <div>
        <div class="name">Desa Kudungga</div>
        <div class="sub">Muara Kaman · Kutai Kartanegara</div>
      </div>
    </a>
    <button class="hamburger" id="hamburgerBtn" aria-label="Buka menu"><div></div><div></div><div></div></button>
    <nav class="tabs" id="navTabs"></nav>
  </div>
</header>

<section class="hero">
  <div class="container">
    <div>
      <span class="eyebrow">Portal Resmi Pemerintah Desa</span>
      <h1>Warisan Kudungga, layanan masa kini.</h1>
      <p class="lead">Informasi desa, transparansi anggaran, dan layanan publik Desa Kudungga di tepian Sungai Mahakam — kini bisa diakses kapan saja, dari mana saja.</p>
      <div class="hero-actions">
        <a class="btn btn-gold" href="#layanan" data-nav="layanan">Ajukan Layanan</a>
        <a class="btn btn-outline" href="#anggaran" data-nav="anggaran">Lihat Transparansi Anggaran</a>
      </div>
    </div>
    <div class="board">
      <span class="eyebrow">Papan Informasi Desa</span>
      <div class="board-title">Kudungga dalam Angka</div>
      <div class="board-stats">
        <div class="board-stat"><div class="num" id="statPenduduk">–</div><div class="lbl">Jiwa</div></div>
        <div class="board-stat"><div class="num" id="statKK">–</div><div class="lbl">Kepala Keluarga</div></div>
        <div class="board-stat"><div class="num">4</div><div class="lbl">Dusun</div></div>
        <div class="board-stat"><div class="num">12,4 km²</div><div class="lbl">Luas Wilayah</div></div>
      </div>
    </div>
  </div>
</section>
<div class="hero-ribbon"><div class="container" id="ribbonText"></div></div>

<main class="container">

<!-- ========== PROFIL DESA ========== -->
<section class="section" id="profil">
  <div class="section-head">
    <span class="eyebrow">Wajib · Profil Desa</span>
    <h2>Sejarah, Visi Misi &amp; Struktur Organisasi</h2>
  </div>

  <div class="grid grid-2" style="margin-bottom:26px;">
    <div class="card">
      <h3>📜 Sejarah Desa</h3>
      <p>Desa Kudungga berdiri di tepian Sungai Mahakam, tanah yang diyakini menjadi cikal bakal peradaban Kutai Martapura — kerajaan bercorak Hindu tertua di Nusantara. Nama desa diambil untuk mengenang Maharaja Kudungga, tokoh yang namanya tercatat dalam prasasti Yupa sebagai leluhur para penguasa Kutai. Warga desa hidup berdampingan dengan sungai sebagai jalur utama perdagangan dan pertanian, menjaga tradisi tenun ulap doyo dan ukiran khas Kutai yang diwariskan turun-temurun hingga kini.</p>
    </div>
    <div class="card">
      <h3>🎯 Visi</h3>
      <p style="font-style:italic;color:var(--green-dark);font-weight:600;">"Terwujudnya Desa Kudungga yang mandiri, sejahtera, dan lestari sebagai penjaga warisan budaya Mahakam pada tahun 2030."</p>
      <h3 style="margin-top:16px;">🧭 Misi</h3>
      <ol style="padding-left:18px;margin:0;">
        <li>Meningkatkan tata kelola pemerintahan desa yang transparan dan akuntabel.</li>
        <li>Mendorong pertumbuhan ekonomi lokal melalui UMKM dan pertanian.</li>
        <li>Meningkatkan kualitas infrastruktur dan pelayanan publik.</li>
        <li>Melestarikan budaya dan lingkungan desa.</li>
      </ol>
    </div>
  </div>

  <div class="card" style="margin-bottom:26px;">
    <h3>🏛️ Struktur Organisasi Pemerintah Desa</h3>
    <div class="orgchart" style="margin-top:18px;">
      <div class="org-box">Kepala Desa<br><span style="font-weight:400;font-size:.78rem;">H. Ardiansyah, S.IP</span></div>
      <div class="org-line"></div>
      <div class="org-box">Sekretaris Desa<br><span style="font-weight:400;font-size:.78rem;">Fitriani Kuntara, S.Sos</span></div>
      <div class="org-line"></div>
      <div class="org-row">
        <div class="org-box">Kaur Keuangan</div>
        <div class="org-box">Kaur Perencanaan</div>
        <div class="org-box">Kaur Tata Usaha &amp; Umum</div>
      </div>
      <div class="org-line"></div>
      <div class="org-row">
        <div class="org-box">Kasi Pemerintahan</div>
        <div class="org-box">Kasi Kesejahteraan</div>
        <div class="org-box">Kasi Pelayanan</div>
      </div>
      <div class="org-line"></div>
      <div class="org-row">
        <div class="org-box">Kepala Dusun I</div>
        <div class="org-box">Kepala Dusun II</div>
        <div class="org-box">Kepala Dusun III</div>
        <div class="org-box">Kepala Dusun IV</div>
      </div>
    </div>
  </div>

  <div class="card">
    <h3>🗺️ Peta Wilayah</h3>
    <p>Peta batas wilayah dusun dan RT/RW dapat dilihat secara interaktif pada bagian <a href="#peta" data-nav="peta" style="color:var(--green);font-weight:700;">Peta Interaktif Desa →</a></p>
  </div>
</section>

<!-- ========== BERITA & PENGUMUMAN ========== -->
<section class="section" id="berita">
  <div class="section-head">
    <span class="eyebrow">Wajib · Berita &amp; Pengumuman</span>
    <h2>Kegiatan, Agenda &amp; Pengumuman Resmi</h2>
  </div>
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:18px;flex-wrap:wrap;gap:10px;">
    <div class="tabgroup" id="beritaFilter">
      <button data-f="semua" class="active">Semua</button>
      <button data-f="berita">Berita</button>
      <button data-f="pengumuman">Pengumuman</button>
    </div>
    <button class="btn btn-green btn-sm admin-only hidden" id="btnTambahBerita">+ Tambah Berita</button>
  </div>
  <div id="beritaForm" class="card hidden" style="margin-bottom:20px;">
    <h3>Tambah Berita / Pengumuman</h3>
    <form class="stack" id="formBerita">
      <div class="field"><label>Judul</label><input type="text" id="beritaJudul" required></div>
      <div class="field"><label>Kategori</label><select id="beritaKategori"><option value="berita">Berita</option><option value="pengumuman">Pengumuman</option></select></div>
      <div class="field"><label>Isi</label><textarea id="beritaIsi" required></textarea></div>
      <div style="display:flex;gap:10px;"><button class="btn btn-green btn-sm" type="submit">Publikasikan</button><button class="btn btn-outline btn-sm" type="button" style="color:var(--ink);border-color:var(--paper-dark);" id="batalBerita">Batal</button></div>
    </form>
  </div>
  <div class="grid grid-3" id="beritaList"></div>
</section>

<!-- ========== TRANSPARANSI ANGGARAN ========== -->
<section class="section" id="anggaran">
  <div class="section-head">
    <span class="eyebrow">Wajib · Transparansi Anggaran</span>
    <h2>Laporan APBDes &amp; Realisasi Anggaran 2026</h2>
  </div>

  <div class="grid grid-4" style="margin-bottom:26px;" id="anggaranStats"></div>

  <div class="grid grid-2" style="margin-bottom:26px;">
    <div class="chart-wrap"><h3 style="font-size:.95rem;">Pendapatan Desa: Anggaran vs Realisasi</h3><canvas id="chartPendapatan" height="220"></canvas></div>
    <div class="chart-wrap"><h3 style="font-size:.95rem;">Belanja per Bidang: Anggaran vs Realisasi</h3><canvas id="chartBelanja" height="220"></canvas></div>
  </div>

  <div class="card" style="margin-bottom:18px;">
    <h3>Rincian Pendapatan Desa</h3>
    <table><thead><tr><th>Sumber Pendapatan</th><th class="num">Anggaran (Rp)</th><th class="num">Realisasi (Rp)</th><th>% Capaian</th></tr></thead><tbody id="tblPendapatan"></tbody></table>
  </div>
  <div class="card">
    <h3>Rincian Belanja per Bidang</h3>
    <table><thead><tr><th>Bidang</th><th class="num">Anggaran (Rp)</th><th class="num">Realisasi (Rp)</th><th>% Capaian</th></tr></thead><tbody id="tblBelanja"></tbody></table>
  </div>
  <p class="form-note" style="margin-top:14px;">Data disajikan sesuai prinsip keterbukaan informasi publik. Unduh dokumen resmi APBDes pada bagian <a href="#ppid" data-nav="ppid" style="color:var(--green);font-weight:700;">PPID</a>.</p>
</section>

<!-- ========== LAYANAN PUBLIK ONLINE ========== -->
<section class="section" id="layanan">
  <div class="section-head">
    <span class="eyebrow">Wajib · Layanan Publik Online</span>
    <h2>Permohonan Surat, Pengaduan &amp; Saran</h2>
  </div>

  <div class="tabgroup" id="layananFilter">
    <button data-f="surat" class="active">Permohonan Surat</button>
    <button data-f="pengaduan">Pengaduan</button>
    <button data-f="saran">Saran &amp; Masukan</button>
  </div>

  <div class="grid grid-2">
    <div class="card">
      <div id="panelSurat">
        <h3>📄 Formulir Permohonan Surat</h3>
        <form class="stack" id="formSurat">
          <div class="field"><label>Nama Lengkap</label><input type="text" required></div>
          <div class="field"><label>NIK</label><input type="text" pattern="[0-9]{16}" maxlength="16" placeholder="16 digit" required></div>
          <div class="field"><label>Jenis Surat</label>
            <select required>
              <option value="">Pilih jenis surat</option>
              <option>Surat Keterangan Domisili</option>
              <option>Surat Keterangan Tidak Mampu (SKTM)</option>
              <option>Surat Pengantar KTP/KK</option>
              <option>Surat Keterangan Usaha</option>
              <option>Surat Keterangan Kelahiran</option>
            </select>
          </div>
          <div class="field"><label>Keperluan</label><textarea placeholder="Jelaskan keperluan surat" required></textarea></div>
          <button class="btn btn-green" type="submit">Ajukan Permohonan</button>
          <div class="status-msg" id="statusSurat"></div>
        </form>
      </div>
      <div id="panelPengaduan" class="hidden">
        <h3>📢 Formulir Pengaduan</h3>
        <form class="stack" id="formPengaduan">
          <div class="field"><label>Nama (boleh anonim)</label><input type="text" placeholder="Anonim jika dikosongkan"></div>
          <div class="field"><label>Kategori Pengaduan</label>
            <select required><option value="">Pilih kategori</option><option>Infrastruktur / Jalan</option><option>Pelayanan Perangkat Desa</option><option>Lingkungan</option><option>Keamanan &amp; Ketertiban</option><option>Lainnya</option></select>
          </div>
          <div class="field"><label>Isi Pengaduan</label><textarea required></textarea></div>
          <button class="btn btn-green" type="submit">Kirim Pengaduan</button>
          <div class="status-msg" id="statusPengaduan"></div>
        </form>
      </div>
      <div id="panelSaran" class="hidden">
        <h3>💡 Formulir Saran &amp; Masukan</h3>
        <form class="stack" id="formSaran">
          <div class="field"><label>Nama</label><input type="text" required></div>
          <div class="field"><label>Saran / Masukan</label><textarea placeholder="Sampaikan ide atau masukan Anda untuk desa" required></textarea></div>
          <button class="btn btn-green" type="submit">Kirim Saran</button>
          <div class="status-msg" id="statusSaran"></div>
        </form>
      </div>
    </div>

    <div class="card">
      <h3>📋 Riwayat Pengajuan Terkini</h3>
      <p class="form-note">Menampilkan status pengajuan yang tersimpan di perangkat/desa ini.</p>
      <div id="riwayatList" style="margin-top:12px;display:flex;flex-direction:column;gap:10px;"></div>
    </div>
  </div>
</section>

<!-- ========== DATA KEPENDUDUKAN ========== -->
<section class="section" id="kependudukan">
  <div class="section-head">
    <span class="eyebrow">Wajib · Data Kependudukan</span>
    <h2>Statistik &amp; Demografi Penduduk</h2>
  </div>
  <div class="grid grid-4" style="margin-bottom:26px;" id="dudukStats"></div>
  <div class="grid grid-2" style="margin-bottom:26px;">
    <div class="chart-wrap"><h3 style="font-size:.95rem;">Jumlah Penduduk per Dusun</h3><canvas id="chartDusun" height="220"></canvas></div>
    <div class="chart-wrap"><h3 style="font-size:.95rem;">Kelompok Usia</h3><canvas id="chartUsia" height="220"></canvas></div>
  </div>
  <div class="grid grid-2">
    <div class="chart-wrap"><h3 style="font-size:.95rem;">Tingkat Pendidikan</h3><canvas id="chartPendidikan" height="220"></canvas></div>
    <div class="chart-wrap"><h3 style="font-size:.95rem;">Mata Pencaharian</h3><canvas id="chartPekerjaan" height="220"></canvas></div>
  </div>
</section>

<!-- ========== GALERI ========== -->
<section class="section" id="galeri">
  <div class="section-head">
    <span class="eyebrow">Penting · Galeri Foto &amp; Video</span>
    <h2>Dokumentasi Kegiatan &amp; Potensi Desa</h2>
    <p>Arsip visual kegiatan pemerintahan, pembangunan, wisata, dan budaya Desa Kudungga.</p>
  </div>
  <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:16px;flex-wrap:wrap;gap:10px;">
    <div class="tabgroup" id="galeriFilter">
      <button data-f="semua" class="active">Semua</button>
      <button data-f="Kegiatan">Kegiatan</button>
      <button data-f="Wisata">Wisata</button>
      <button data-f="Pembangunan">Pembangunan</button>
      <button data-f="Budaya">Budaya</button>
    </div>
    <button class="btn btn-green btn-sm admin-only hidden" id="btnTambahGaleri">+ Tambah Dokumentasi</button>
  </div>
  <div id="galeriForm" class="card hidden" style="margin-bottom:20px;">
    <h3>Tambah Dokumentasi</h3>
    <form class="stack" id="formGaleri">
      <div class="field"><label>Judul</label><input type="text" id="galeriJudul" required></div>
      <div class="field"><label>Kategori</label><select id="galeriKategori"><option>Kegiatan</option><option>Wisata</option><option>Pembangunan</option><option>Budaya</option></select></div>
      <div class="field"><label>Jenis</label><select id="galeriJenis"><option value="📷">Foto</option><option value="🎬">Video</option></select></div>
      <div class="field"><label>Lokasi</label><input type="text" id="galeriLokasi" placeholder="Contoh: Dusun II" required></div>
      <div class="field"><label>Keterangan</label><textarea id="galeriDeskripsi" placeholder="Ceritakan singkat dokumentasi ini" required></textarea></div>
      <div style="display:flex;gap:10px;"><button class="btn btn-green btn-sm" type="submit">Simpan</button><button class="btn btn-outline btn-sm" type="button" style="color:var(--ink);border-color:var(--paper-dark);" id="batalGaleri">Batal</button></div>
      <p class="form-note">Catatan: unggah berkas asli dapat diintegrasikan dengan penyimpanan cloud pada tahap pengembangan lanjutan.</p>
    </form>
  </div>
  <div class="grid grid-3" id="galeriList"></div>
  <p class="form-note" style="margin-top:16px;">Menampilkan <span id="galeriCount" class="mono" style="font-weight:700;color:var(--green-dark);"></span> dokumentasi.</p>
</section>

<!-- ========== PPID ========== -->
<section class="section" id="ppid">
  <div class="section-head">
    <span class="eyebrow">Penting · PPID</span>
    <h2>Akses Dokumen Publik</h2>
    <p>Sesuai UU No. 14 Tahun 2008 tentang Keterbukaan Informasi Publik, dokumen berikut dapat diakses oleh masyarakat umum.</p>
  </div>
  <div class="tabgroup" id="ppidFilter">
    <button data-f="semua" class="active">Semua</button>
    <button data-f="Informasi Berkala">Berkala</button>
    <button data-f="Informasi Serta Merta">Serta Merta</button>
    <button data-f="Informasi Setiap Saat">Setiap Saat</button>
    <button data-f="Informasi Dikecualikan">Dikecualikan</button>
  </div>
  <div id="ppidList"></div>
  <p class="form-note" style="margin-top:16px;">Total <span id="ppidCount" class="mono" style="font-weight:700;color:var(--green-dark);"></span> dokumen terdaftar dalam Daftar Informasi Publik (DIP) Desa Kudungga per <span id="ppidUpdated"></span>.</p>
</section>

<!-- ========== PETA INTERAKTIF ========== -->
<section class="section" id="peta">
  <div class="section-head">
    <span class="eyebrow">Rekomendasi · Peta Interaktif</span>
    <h2>Peta Wilayah &amp; Batas Dusun / RT-RW</h2>
    <p>Klik area pada peta untuk melihat informasi masing-masing dusun.</p>
  </div>
  <div class="map-wrap">
    <svg id="villageMap" viewBox="0 0 500 380" style="border-radius:var(--radius);box-shadow:var(--shadow);background:#F1F6F5;">
      <path class="map-region" data-dusun="0" d="M10,10 L250,10 L250,190 L10,190 Z" fill="#0E3F41"></path>
      <path class="map-region" data-dusun="1" d="M250,10 L490,10 L490,190 L250,190 Z" fill="#146B6E"></path>
      <path class="map-region" data-dusun="2" d="M10,190 L250,190 L250,370 L10,370 Z" fill="#8FB5B3"></path>
      <path class="map-region" data-dusun="3" d="M250,190 L490,190 L490,370 L250,370 Z" fill="#F3E6B8"></path>
      <path d="M0,190 L500,190" stroke="#C9A227" stroke-width="4" stroke-dasharray="2 6"></path>
      <path d="M250,0 L250,380" stroke="#C9A227" stroke-width="4" stroke-dasharray="2 6"></path>
      <path d="M0,90 Q250,150 500,60" stroke="#7FB7D9" stroke-width="6" fill="none" opacity=".7"></path>
      <text x="130" y="105" text-anchor="middle" font-family="Fraunces,serif" font-weight="700" fill="#FFFFFF">Dusun I</text>
      <text x="370" y="105" text-anchor="middle" font-family="Fraunces,serif" font-weight="700" fill="#FFFFFF">Dusun II</text>
      <text x="130" y="285" text-anchor="middle" font-family="Fraunces,serif" font-weight="700" fill="#0B2C2D">Dusun III</text>
      <text x="370" y="285" text-anchor="middle" font-family="Fraunces,serif" font-weight="700" fill="#0B2C2D">Dusun IV</text>
    </svg>
    <div class="map-info" id="mapInfo">
      <span class="eyebrow">Info Wilayah</span>
      <p>Klik salah satu area pada peta untuk menampilkan informasi dusun, meliputi kepala dusun, jumlah RT/RW, dan jumlah penduduk.</p>
    </div>
  </div>
</section>

<!-- ========== UMKM ========== -->
<section class="section" id="umkm">
  <div class="section-head">
    <span class="eyebrow">Rekomendasi · Katalog UMKM</span>
    <h2>Produk &amp; Kerajinan Lokal Desa</h2>
  </div>
  <div style="display:flex;justify-content:flex-end;margin-bottom:16px;">
    <button class="btn btn-green btn-sm admin-only hidden" id="btnTambahUmkm">+ Tambah Produk</button>
  </div>
  <div id="umkmForm" class="card hidden" style="margin-bottom:20px;">
    <h3>Tambah Produk UMKM</h3>
    <form class="stack" id="formUmkm">
      <div class="field"><label>Nama Produk</label><input type="text" id="umkmNama" required></div>
      <div class="field"><label>Nama Pemilik</label><input type="text" id="umkmPemilik" required></div>
      <div class="field"><label>Harga (Rp)</label><input type="number" id="umkmHarga" required></div>
      <div class="field"><label>Kontak (WhatsApp)</label><input type="text" id="umkmKontak" placeholder="08xxxxxxxxxx" required></div>
      <div class="field"><label>Deskripsi</label><textarea id="umkmDeskripsi" required></textarea></div>
      <div style="display:flex;gap:10px;"><button class="btn btn-green btn-sm" type="submit">Simpan Produk</button><button class="btn btn-outline btn-sm" type="button" style="color:var(--ink);border-color:var(--paper-dark);" id="batalUmkm">Batal</button></div>
    </form>
  </div>
  <div class="grid grid-4" id="umkmList"></div>
</section>

<!-- ========== MEDIA SOSIAL ========== -->
<section class="section" id="sosial" style="border-bottom:none;">
  <div class="section-head">
    <span class="eyebrow">Rekomendasi · Integrasi Media Sosial</span>
    <h2>Terhubung dengan Kami</h2>
  </div>
  <div class="social-row">
    <a class="social-btn" href="https://facebook.com" target="_blank" rel="noopener"><span class="ic" style="background:#1877F2;">f</span> Facebook Desa Kudungga</a>
    <a class="social-btn" href="https://instagram.com" target="_blank" rel="noopener"><span class="ic" style="background:#D6249F;">ig</span> @desakudungga</a>
    <a class="social-btn" href="https://wa.me/6281234567890" target="_blank" rel="noopener"><span class="ic" style="background:#25D366;">wa</span> WhatsApp Desa</a>
    <a class="social-btn" href="https://youtube.com" target="_blank" rel="noopener"><span class="ic" style="background:#FF0000;">▶</span> YouTube Desa Kudungga</a>
  </div>
</section>

</main>

<footer>
  <div class="container">
    <div>
      <h4>Desa Kudungga</h4>
      <p style="opacity:.85;font-size:.86rem;">Jl. Poros Mahakam No. 1, Kecamatan Muara Kaman, Kabupaten Kutai Kartanegara, Kalimantan Timur 75581</p>
    </div>
    <div>
      <h4>Navigasi</h4>
      <a href="#profil" data-nav="profil">Profil Desa</a>
      <a href="#berita" data-nav="berita">Berita &amp; Pengumuman</a>
      <a href="#anggaran" data-nav="anggaran">Transparansi Anggaran</a>
      <a href="#layanan" data-nav="layanan">Layanan Publik</a>
    </div>
    <div>
      <h4>Informasi</h4>
      <a href="#kependudukan" data-nav="kependudukan">Data Kependudukan</a>
      <a href="#ppid" data-nav="ppid">PPID</a>
      <a href="#peta" data-nav="peta">Peta Interaktif</a>
      <a href="#umkm" data-nav="umkm">Katalog UMKM</a>
    </div>
    <div>
      <h4>Kontak</h4>
      <a href="tel:0541123456">(0541) 123-456</a>
      <a href="mailto:desa.kudungga@kukarkab.go.id">desa.kudungga@kukarkab.go.id</a>
    </div>
  </div>
  <div class="foot-bottom">© 2026 Pemerintah Desa Kudungga. Dibuat untuk mendukung keterbukaan informasi publik.</div>
</footer>

<div class="admin-toggle">
  <div class="admin-panel hidden" id="adminPanel">
    <span>🔓 Mode Admin aktif</span>
    <button class="btn btn-sm" style="background:var(--gold);color:var(--soil);" id="btnLogoutAdmin">Keluar</button>
  </div>
</div>

<script>
/* ============ ICONS ============ */
const ICONS = {
  beranda:'<path d="M3 10l9-7 9 7v9a2 2 0 0 1-2 2h-4v-6H9v6H5a2 2 0 0 1-2-2z" fill="none" stroke="currentColor" stroke-width="1.8"/>',
  profil:'<circle cx="12" cy="8" r="3.2" fill="none" stroke="currentColor" stroke-width="1.8"/><path d="M4 20c1.5-4 5-6 8-6s6.5 2 8 6" fill="none" stroke="currentColor" stroke-width="1.8"/>',
  berita:'<rect x="3" y="5" width="14" height="14" rx="1.5" fill="none" stroke="currentColor" stroke-width="1.8"/><path d="M7 9h6M7 12.5h6M7 16h3" stroke="currentColor" stroke-width="1.6"/><path d="M17 8h4v9a2 2 0 0 1-2 2h-2" fill="none" stroke="currentColor" stroke-width="1.8"/>',
  anggaran:'<path d="M4 20V10M10 20V4M16 20v-7M20.5 20H3.5" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round"/>',
  layanan:'<path d="M6 3h9l4 4v14a1 1 0 0 1-1 1H6a1 1 0 0 1-1-1V4a1 1 0 0 1 1-1z" fill="none" stroke="currentColor" stroke-width="1.8"/><path d="M9 12l2 2 4-4" stroke="currentColor" stroke-width="1.8" fill="none"/>',
  kependudukan:'<circle cx="9" cy="8" r="2.6" fill="none" stroke="currentColor" stroke-width="1.7"/><circle cx="17" cy="9" r="2.1" fill="none" stroke="currentColor" stroke-width="1.7"/><path d="M3 19c1-3.4 3.6-5 6-5s5 1.6 6 5M15.5 19c.6-2.3 2-3.7 3.5-4.3" fill="none" stroke="currentColor" stroke-width="1.7"/>',
  galeri:'<rect x="3" y="4" width="18" height="15" rx="1.5" fill="none" stroke="currentColor" stroke-width="1.8"/><circle cx="8.5" cy="9.5" r="1.6" fill="none" stroke="currentColor" stroke-width="1.6"/><path d="M4 17l5-5 3.5 3.5L16 12l4.5 5" fill="none" stroke="currentColor" stroke-width="1.7"/>',
  ppid:'<path d="M6 3h8l4 4v14a1 1 0 0 1-1 1H6a1 1 0 0 1-1-1V4a1 1 0 0 1 1-1z" fill="none" stroke="currentColor" stroke-width="1.8"/><path d="M9 12h6M9 15.5h6" stroke="currentColor" stroke-width="1.6"/>',
  peta:'<path d="M9 4l-5.5 2v14L9 18l6 2 5.5-2V4L15 6 9 4z" fill="none" stroke="currentColor" stroke-width="1.7" stroke-linejoin="round"/><path d="M9 4v14M15 6v14" stroke="currentColor" stroke-width="1.5"/>',
  umkm:'<path d="M4 8l1-4h14l1 4" fill="none" stroke="currentColor" stroke-width="1.7"/><path d="M4 8h16v10a1 1 0 0 1-1 1H5a1 1 0 0 1-1-1V8z" fill="none" stroke="currentColor" stroke-width="1.7"/><path d="M9 8v2.2a3 3 0 0 0 6 0V8" fill="none" stroke="currentColor" stroke-width="1.6"/>',
  sosial:'<circle cx="6" cy="12" r="2.3" fill="none" stroke="currentColor" stroke-width="1.7"/><circle cx="18" cy="6" r="2.3" fill="none" stroke="currentColor" stroke-width="1.7"/><circle cx="18" cy="18" r="2.3" fill="none" stroke="currentColor" stroke-width="1.7"/><path d="M8.1 11l7.8-4M8.1 13l7.8 4" stroke="currentColor" stroke-width="1.6"/>'
};
const TAB_LABELS = {
  beranda:'Beranda', profil:'Profil Desa', berita:'Berita', anggaran:'Anggaran',
  layanan:'Layanan Publik', kependudukan:'Kependudukan', galeri:'Galeri', ppid:'PPID',
  peta:'Peta', umkm:'UMKM', sosial:'Sosial Media'
};

/* ============ STORAGE HELPERS ============ */
async function loadData(key, def){
  try{
    const r = await window.storage.get(key, true);
    return r ? JSON.parse(r.value) : def;
  }catch(e){ return def; }
}
async function saveData(key, val){
  try{ await window.storage.set(key, JSON.stringify(val), true); }catch(e){ console.error('storage error',e); }
}
async function loadLocal(key, def){
  try{
    const r = await window.storage.get(key, false);
    return r ? JSON.parse(r.value) : def;
  }catch(e){ return def; }
}
async function saveLocal(key, val){
  try{ await window.storage.set(key, JSON.stringify(val), false); }catch(e){ console.error('storage error',e); }
}
function rupiah(n){ return 'Rp ' + Number(n).toLocaleString('id-ID'); }
function uid(){ return Date.now().toString(36) + Math.random().toString(36).slice(2,7); }

/* ============ DEFAULT DATA ============ */
const DEFAULT_BERITA = [
  {id:uid(), kategori:'pengumuman', judul:'Jadwal Musyawarah Desa Penyusunan RKPDes 2027', tanggal:'2026-08-25', isi:'Pemerintah Desa Kudungga mengundang seluruh tokoh masyarakat dan perwakilan warga untuk menghadiri Musyawarah Desa penyusunan RKPDes 2027 pada tanggal 5 September 2026 di Balai Desa.'},
  {id:uid(), kategori:'berita', judul:'Gotong Royong Bersih Sungai Dusun II', tanggal:'2026-08-20', isi:'Warga Dusun II bersama karang taruna melaksanakan kegiatan bersih sungai sebagai bagian dari program peduli lingkungan desa.'},
  {id:uid(), kategori:'pengumuman', judul:'Pembagian Bantuan Langsung Tunai (BLT) Dana Desa', tanggal:'2026-08-15', isi:'Pencairan BLT Dana Desa tahap III akan dilaksanakan mulai 1 September 2026. Warga penerima manfaat dimohon membawa KTP dan KK asli.'},
  {id:uid(), kategori:'berita', judul:'Panen Raya Kopi Dusun IV Capai Hasil Terbaik', tanggal:'2026-08-10', isi:'Kelompok tani Dusun IV mencatat hasil panen kopi terbaik dalam 3 tahun terakhir berkat program pendampingan pertanian desa.'}
];
const DEFAULT_PPID = [
  // --- Informasi Berkala: wajib diumumkan secara rutin ---
  {id:uid(), kategori:'Informasi Berkala', nama:'Profil dan Struktur Organisasi Pemerintah Desa', nomor:'DIP/001/2026', tanggal:'2026-01-10', format:'PDF', ukuran:'1.8 MB'},
  {id:uid(), kategori:'Informasi Berkala', nama:'Rencana Pembangunan Jangka Menengah Desa (RPJMDes) 2025–2030', nomor:'DIP/002/2025', tanggal:'2025-11-20', format:'PDF', ukuran:'4.2 MB'},
  {id:uid(), kategori:'Informasi Berkala', nama:'Rencana Kerja Pemerintah Desa (RKPDes) Tahun 2026', nomor:'DIP/003/2026', tanggal:'2026-01-05', format:'PDF', ukuran:'2.1 MB'},
  {id:uid(), kategori:'Informasi Berkala', nama:'Laporan APBDes Tahun Anggaran 2026', nomor:'DIP/004/2026', tanggal:'2026-01-15', format:'PDF', ukuran:'3.0 MB'},
  {id:uid(), kategori:'Informasi Berkala', nama:'Laporan Realisasi Pelaksanaan APBDes Semester I 2026', nomor:'DIP/005/2026', tanggal:'2026-07-10', format:'PDF', ukuran:'2.6 MB'},
  {id:uid(), kategori:'Informasi Berkala', nama:'Laporan Pertanggungjawaban Realisasi APBDes Tahun 2025', nomor:'DIP/006/2026', tanggal:'2026-02-01', format:'PDF', ukuran:'3.4 MB'},
  {id:uid(), kategori:'Informasi Berkala', nama:'Laporan Penyelenggaraan Pemerintahan Desa (LPPDes) 2025', nomor:'DIP/007/2026', tanggal:'2026-02-15', format:'PDF', ukuran:'5.1 MB'},
  {id:uid(), kategori:'Informasi Berkala', nama:'Daftar Aset dan Inventaris Desa', nomor:'DIP/008/2026', tanggal:'2026-02-20', format:'XLSX', ukuran:'860 KB'},

  // --- Informasi Serta Merta: wajib diumumkan seketika karena menyangkut hajat hidup orang banyak ---
  {id:uid(), kategori:'Informasi Serta Merta', nama:'Pengumuman Status Siaga Bencana Banjir Sungai Mahakam', nomor:'ISM/001/2026', tanggal:'2026-07-02', format:'PDF', ukuran:'640 KB'},
  {id:uid(), kategori:'Informasi Serta Merta', nama:'Peringatan Dini Cuaca Ekstrem BMKG Wilayah Kutai Kartanegara', nomor:'ISM/002/2026', tanggal:'2026-06-18', format:'PDF', ukuran:'420 KB'},
  {id:uid(), kategori:'Informasi Serta Merta', nama:'Informasi Gangguan Darurat Layanan Air Bersih Dusun II', nomor:'ISM/003/2026', tanggal:'2026-05-30', format:'PDF', ukuran:'310 KB'},

  // --- Informasi Setiap Saat: tersedia dan dapat diminta kapan saja oleh masyarakat ---
  {id:uid(), kategori:'Informasi Setiap Saat', nama:'Peraturan Desa (Perdes) tentang RPJMDes 2025–2030', nomor:'PERDES/03/2025', tanggal:'2025-11-20', format:'PDF', ukuran:'1.2 MB'},
  {id:uid(), kategori:'Informasi Setiap Saat', nama:'Peraturan Kepala Desa tentang Susunan Organisasi dan Tata Kerja (SOTK)', nomor:'PERKADES/05/2025', tanggal:'2025-09-12', format:'PDF', ukuran:'980 KB'},
  {id:uid(), kategori:'Informasi Setiap Saat', nama:'Standar Operasional Prosedur (SOP) Pelayanan Administrasi Surat', nomor:'SOP/01/2026', tanggal:'2026-01-08', format:'PDF', ukuran:'540 KB'},
  {id:uid(), kategori:'Informasi Setiap Saat', nama:'Daftar Penerima Bantuan Langsung Tunai (BLT) Dana Desa 2026', nomor:'DIP/009/2026', tanggal:'2026-08-01', format:'XLSX', ukuran:'720 KB'},
  {id:uid(), kategori:'Informasi Setiap Saat', nama:'Risalah Musyawarah Desa (Musdes) Tahun 2026', nomor:'DIP/010/2026', tanggal:'2026-03-14', format:'PDF', ukuran:'1.5 MB'},
  {id:uid(), kategori:'Informasi Setiap Saat', nama:'Data Potensi dan Profil Desa (Prodeskel)', nomor:'DIP/011/2026', tanggal:'2026-01-25', format:'PDF', ukuran:'2.9 MB'},

  // --- Informasi Dikecualikan: tidak dibuka untuk umum, wajib tetap diumumkan kategorinya beserta alasan ---
  {id:uid(), kategori:'Informasi Dikecualikan', nama:'Data Pribadi Warga Penerima Bantuan Sosial (Rincian NIK & Rekening)', nomor:'DIK/001/2026', tanggal:'2026-01-01', alasan:'Melindungi data pribadi warga sesuai UU Pelindungan Data Pribadi.'},
  {id:uid(), kategori:'Informasi Dikecualikan', nama:'Dokumen Internal Proses Lelang Pengadaan yang Masih Berjalan', nomor:'DIK/002/2026', tanggal:'2026-05-10', alasan:'Berpotensi menghambat proses penegakan hukum dan persaingan usaha yang sehat apabila dibuka sebelum proses selesai.'},
  {id:uid(), kategori:'Informasi Dikecualikan', nama:'Catatan Hasil Mediasi Sengketa Tanah Warga', nomor:'DIK/003/2026', tanggal:'2026-04-22', alasan:'Menyangkut privasi pihak yang bersengketa dan proses mediasi yang masih berlangsung.'}
];
const KATEGORI_WARNA = {Kegiatan:'#146B6E', Wisata:'#2C8C86', Pembangunan:'#0E3F41', Budaya:'#C9A227'};
const DEFAULT_GALERI = [
  // --- Kegiatan ---
  {id:uid(), judul:'Gotong Royong Bersih Sungai Mahakam', kategori:'Kegiatan', jenis:'📷', tanggal:'2026-08-20', lokasi:'Tepian Dusun II', deskripsi:'Warga bersama Karang Taruna membersihkan bantaran sungai dari sampah menjelang musim penghujan.'},
  {id:uid(), judul:'Pelatihan Digitalisasi UMKM', kategori:'Kegiatan', jenis:'🎬', tanggal:'2026-07-15', lokasi:'Balai Desa Kudungga', deskripsi:'Pelaku UMKM dibekali cara memasarkan produk secara daring bersama pendamping desa.'},
  {id:uid(), judul:'Sosialisasi Pencegahan Stunting', kategori:'Kegiatan', jenis:'📷', tanggal:'2026-06-10', lokasi:'Posyandu Dusun I', deskripsi:'Kader kesehatan memberikan edukasi gizi seimbang bagi ibu hamil dan balita.'},
  {id:uid(), judul:'Musyawarah Desa Penyusunan RKPDes 2027', kategori:'Kegiatan', jenis:'🎬', tanggal:'2026-08-05', lokasi:'Balai Desa Kudungga', deskripsi:'Perwakilan warga dan BPD merumuskan prioritas pembangunan desa untuk tahun anggaran berikutnya.'},

  // --- Wisata ---
  {id:uid(), judul:'Riam Mahakam, Air Terjun Tersembunyi', kategori:'Wisata', jenis:'📷', tanggal:'2026-05-01', lokasi:'Dusun III', deskripsi:'Destinasi wisata alam andalan desa dengan air terjun bertingkat yang mulai ramai dikunjungi wisatawan.'},
  {id:uid(), judul:'Susur Sungai Mahakam Naik Ketinting', kategori:'Wisata', jenis:'🎬', tanggal:'2026-04-18', lokasi:'Dermaga Desa', deskripsi:'Wisata perahu tradisional menyusuri Sungai Mahakam sambil menikmati pemandangan tepian desa.'},
  {id:uid(), judul:'Hutan Rotan dan Anggrek Hutan Kudungga', kategori:'Wisata', jenis:'📷', tanggal:'2026-02-22', lokasi:'Dusun IV', deskripsi:'Kawasan konservasi warga yang menyimpan aneka anggrek hutan endemik Kalimantan Timur.'},

  // --- Pembangunan ---
  {id:uid(), judul:'Pembangunan Jalan Rabat Beton', kategori:'Pembangunan', jenis:'📷', tanggal:'2026-06-01', lokasi:'Dusun III', deskripsi:'Proyek Dana Desa untuk memperlancar akses warga menuju lahan pertanian dan permukiman.'},
  {id:uid(), judul:'Renovasi Balai Desa dan Aula Serbaguna', kategori:'Pembangunan', jenis:'📷', tanggal:'2026-03-05', lokasi:'Pusat Desa', deskripsi:'Perluasan aula untuk mendukung kegiatan musyawarah dan acara warga yang lebih representatif.'},
  {id:uid(), judul:'Pemasangan Lampu Jalan Tenaga Surya', kategori:'Pembangunan', jenis:'🎬', tanggal:'2026-01-20', lokasi:'Dusun I & II', deskripsi:'Penerangan jalan ramah lingkungan untuk meningkatkan keamanan warga saat malam hari.'},

  // --- Budaya ---
  {id:uid(), judul:'Festival Erau Adat Kudungga', kategori:'Budaya', jenis:'🎬', tanggal:'2026-08-08', lokasi:'Lapangan Desa', deskripsi:'Perayaan tahunan menghormati leluhur Kutai, diisi tari-tarian adat dan ritual mengulur naga.'},
  {id:uid(), judul:'Kirab Budaya Peringatan HUT RI ke-81', kategori:'Budaya', jenis:'📷', tanggal:'2026-08-17', lokasi:'Jalan Poros Desa', deskripsi:'Arak-arakan warga dengan pakaian adat Kutai dan hasil bumi khas desa.'},
  {id:uid(), judul:'Pameran Tenun Ulap Doyo dan Ukiran Kutai', kategori:'Budaya', jenis:'📷', tanggal:'2026-07-01', lokasi:'Balai Desa Kudungga', deskripsi:'Pameran hasil kriya perempuan Kutai berupa tenun ulap doyo dan ukiran kayu bermotif khas.'}
];
const DEFAULT_UMKM = [
  {id:uid(), nama:'Kopi Robusta Kudungga', pemilik:'Bu Yayah', harga:35000, kontak:'081234567801', deskripsi:'Kopi robusta asli hasil kebun Dusun IV, disangrai secara tradisional.', ic:'☕'},
  {id:uid(), nama:'Kerajinan Anyaman Bambu', pemilik:'Pak Dedi', harga:75000, kontak:'081234567802', deskripsi:'Kerajinan tangan anyaman bambu khas desa, cocok untuk dekorasi rumah.', ic:'🧺'},
  {id:uid(), nama:'Keripik Singkong Balado', pemilik:'Ibu Ratna', harga:15000, kontak:'081234567803', deskripsi:'Camilan renyah dengan bumbu balado khas, tanpa pengawet.', ic:'🍟'},
  {id:uid(), nama:'Madu Hutan Asli', pemilik:'Pak Ujang', harga:60000, kontak:'081234567804', deskripsi:'Madu asli dari hutan sekitar desa, dipanen langsung dari sarang lebah liar.', ic:'🍯'}
];
const DEFAULT_ANGGARAN = {
  tahun:2026,
  pendapatan:[
    {sumber:'Dana Desa (APBN)',anggaran:850000000,realisasi:850000000},
    {sumber:'Alokasi Dana Desa (ADD)',anggaran:420000000,realisasi:410000000},
    {sumber:'Bagi Hasil Pajak & Retribusi',anggaran:95000000,realisasi:88000000},
    {sumber:'Pendapatan Asli Desa',anggaran:60000000,realisasi:52000000}
  ],
  belanja:[
    {bidang:'Penyelenggaraan Pemerintahan',anggaran:380000000,realisasi:365000000},
    {bidang:'Pelaksanaan Pembangunan Desa',anggaran:620000000,realisasi:598000000},
    {bidang:'Pembinaan Kemasyarakatan',anggaran:110000000,realisasi:102000000},
    {bidang:'Pemberdayaan Masyarakat',anggaran:180000000,realisasi:170000000},
    {bidang:'Belanja Tak Terduga',anggaran:35000000,realisasi:12000000}
  ]
};
const DEFAULT_DUDUK = {
  total:4523, kk:1320, lakiLaki:2280, perempuan:2243,
  dusun:[{label:'Dusun I',value:1200},{label:'Dusun II',value:980},{label:'Dusun III',value:1450},{label:'Dusun IV',value:893}],
  usia:[{label:'0-14 th',value:1100},{label:'15-64 th',value:2900},{label:'65+ th',value:523}],
  pendidikan:[{label:'SD',value:1500},{label:'SMP',value:1100},{label:'SMA',value:1300},{label:'D3/S1',value:400},{label:'Lainnya',value:223}],
  pekerjaan:[{label:'Petani',value:1800},{label:'Wiraswasta',value:900},{label:'PNS/ASN',value:150},{label:'Buruh',value:700},{label:'Lainnya',value:973}]
};
const DUSUN_INFO = [
  {nama:'Dusun I', kadus:'Pak Warto', rt:6, rw:2, penduduk:1200},
  {nama:'Dusun II', kadus:'Pak Nana', rt:5, rw:2, penduduk:980},
  {nama:'Dusun III', kadus:'Bu Iis', rt:7, rw:3, penduduk:1450},
  {nama:'Dusun IV', kadus:'Pak Ujang', rt:4, rw:2, penduduk:893}
];

let STATE = { berita:[], ppid:[], galeri:[], umkm:[], anggaran:null, duduk:null, riwayat:[], isAdmin:false };

/* ============ NAV BUILD ============ */
function buildNav(){
  const nav = document.getElementById('navTabs');
  nav.innerHTML = Object.keys(TAB_LABELS).map(key=>`
    <button data-nav="${key}"><svg viewBox="0 0 24 24">${ICONS[key]}</svg>${TAB_LABELS[key]}</button>
  `).join('');
}
function setActiveTab(tab){
  document.querySelectorAll('[data-nav]').forEach(el=>{
    if(el.tagName==='BUTTON') el.classList.toggle('active', el.dataset.nav===tab);
  });
  const ribbon = {beranda:'Selamat datang di portal resmi Desa Kudungga', profil:'Mengenal lebih dekat Desa Kudungga', berita:'Informasi terbaru untuk warga', anggaran:'Transparan untuk kepercayaan bersama', layanan:'Layanan publik lebih dekat dan cepat', kependudukan:'Data akurat untuk perencanaan desa', galeri:'Mengabadikan setiap momen desa', ppid:'Keterbukaan informasi publik', peta:'Menjelajah wilayah Desa Kudungga', umkm:'Mendukung ekonomi lokal warga', sosial:'Terhubung lebih dekat dengan warga'};
  document.getElementById('ribbonText').textContent = '📌 ' + (ribbon[tab]||'');
}
document.addEventListener('click', (e)=>{
  const el = e.target.closest('[data-nav]');
  if(el){
    const tab = el.dataset.nav;
    if(tab==='beranda'){ window.scrollTo({top:0,behavior:'smooth'}); setActiveTab(tab); }
    else {
      const target = document.getElementById(tab);
      if(target){ target.scrollIntoView({behavior:'smooth', block:'start'}); setActiveTab(tab); }
    }
    document.getElementById('navTabs').classList.remove('open');
  }
});
document.getElementById('hamburgerBtn').addEventListener('click', ()=>{
  document.getElementById('navTabs').classList.toggle('open');
});

/* Scroll-spy */
const sections = ['profil','berita','anggaran','layanan','kependudukan','galeri','ppid','peta','umkm','sosial'];
const observer = new IntersectionObserver((entries)=>{
  entries.forEach(entry=>{
    if(entry.isIntersecting) setActiveTab(entry.target.id);
  });
},{ rootMargin:'-40% 0px -50% 0px' });
window.addEventListener('load', ()=> sections.forEach(id=>{ const el=document.getElementById(id); if(el) observer.observe(el); }));

/* ============ RENDER: BERITA ============ */
function renderBerita(filter='semua'){
  const list = STATE.berita.filter(b=> filter==='semua' || b.kategori===filter)
    .sort((a,b)=> new Date(b.tanggal)-new Date(a.tanggal));
  document.getElementById('beritaList').innerHTML = list.map(b=>`
    <div class="card">
      <span class="tag tag-${b.kategori}">${b.kategori==='berita'?'Berita':'Pengumuman'}</span>
      <h3>${escapeHtml(b.judul)}</h3>
      <div class="news-date">${formatTanggal(b.tanggal)}</div>
      <p>${escapeHtml(b.isi)}</p>
    </div>
  `).join('') || '<p class="form-note">Belum ada data untuk kategori ini.</p>';
}
function formatTanggal(t){
  try{ return new Date(t).toLocaleDateString('id-ID',{day:'numeric',month:'long',year:'numeric'}); }catch(e){ return t; }
}
function escapeHtml(s){ const d=document.createElement('div'); d.textContent=s; return d.innerHTML; }

document.getElementById('beritaFilter').addEventListener('click', e=>{
  const btn = e.target.closest('button'); if(!btn) return;
  document.querySelectorAll('#beritaFilter button').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  renderBerita(btn.dataset.f);
});
document.getElementById('btnTambahBerita').addEventListener('click', ()=> document.getElementById('beritaForm').classList.toggle('hidden'));
document.getElementById('batalBerita').addEventListener('click', ()=> document.getElementById('beritaForm').classList.add('hidden'));
document.getElementById('formBerita').addEventListener('submit', async e=>{
  e.preventDefault();
  STATE.berita.unshift({
    id:uid(),
    judul:document.getElementById('beritaJudul').value,
    kategori:document.getElementById('beritaKategori').value,
    isi:document.getElementById('beritaIsi').value,
    tanggal:new Date().toISOString().slice(0,10)
  });
  await saveData('berita', STATE.berita);
  renderBerita();
  e.target.reset();
  document.getElementById('beritaForm').classList.add('hidden');
});

/* ============ RENDER: ANGGARAN ============ */
let chartPendapatan, chartBelanja;
function totalOf(arr,key){ return arr.reduce((s,x)=>s+x[key],0); }
function renderAnggaran(){
  const a = STATE.anggaran;
  const totalPendAnggaran = totalOf(a.pendapatan,'anggaran');
  const totalPendRealisasi = totalOf(a.pendapatan,'realisasi');
  const totalBelanjaAnggaran = totalOf(a.belanja,'anggaran');
  const totalBelanjaRealisasi = totalOf(a.belanja,'realisasi');

  document.getElementById('anggaranStats').innerHTML = `
    <div class="stat-card"><div class="num mono">${rupiah(totalPendAnggaran)}</div><div class="lbl">Total Pendapatan (Anggaran)</div></div>
    <div class="stat-card"><div class="num mono">${rupiah(totalPendRealisasi)}</div><div class="lbl">Total Pendapatan (Realisasi)</div></div>
    <div class="stat-card"><div class="num mono">${rupiah(totalBelanjaAnggaran)}</div><div class="lbl">Total Belanja (Anggaran)</div></div>
    <div class="stat-card"><div class="num mono">${rupiah(totalBelanjaRealisasi)}</div><div class="lbl">Total Belanja (Realisasi)</div></div>
  `;

  document.getElementById('tblPendapatan').innerHTML = a.pendapatan.map(p=>`
    <tr><td>${p.sumber}</td><td class="num">${p.anggaran.toLocaleString('id-ID')}</td><td class="num">${p.realisasi.toLocaleString('id-ID')}</td>
    <td><div class="progress-bar"><span style="width:${Math.min(100,(p.realisasi/p.anggaran*100)).toFixed(0)}%"></span></div>${(p.realisasi/p.anggaran*100).toFixed(1)}%</td></tr>
  `).join('') + `<tr class="total"><td>Total</td><td class="num">${totalPendAnggaran.toLocaleString('id-ID')}</td><td class="num">${totalPendRealisasi.toLocaleString('id-ID')}</td><td></td></tr>`;

  document.getElementById('tblBelanja').innerHTML = a.belanja.map(b=>`
    <tr><td>${b.bidang}</td><td class="num">${b.anggaran.toLocaleString('id-ID')}</td><td class="num">${b.realisasi.toLocaleString('id-ID')}</td>
    <td><div class="progress-bar"><span style="width:${Math.min(100,(b.realisasi/b.anggaran*100)).toFixed(0)}%"></span></div>${(b.realisasi/b.anggaran*100).toFixed(1)}%</td></tr>
  `).join('') + `<tr class="total"><td>Total</td><td class="num">${totalBelanjaAnggaran.toLocaleString('id-ID')}</td><td class="num">${totalBelanjaRealisasi.toLocaleString('id-ID')}</td><td></td></tr>`;

  const ctxP = document.getElementById('chartPendapatan');
  if(chartPendapatan) chartPendapatan.destroy();
  chartPendapatan = new Chart(ctxP,{type:'bar',data:{labels:a.pendapatan.map(p=>p.sumber),datasets:[
    {label:'Anggaran',data:a.pendapatan.map(p=>p.anggaran),backgroundColor:'#9FD1CE'},
    {label:'Realisasi',data:a.pendapatan.map(p=>p.realisasi),backgroundColor:'#146B6E'}
  ]},options:chartOpts()});

  const ctxB = document.getElementById('chartBelanja');
  if(chartBelanja) chartBelanja.destroy();
  chartBelanja = new Chart(ctxB,{type:'bar',data:{labels:a.belanja.map(b=>b.bidang),datasets:[
    {label:'Anggaran',data:a.belanja.map(b=>b.anggaran),backgroundColor:'#F3E6B8'},
    {label:'Realisasi',data:a.belanja.map(b=>b.realisasi),backgroundColor:'#C9A227'}
  ]},options:chartOpts()});
}
function chartOpts(){
  return {responsive:true,plugins:{legend:{position:'bottom',labels:{font:{family:"'Plus Jakarta Sans'"}}}},
    scales:{x:{ticks:{font:{size:9}}},y:{ticks:{callback:v=>(v/1000000)+'jt'}}}};
}

/* ============ RENDER: KEPENDUDUKAN ============ */
let chartDusun, chartUsia, chartPendidikan, chartPekerjaan;
function renderDuduk(){
  const d = STATE.duduk;
  document.getElementById('dudukStats').innerHTML = `
    <div class="stat-card"><div class="num">${d.total.toLocaleString('id-ID')}</div><div class="lbl">Total Penduduk</div></div>
    <div class="stat-card"><div class="num">${d.kk.toLocaleString('id-ID')}</div><div class="lbl">Kepala Keluarga</div></div>
    <div class="stat-card"><div class="num">${d.lakiLaki.toLocaleString('id-ID')}</div><div class="lbl">Laki-laki</div></div>
    <div class="stat-card"><div class="num">${d.perempuan.toLocaleString('id-ID')}</div><div class="lbl">Perempuan</div></div>
  `;
  document.getElementById('statPenduduk').textContent = d.total.toLocaleString('id-ID');
  document.getElementById('statKK').textContent = d.kk.toLocaleString('id-ID');

  const palette = ['#146B6E','#2C8C86','#9FD1CE','#0B2C2D','#C9A227','#F3E6B8'];
  const mk = (id,labels,values,type)=>{
    const c = document.getElementById(id);
    return new Chart(c,{type:type,data:{labels,datasets:[{data:values,backgroundColor:palette,borderWidth:type==='doughnut'?2:0}]},
      options:{responsive:true,plugins:{legend:{position: type==='bar'?'none':'bottom',labels:{font:{family:"'Plus Jakarta Sans'"},boxWidth:12}}},scales:type==='bar'?{y:{beginAtZero:true}}:{}}});
  };
  if(chartDusun) chartDusun.destroy();
  if(chartUsia) chartUsia.destroy();
  if(chartPendidikan) chartPendidikan.destroy();
  if(chartPekerjaan) chartPekerjaan.destroy();
  chartDusun = mk('chartDusun', d.dusun.map(x=>x.label), d.dusun.map(x=>x.value),'bar');
  chartUsia = mk('chartUsia', d.usia.map(x=>x.label), d.usia.map(x=>x.value),'doughnut');
  chartPendidikan = mk('chartPendidikan', d.pendidikan.map(x=>x.label), d.pendidikan.map(x=>x.value),'bar');
  chartPekerjaan = mk('chartPekerjaan', d.pekerjaan.map(x=>x.label), d.pekerjaan.map(x=>x.value),'doughnut');
}

/* ============ RENDER: GALERI ============ */
function renderGaleri(filter='semua'){
  const list = STATE.galeri.filter(g=> filter==='semua' || g.kategori===filter)
    .sort((a,b)=> new Date(b.tanggal)-new Date(a.tanggal));
  document.getElementById('galeriList').innerHTML = list.map(g=>`
    <div class="gallery-item">
      <div class="gallery-thumb" style="background:${g.color || KATEGORI_WARNA[g.kategori] || '#146B6E'}">
        <span class="gtag">${g.kategori}</span>${g.jenis}
      </div>
      <div class="gallery-body">
        <h4>${escapeHtml(g.judul)}</h4>
        <span class="gmeta">📍 ${escapeHtml(g.lokasi||'-')} · ${formatTanggal(g.tanggal)}</span>
        <p class="gdesc">${escapeHtml(g.deskripsi||'')}</p>
      </div>
    </div>
  `).join('') || '<p class="form-note">Belum ada dokumentasi untuk kategori ini.</p>';
  document.getElementById('galeriCount').textContent = list.length;
}
document.getElementById('galeriFilter').addEventListener('click', e=>{
  const btn = e.target.closest('button'); if(!btn) return;
  document.querySelectorAll('#galeriFilter button').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  renderGaleri(btn.dataset.f);
});
document.getElementById('btnTambahGaleri').addEventListener('click', ()=> document.getElementById('galeriForm').classList.toggle('hidden'));
document.getElementById('batalGaleri').addEventListener('click', ()=> document.getElementById('galeriForm').classList.add('hidden'));
document.getElementById('formGaleri').addEventListener('submit', async e=>{
  e.preventDefault();
  STATE.galeri.unshift({
    id:uid(), judul:document.getElementById('galeriJudul').value,
    kategori:document.getElementById('galeriKategori').value,
    jenis:document.getElementById('galeriJenis').value,
    lokasi:document.getElementById('galeriLokasi').value,
    deskripsi:document.getElementById('galeriDeskripsi').value,
    tanggal:new Date().toISOString().slice(0,10)
  });
  await saveData('galeri', STATE.galeri);
  document.querySelectorAll('#galeriFilter button').forEach(b=>b.classList.remove('active'));
  document.querySelector('#galeriFilter button[data-f="semua"]').classList.add('active');
  renderGaleri();
  e.target.reset();
  document.getElementById('galeriForm').classList.add('hidden');
});

/* ============ RENDER: PPID ============ */
const KATEGORI_TAG = {
  'Informasi Berkala':'#DCEFEC','Informasi Serta Merta':'#F3E6B8',
  'Informasi Setiap Saat':'#EAF0EF','Informasi Dikecualikan':'#F4D9D0'
};
function renderPpid(filter='semua'){
  const list = STATE.ppid.filter(p=> filter==='semua' || p.kategori===filter)
    .sort((a,b)=> new Date(b.tanggal)-new Date(a.tanggal));
  document.getElementById('ppidList').innerHTML = list.map(p=>{
    const dikecualikan = p.kategori === 'Informasi Dikecualikan';
    const badgeBg = KATEGORI_TAG[p.kategori] || '#EAF0EF';
    if(dikecualikan){
      return `
      <div class="doc-row" style="align-items:flex-start;">
        <div class="doc-icon" style="background:${badgeBg};">🔒</div>
        <div class="doc-meta">
          <h4>${escapeHtml(p.nama)}</h4>
          <span>${p.kategori} · No. ${p.nomor||'-'} · ${formatTanggal(p.tanggal)}</span>
          <p style="margin:6px 0 0;font-size:.8rem;color:var(--ink-soft);"><strong>Alasan pengecualian:</strong> ${escapeHtml(p.alasan||'-')}</p>
        </div>
      </div>`;
    }
    return `
      <div class="doc-row">
        <div class="doc-icon" style="background:${badgeBg};">📄</div>
        <div class="doc-meta">
          <h4>${escapeHtml(p.nama)}</h4>
          <span>${p.kategori} · No. ${p.nomor||'-'} · ${formatTanggal(p.tanggal)} · ${p.format||'PDF'} · ${p.ukuran||'-'}</span>
        </div>
        <button class="btn btn-outline btn-sm" style="color:var(--green-dark);border-color:var(--green);" onclick="alert('Simulasi unduh dokumen: ${escapeHtml(p.nama)}\\n\\nPada implementasi produksi, tautan ini terhubung ke berkas ${p.format||'PDF'} resmi.')">Unduh</button>
      </div>`;
  }).join('') || '<p class="form-note">Tidak ada dokumen pada kategori ini.</p>';
  document.getElementById('ppidCount').textContent = STATE.ppid.length;
  document.getElementById('ppidUpdated').textContent = formatTanggal(new Date().toISOString().slice(0,10));
}
document.getElementById('ppidFilter').addEventListener('click', e=>{
  const btn = e.target.closest('button'); if(!btn) return;
  document.querySelectorAll('#ppidFilter button').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  renderPpid(btn.dataset.f);
});

/* ============ RENDER: UMKM ============ */
const UMKM_ICONS = ['🛍️','🧺','🍯','☕','🍟','🌾','🧵','🥭'];
function renderUmkm(){
  document.getElementById('umkmList').innerHTML = STATE.umkm.map(u=>`
    <div class="umkm-card">
      <div class="umkm-thumb" style="background:var(--paper-dark);">${u.ic||'🛍️'}</div>
      <div class="umkm-body">
        <h4 style="font-family:'Fraunces',serif;font-size:1rem;margin:0;">${escapeHtml(u.nama)}</h4>
        <div class="umkm-price">${rupiah(u.harga)}</div>
        <p style="font-size:.82rem;margin:0;color:var(--ink-soft);">${escapeHtml(u.deskripsi)}</p>
        <div class="umkm-owner">Oleh: ${escapeHtml(u.pemilik)}</div>
        <a class="btn btn-green btn-sm" style="margin-top:6px;" href="https://wa.me/62${u.kontak.replace(/^0/,'')}" target="_blank" rel="noopener">Hubungi via WhatsApp</a>
      </div>
    </div>
  `).join('');
}
document.getElementById('btnTambahUmkm').addEventListener('click', ()=> document.getElementById('umkmForm').classList.toggle('hidden'));
document.getElementById('batalUmkm').addEventListener('click', ()=> document.getElementById('umkmForm').classList.add('hidden'));
document.getElementById('formUmkm').addEventListener('submit', async e=>{
  e.preventDefault();
  STATE.umkm.unshift({
    id:uid(), nama:document.getElementById('umkmNama').value,
    pemilik:document.getElementById('umkmPemilik').value,
    harga:Number(document.getElementById('umkmHarga').value),
    kontak:document.getElementById('umkmKontak').value,
    deskripsi:document.getElementById('umkmDeskripsi').value,
    ic:UMKM_ICONS[Math.floor(Math.random()*UMKM_ICONS.length)]
  });
  await saveData('umkm', STATE.umkm);
  renderUmkm();
  e.target.reset();
  document.getElementById('umkmForm').classList.add('hidden');
});

/* ============ PETA INTERAKTIF ============ */
document.querySelectorAll('.map-region').forEach(region=>{
  region.addEventListener('click', ()=>{
    document.querySelectorAll('.map-region').forEach(r=>r.classList.remove('selected'));
    region.classList.add('selected');
    const info = DUSUN_INFO[Number(region.dataset.dusun)];
    document.getElementById('mapInfo').innerHTML = `
      <span class="eyebrow">Info Wilayah</span>
      <h3>${info.nama}</h3>
      <p><strong>Kepala Dusun:</strong> ${info.kadus}</p>
      <p><strong>Jumlah RT / RW:</strong> ${info.rt} RT / ${info.rw} RW</p>
      <p><strong>Jumlah Penduduk:</strong> ${info.penduduk.toLocaleString('id-ID')} jiwa</p>
    `;
  });
});

/* ============ LAYANAN PUBLIK ============ */
document.getElementById('layananFilter').addEventListener('click', e=>{
  const btn = e.target.closest('button'); if(!btn) return;
  document.querySelectorAll('#layananFilter button').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  ['Surat','Pengaduan','Saran'].forEach(p=> document.getElementById('panel'+p).classList.add('hidden'));
  const map = {surat:'Surat', pengaduan:'Pengaduan', saran:'Saran'};
  document.getElementById('panel'+map[btn.dataset.f]).classList.remove('hidden');
});

async function submitLayanan(jenis, ringkasan){
  const item = {id:uid(), jenis, ringkasan, tanggal:new Date().toISOString(), status:'Diajukan'};
  STATE.riwayat.unshift(item);
  await saveLocal('riwayat-layanan', STATE.riwayat);
  renderRiwayat();
}
function renderRiwayat(){
  const badge = {Diajukan:'badge-req', Diproses:'badge-proses', Selesai:'badge-selesai'};
  document.getElementById('riwayatList').innerHTML = STATE.riwayat.slice(0,8).map(r=>`
    <div style="border:1px solid var(--paper-dark);border-radius:10px;padding:12px;">
      <div style="display:flex;justify-content:space-between;gap:8px;">
        <strong style="font-size:.85rem;">${r.jenis}</strong>
        <span class="${badge[r.status]||'badge-req'}">${r.status}</span>
      </div>
      <p style="margin:6px 0 0;font-size:.8rem;color:var(--ink-soft);">${escapeHtml(r.ringkasan)}</p>
      <div class="news-date" style="margin-top:4px;">${formatTanggal(r.tanggal)}</div>
    </div>
  `).join('') || '<p class="form-note">Belum ada pengajuan.</p>';
}
function showStatus(id, ok, msg){
  const el = document.getElementById(id);
  el.className = 'status-msg ' + (ok?'ok':'err');
  el.textContent = msg;
  setTimeout(()=> el.className='status-msg', 4000);
}
document.getElementById('formSurat').addEventListener('submit', async e=>{
  e.preventDefault();
  const jenis = e.target.querySelector('select').value;
  await submitLayanan('Permohonan Surat: '+jenis, jenis);
  showStatus('statusSurat', true, 'Permohonan berhasil diajukan. Silakan pantau status pada bagian Riwayat Pengajuan.');
  e.target.reset();
});
document.getElementById('formPengaduan').addEventListener('submit', async e=>{
  e.preventDefault();
  const kategori = e.target.querySelector('select').value;
  await submitLayanan('Pengaduan: '+kategori, kategori);
  showStatus('statusPengaduan', true, 'Pengaduan berhasil dikirim. Tim desa akan menindaklanjuti secepatnya.');
  e.target.reset();
});
document.getElementById('formSaran').addEventListener('submit', async e=>{
  e.preventDefault();
  await submitLayanan('Saran & Masukan', 'Saran telah dikirim, terima kasih atas partisipasi Anda.');
  showStatus('statusSaran', true, 'Terima kasih, saran Anda telah kami terima.');
  e.target.reset();
});

/* ============ ADMIN MODE ============ */
document.getElementById('adminLoginLink').addEventListener('click', (e)=>{
  e.preventDefault();
  if(STATE.isAdmin){ return; }
  const pass = prompt('Masukkan kata sandi admin (demo: admin123):');
  if(pass === 'admin123'){
    STATE.isAdmin = true;
    document.querySelectorAll('.admin-only').forEach(el=>el.classList.remove('hidden'));
    document.getElementById('adminPanel').classList.remove('hidden');
  } else if(pass !== null){
    alert('Kata sandi salah.');
  }
});
document.getElementById('btnLogoutAdmin').addEventListener('click', ()=>{
  STATE.isAdmin = false;
  document.querySelectorAll('.admin-only').forEach(el=>el.classList.add('hidden'));
  document.getElementById('adminPanel').classList.add('hidden');
});

/* ============ INIT ============ */
async function init(){
  buildNav();
  STATE.berita = await loadData('berita', DEFAULT_BERITA);
  STATE.ppid = await loadData('ppid', DEFAULT_PPID);
  STATE.galeri = await loadData('galeri', DEFAULT_GALERI);
  STATE.umkm = await loadData('umkm', DEFAULT_UMKM);
  STATE.anggaran = await loadData('anggaran', DEFAULT_ANGGARAN);
  STATE.duduk = await loadData('kependudukan', DEFAULT_DUDUK);
  STATE.riwayat = await loadLocal('riwayat-layanan', []);

  renderBerita();
  renderAnggaran();
  renderDuduk();
  renderGaleri();
  renderPpid();
  renderUmkm();
  renderRiwayat();
  setActiveTab('beranda');
}
init();
</script>
</body>
</html>
