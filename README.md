<!DOCTYPE html>
<html lang="hi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="theme-color" content="#1a3a6e">
<title>Prince Soni CSC Centre</title>
<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@400;500;600;700;800&family=JetBrains+Mono:wght@500;700&display=swap" rel="stylesheet">
<style>
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
:root{
  --p:#1a3a6e;--pl:#2356b8;--pd:#0f2247;
  --acc:#f59e0b;--ok:#10b981;--err:#ef4444;--warn:#f59e0b;--pur:#8b5cf6;
  --bg:#eef2ff;--card:#fff;--sid:#0f2247;--sida:rgba(255,255,255,0.08);
  --txt:#1e293b;--muted:#64748b;--bdr:#e2e8f0;
  --sh:0 2px 12px rgba(26,58,110,.10);--shl:0 6px 30px rgba(26,58,110,.16);
  --r:14px;--rs:8px;
  --font:'Baloo 2',sans-serif;
}
html,body{height:100%;overflow-x:hidden;font-family:var(--font);background:var(--bg);color:var(--txt)}
@keyframes fadeUp{from{opacity:0;transform:translateY(16px)}to{opacity:1;transform:translateY(0)}}
@keyframes popIn{0%{transform:scale(.85);opacity:0}60%{transform:scale(1.04)}100%{transform:scale(1);opacity:1}}
@keyframes shake{0%,100%{transform:translateX(0)}25%{transform:translateX(-7px)}75%{transform:translateX(7px)}}
.shake{animation:shake .4s ease !important;}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-5px)}}
@keyframes spin{to{transform:rotate(360deg)}}

/* ══════════════════ LOGIN ══════════════════ */
#loginPage{
  min-height:100vh;display:flex;align-items:center;justify-content:center;
  background:linear-gradient(145deg,#0f2247 0%,#1a3a6e 50%,#2356b8 100%);
  padding:16px;position:relative;overflow:hidden;
}
#loginPage::before{content:'';position:absolute;width:500px;height:500px;border-radius:50%;background:rgba(255,255,255,.04);top:-200px;right:-150px}
#loginPage::after{content:'';position:absolute;width:350px;height:350px;border-radius:50%;background:rgba(255,255,255,.03);bottom:-100px;left:-100px}
.login-box{background:#fff;border-radius:24px;padding:clamp(24px,5vw,48px) clamp(20px,5vw,44px);width:100%;max-width:420px;box-shadow:0 24px 80px rgba(0,0,0,.3);animation:popIn .5s ease;position:relative;z-index:1}
.login-logo{text-align:center;margin-bottom:24px}
.login-icon{width:68px;height:68px;background:linear-gradient(135deg,var(--p),var(--pl));border-radius:18px;display:inline-flex;align-items:center;justify-content:center;font-size:30px;margin-bottom:10px;animation:float 3s ease-in-out infinite;box-shadow:0 8px 24px rgba(26,58,110,.35)}
.login-logo h1{font-size:clamp(16px,4vw,20px);font-weight:800;color:var(--pd);line-height:1.2}
.login-logo p{font-size:13px;color:var(--muted);margin-top:3px}
.type-tabs{display:flex;background:var(--bg);border-radius:10px;padding:4px;margin-bottom:20px}
.type-tab{flex:1;padding:8px;border:none;border-radius:7px;font-family:var(--font);font-size:14px;font-weight:700;cursor:pointer;transition:all .25s;color:var(--muted);background:transparent}
.type-tab.on{background:#fff;color:var(--p);box-shadow:0 2px 8px rgba(26,58,110,.15)}
.f-group{margin-bottom:16px}
.f-label{display:block;font-size:11px;font-weight:700;color:var(--muted);text-transform:uppercase;letter-spacing:.6px;margin-bottom:6px}
.f-input{width:100%;padding:12px 14px;border:2px solid var(--bdr);border-radius:10px;font-family:var(--font);font-size:15px;color:var(--txt);outline:none;transition:border-color .2s;background:#fff}
.f-input:focus{border-color:var(--pl)}
.f-select{width:100%;padding:11px 14px;border:2px solid var(--bdr);border-radius:10px;font-family:var(--font);font-size:14px;color:var(--txt);outline:none;transition:border-color .2s;background:#fff;cursor:pointer}
.f-select:focus{border-color:var(--pl)}
.f-textarea{width:100%;padding:11px 14px;border:2px solid var(--bdr);border-radius:10px;font-family:var(--font);font-size:14px;color:var(--txt);outline:none;resize:vertical;min-height:80px;transition:border-color .2s}
.f-textarea:focus{border-color:var(--pl)}
.btn-login{width:100%;padding:14px;background:linear-gradient(135deg,var(--p),var(--pl));color:#fff;border:none;border-radius:12px;font-family:var(--font);font-size:16px;font-weight:800;cursor:pointer;box-shadow:0 6px 20px rgba(26,58,110,.35);transition:all .25s;margin-top:4px}
.btn-login:hover{transform:translateY(-2px);box-shadow:0 10px 28px rgba(26,58,110,.45)}
.btn-link{background:none;border:none;color:var(--pl);font-family:var(--font);font-size:14px;font-weight:600;cursor:pointer;text-decoration:underline}
.err-msg{background:#fef2f2;color:var(--err);border:1px solid #fecaca;border-radius:8px;padding:10px 14px;font-size:13px;margin-bottom:14px;display:none}

/* ══════════════════ APP SHELL ══════════════════ */
#app{display:none;height:100vh;overflow:hidden}
.app-layout{display:flex;height:100vh}

/* ══════════════════ SIDEBAR ══════════════════ */
.sidebar{
  width:250px;flex-shrink:0;background:var(--sid);
  display:flex;flex-direction:column;
  overflow-y:auto;overflow-x:hidden;
  transition:transform .3s cubic-bezier(.4,0,.2,1);
  z-index:100;
}
.s-logo{padding:20px 16px;border-bottom:1px solid rgba(255,255,255,.07);display:flex;align-items:center;gap:11px}
.s-logo-icon{width:42px;height:42px;background:linear-gradient(135deg,var(--acc),#f97316);border-radius:11px;display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0}
.s-logo-text h2{color:#fff;font-size:13px;font-weight:800;line-height:1.3}
.s-logo-text p{color:rgba(255,255,255,.45);font-size:10px;margin-top:1px}
.s-nav{flex:1;padding:12px 10px}
.s-sec{color:rgba(255,255,255,.3);font-size:9px;font-weight:800;text-transform:uppercase;letter-spacing:1.5px;padding:12px 8px 5px}
.s-item{display:flex;align-items:center;gap:10px;padding:10px 12px;border-radius:10px;color:rgba(255,255,255,.65);font-size:13px;font-weight:600;cursor:pointer;transition:all .2s;margin-bottom:1px;border:none;background:transparent;width:100%;text-align:left;font-family:var(--font)}
.s-item:hover{background:rgba(255,255,255,.07);color:#fff}
.s-item.on{background:var(--pl);color:#fff;box-shadow:0 3px 12px rgba(35,86,184,.4)}
.s-item .ico{font-size:17px;flex-shrink:0}
.s-badge{margin-left:auto;background:var(--err);color:#fff;font-size:10px;font-weight:800;padding:2px 6px;border-radius:20px;min-width:20px;text-align:center}
.s-foot{padding:14px 12px;border-top:1px solid rgba(255,255,255,.07)}
.s-user{display:flex;align-items:center;gap:10px;background:rgba(255,255,255,.06);border-radius:11px;padding:10px}
.s-avatar{width:36px;height:36px;background:linear-gradient(135deg,var(--acc),var(--pl));border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:15px;font-weight:800;color:#fff;flex-shrink:0}
.s-user-info h4{color:#fff;font-size:12px;font-weight:700}
.s-user-info p{color:rgba(255,255,255,.45);font-size:10px}
.s-btn{width:100%;margin-top:8px;padding:9px;border-radius:9px;font-family:var(--font);font-size:12px;font-weight:700;cursor:pointer;transition:all .2s;display:flex;align-items:center;justify-content:center;gap:7px;border:1px solid}
.s-btn-pass{background:rgba(255,255,255,.07);border-color:rgba(255,255,255,.13);color:rgba(255,255,255,.75)}
.s-btn-pass:hover{background:rgba(255,255,255,.14)}
.s-btn-out{background:rgba(239,68,68,.12);border-color:rgba(239,68,68,.25);color:#fca5a5;margin-top:6px}
.s-btn-out:hover{background:rgba(239,68,68,.25)}

/* ══════════════════ MAIN CONTENT ══════════════════ */
.main{flex:1;display:flex;flex-direction:column;min-width:0;overflow:hidden}
.topbar{background:#fff;padding:0 clamp(12px,3vw,24px);height:58px;display:flex;align-items:center;justify-content:space-between;border-bottom:1px solid var(--bdr);flex-shrink:0;box-shadow:0 2px 8px rgba(0,0,0,.05)}
.tb-left{display:flex;align-items:center;gap:10px}
.tb-title{font-size:clamp(14px,2.5vw,18px);font-weight:800;color:var(--txt);white-space:nowrap}
.tb-right{display:flex;align-items:center;gap:10px}
.tb-search{display:flex;align-items:center;background:var(--bg);border:2px solid transparent;border-radius:10px;padding:7px 12px;gap:7px;transition:border-color .2s}
.tb-search:focus-within{border-color:var(--pl);background:#fff}
.tb-search input{border:none;background:transparent;font-family:var(--font);font-size:13px;color:var(--txt);outline:none;width:clamp(80px,12vw,180px)}
.tb-clock{font-family:'JetBrains Mono',monospace;font-size:clamp(12px,2vw,15px);font-weight:700;color:var(--p);background:var(--bg);padding:6px 10px;border-radius:8px;white-space:nowrap}
.tb-notif{width:36px;height:36px;background:var(--bg);border:none;border-radius:9px;cursor:pointer;font-size:18px;display:flex;align-items:center;justify-content:center;position:relative;transition:background .2s}
.tb-notif:hover{background:var(--bdr)}
.notif-dot{position:absolute;top:5px;right:5px;width:8px;height:8px;background:var(--err);border-radius:50%;border:2px solid #fff}
.ham{width:36px;height:36px;background:var(--bg);border:none;border-radius:9px;cursor:pointer;font-size:20px;display:none;align-items:center;justify-content:center}
.page-wrap{flex:1;overflow-y:auto;overflow-x:hidden;padding:clamp(12px,3vw,24px);padding-bottom:clamp(16px,4vw,24px)}

/* ══════════════════ PAGES ══════════════════ */
.page{display:none;animation:fadeUp .35s ease}
.page.on{display:block}

/* ══════════════════ DASHBOARD ══════════════════ */
.welcome{background:linear-gradient(135deg,var(--pd),var(--p),var(--pl));border-radius:var(--r);padding:clamp(16px,4vw,28px) clamp(16px,4vw,28px);color:#fff;margin-bottom:clamp(12px,3vw,20px);position:relative;overflow:hidden}
.welcome::after{content:'🏛️';position:absolute;right:clamp(10px,3vw,24px);top:50%;transform:translateY(-50%);font-size:clamp(36px,8vw,64px);opacity:.18}
.welcome h2{font-size:clamp(15px,3.5vw,22px);font-weight:800;margin-bottom:5px}
.welcome p{font-size:clamp(11px,2.5vw,14px);opacity:.85}
.welcome-date{font-size:clamp(10px,2vw,13px);opacity:.65;margin-top:8px}
.stats{display:grid;grid-template-columns:repeat(auto-fill,minmax(clamp(130px,22vw,180px),1fr));gap:clamp(8px,2vw,16px);margin-bottom:clamp(12px,3vw,20px)}
.stat{background:#fff;border-radius:var(--r);padding:clamp(14px,3vw,22px) clamp(12px,2.5vw,20px);box-shadow:var(--sh);border-left:4px solid;cursor:default;transition:transform .2s,box-shadow .2s}
.stat:hover{transform:translateY(-2px);box-shadow:var(--shl)}
.stat.c1{border-color:var(--p)}.stat.c2{border-color:var(--ok)}.stat.c3{border-color:var(--warn)}
.stat.c4{border-color:var(--err)}.stat.c5{border-color:var(--pur)}.stat.c6{border-color:#14b8a6}
.stat-ico{font-size:clamp(20px,4vw,26px);margin-bottom:8px}
.stat-val{font-size:clamp(20px,5vw,28px);font-weight:800}
.stat-lbl{font-size:clamp(10px,2vw,13px);color:var(--muted);margin-top:3px;font-weight:500}
.dash-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(clamp(240px,40vw,420px),1fr));gap:clamp(10px,2.5vw,18px)}
.card{background:#fff;border-radius:var(--r);padding:clamp(14px,3vw,22px);box-shadow:var(--sh)}
.card-ttl{font-size:clamp(13px,2.5vw,16px);font-weight:800;margin-bottom:14px;display:flex;align-items:center;gap:7px}
.bars{display:flex;align-items:flex-end;gap:clamp(4px,1.5vw,8px);height:clamp(60px,12vw,100px);margin-top:10px}
.bar{flex:1;background:linear-gradient(to top,var(--p),var(--pl));border-radius:5px 5px 0 0;transition:opacity .2s;cursor:pointer}
.bar:hover{opacity:.75}
.bar-lbls{display:flex;gap:clamp(4px,1.5vw,8px);margin-top:4px}
.bar-lbl{flex:1;text-align:center;font-size:clamp(8px,1.5vw,10px);color:var(--muted)}
.act-item{display:flex;align-items:flex-start;gap:10px;padding:10px 0;border-bottom:1px solid var(--bdr)}
.act-item:last-child{border-bottom:none}
.act-dot{width:9px;height:9px;border-radius:50%;flex-shrink:0;margin-top:5px}
.act-txt{font-size:clamp(11px,2vw,13px);flex:1}
.act-time{font-size:clamp(10px,1.8vw,11px);color:var(--muted);white-space:nowrap}
.rem-item{display:flex;align-items:center;gap:10px;padding:10px;background:#fffbeb;border-radius:10px;border:1px solid #fde68a;margin-bottom:8px}
.rem-info{flex:1}
.rem-name{font-size:clamp(12px,2vw,14px);font-weight:700}
.rem-amt{font-size:clamp(11px,1.8vw,12px);color:var(--muted)}

/* ══════════════════ BUTTONS ══════════════════ */
.btn{padding:clamp(9px,2vw,12px) clamp(14px,3vw,22px);border-radius:10px;font-family:var(--font);font-size:clamp(12px,2vw,14px);font-weight:700;cursor:pointer;border:none;transition:all .2s;display:inline-flex;align-items:center;gap:7px;white-space:nowrap}
.btn-p{background:linear-gradient(135deg,var(--p),var(--pl));color:#fff;box-shadow:0 4px 14px rgba(26,58,110,.3)}
.btn-p:hover{transform:translateY(-1px);box-shadow:0 7px 20px rgba(26,58,110,.4)}
.btn-ok{background:var(--ok);color:#fff}
.btn-err{background:var(--err);color:#fff}
.btn-warn{background:var(--warn);color:#fff}
.btn-sec{background:var(--bg);color:var(--txt);border:2px solid var(--bdr)}
.bsm{padding:clamp(4px,1vw,5px) clamp(7px,1.5vw,10px);border-radius:7px;font-size:clamp(10px,1.8vw,12px);font-weight:700;cursor:pointer;border:none;font-family:var(--font);transition:all .2s;display:inline-flex;align-items:center;gap:4px}
.bsm:hover{opacity:.82;transform:scale(1.04)}
.bsm-p{background:var(--p);color:#fff}.bsm-ok{background:var(--ok);color:#fff}
.bsm-err{background:var(--err);color:#fff}.bsm-warn{background:var(--warn);color:#fff}
.bsm-sec{background:var(--bg);color:var(--txt);border:1px solid var(--bdr)}

/* ══════════════════ FORMS ══════════════════ */
.form-wrap{background:#fff;border-radius:var(--r);padding:clamp(16px,4vw,28px);box-shadow:var(--sh)}
.form-ttl{font-size:clamp(15px,3vw,18px);font-weight:800;margin-bottom:20px;padding-bottom:14px;border-bottom:2px solid var(--bg);display:flex;align-items:center;gap:9px}
.fg{margin-bottom:14px}
.fg-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(clamp(140px,30vw,220px),1fr));gap:14px}
.fg-grid.full{grid-template-columns:1fr}
.pay-toggle{display:flex;gap:10px}
.pay-opt{flex:1;padding:10px;border:2px solid var(--bdr);border-radius:10px;text-align:center;cursor:pointer;font-weight:700;font-size:clamp(12px,2.5vw,14px);transition:all .2s}
.pay-opt.ok{border-color:var(--ok);background:#d1fae5;color:#065f46}
.pay-opt.pend{border-color:var(--warn);background:#fef3c7;color:#92400e}
.f-actions{margin-top:18px;display:flex;gap:10px;flex-wrap:wrap}

/* ══════════════════ MULTI-SELECT SERVICE ══════════════════ */
.ms-box{min-height:44px;border:2px solid var(--bdr);border-radius:10px;padding:6px 10px;cursor:pointer;display:flex;flex-wrap:wrap;gap:5px;align-items:center;background:#fff;transition:border-color .2s}
.ms-box:focus-within,.ms-box.open{border-color:var(--pl)}
.ms-ph{color:#94a3b8;font-size:14px}
.ms-tag{background:var(--p);color:#fff;padding:3px 9px;border-radius:20px;font-size:clamp(10px,2vw,12px);font-weight:600;display:inline-flex;align-items:center;gap:4px;cursor:pointer}
.ms-panel{display:none;border:2px solid var(--pl);border-radius:12px;margin-top:5px;background:#fff;box-shadow:0 8px 28px rgba(26,58,110,.14);position:relative;z-index:50}
.ms-panel.open{display:block}
.ms-search{display:flex;align-items:center;gap:7px;padding:9px 12px;border-bottom:1px solid var(--bdr)}
.ms-search input{border:none;outline:none;font-family:var(--font);font-size:14px;width:100%;background:transparent}
.ms-list{max-height:clamp(160px,30vh,220px);overflow-y:auto;padding:5px}
.ms-opt{display:flex;align-items:center;gap:9px;padding:8px 10px;border-radius:8px;cursor:pointer;font-size:clamp(12px,2vw,14px);transition:background .15s}
.ms-opt:hover{background:#f0f4ff}
.ms-opt.sel{background:#eff6ff}
.ms-chk{width:18px;height:18px;border-radius:5px;border:2px solid var(--bdr);background:#fff;display:flex;align-items:center;justify-content:center;flex-shrink:0;transition:all .15s;font-size:11px;font-weight:900}
.ms-chk.on{background:var(--p);border-color:var(--p);color:#fff}
.ms-foot{padding:8px 12px;border-top:1px solid var(--bdr);display:flex;justify-content:space-between;align-items:center}
.ms-cnt{font-size:12px;color:var(--muted)}

/* ══════════════════ FILTER BAR ══════════════════ */
.filter-bar{display:flex;gap:8px;flex-wrap:wrap;align-items:center;margin-bottom:16px}
.fb{padding:7px 14px;border-radius:20px;border:2px solid var(--bdr);background:#fff;font-family:var(--font);font-size:clamp(11px,2vw,13px);font-weight:700;cursor:pointer;transition:all .2s;color:var(--muted)}
.fb.on{background:var(--p);color:#fff;border-color:var(--p)}
.fb:hover:not(.on){border-color:var(--p);color:var(--p)}
.srch-bar{display:flex;align-items:center;background:#fff;border:2px solid var(--bdr);border-radius:10px;padding:7px 11px;gap:7px;margin-left:auto;transition:border-color .2s}
.srch-bar:focus-within{border-color:var(--p)}
.srch-bar input{border:none;background:transparent;font-family:var(--font);font-size:13px;outline:none;width:clamp(100px,20vw,180px)}

/* ══════════════════ TABLES ══════════════════ */
.tbl-wrap{overflow-x:auto;-webkit-overflow-scrolling:touch}
table{width:100%;border-collapse:collapse;font-size:clamp(11px,2vw,14px)}
thead tr{background:var(--bg)}
th{padding:clamp(8px,2vw,12px) clamp(8px,1.5vw,14px);text-align:left;font-size:clamp(9px,1.5vw,11px);font-weight:800;text-transform:uppercase;letter-spacing:.5px;color:var(--muted);white-space:nowrap}
td{padding:clamp(9px,2vw,13px) clamp(8px,1.5vw,14px);border-bottom:1px solid var(--bdr)}
tr:hover td{background:#f8faff}
tr:last-child td{border-bottom:none}
.badge{display:inline-block;padding:3px 9px;border-radius:20px;font-size:clamp(10px,1.8vw,12px);font-weight:700;white-space:nowrap}
.bg-ok{background:#d1fae5;color:#065f46}.bg-pend{background:#fef3c7;color:#92400e}
.bg-done{background:#dbeafe;color:#1e40af}.bg-prog{background:#ede9fe;color:#5b21b6}
.act-btns{display:flex;gap:4px;flex-wrap:wrap}

/* ══════════════════ MOBILE CARDS ══════════════════ */
.m-card{background:#fff;border-radius:12px;padding:clamp(12px,3vw,16px);margin-bottom:10px;box-shadow:var(--sh);border-left:4px solid var(--p)}
.mc-top{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:8px}
.mc-name{font-size:clamp(14px,3.5vw,16px);font-weight:800}
.mc-id{font-size:clamp(9px,2vw,11px);color:var(--muted);font-family:'JetBrains Mono',monospace;margin-top:2px}
.mc-amt{font-size:clamp(16px,4vw,20px);font-weight:800;color:var(--p)}
.mc-tags{display:flex;gap:6px;flex-wrap:wrap;margin-bottom:10px}
.mc-tag{font-size:clamp(10px,2vw,12px);background:var(--bg);padding:3px 8px;border-radius:6px;color:var(--muted)}
.mc-tag b{color:var(--txt)}
.mc-actions{display:flex;gap:5px;flex-wrap:wrap}

/* ══════════════════ STAFF GRID ══════════════════ */
.staff-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(clamp(220px,40vw,280px),1fr));gap:clamp(10px,2.5vw,16px)}
.staff-card{background:#fff;border-radius:var(--r);padding:clamp(16px,3.5vw,22px);box-shadow:var(--sh);transition:transform .2s}
.staff-card:hover{transform:translateY(-2px)}
.st-av{width:clamp(44px,8vw,52px);height:clamp(44px,8vw,52px);border-radius:clamp(11px,2vw,14px);background:linear-gradient(135deg,var(--p),var(--pur));display:flex;align-items:center;justify-content:center;font-size:clamp(18px,4vw,22px);font-weight:800;color:#fff;margin-bottom:12px}
.st-name{font-size:clamp(14px,3vw,16px);font-weight:800}
.st-id{font-size:clamp(10px,2vw,12px);color:var(--muted);font-family:'JetBrains Mono',monospace;margin-top:2px}
.st-meta{margin-top:10px;display:flex;flex-direction:column;gap:5px}
.st-row{font-size:clamp(11px,2vw,13px);color:var(--muted);display:flex;gap:6px}
.st-row b{color:var(--txt)}

/* ══════════════════ PENDING CARDS ══════════════════ */
.pend-card{background:#fff;border-radius:var(--r);padding:clamp(14px,3vw,18px);box-shadow:var(--sh);display:flex;align-items:center;gap:12px;margin-bottom:10px;border-left:4px solid var(--warn);transition:transform .2s}
.pend-card:hover{transform:translateX(3px)}
.pend-info{flex:1;min-width:0}
.pend-name{font-size:clamp(13px,3vw,15px);font-weight:800}
.pend-det{font-size:clamp(11px,2vw,13px);color:var(--muted);margin-top:3px}
.pend-amt{font-size:clamp(15px,3.5vw,18px);font-weight:800;color:var(--p);white-space:nowrap}

/* ══════════════════ INVOICE ══════════════════ */
.inv-layout{display:grid;grid-template-columns:1fr 1fr;gap:clamp(12px,3vw,20px);align-items:start}
.inv-sec-hdr{font-size:11px;font-weight:800;text-transform:uppercase;letter-spacing:1px;color:var(--p);background:#eff6ff;padding:6px 12px;border-radius:7px;margin-bottom:10px;border-left:3px solid var(--pl)}
.inv-upload{border:2px dashed var(--bdr);border-radius:10px;padding:12px 8px;text-align:center;cursor:pointer;transition:all .2s;color:var(--muted);background:#fafbff;min-height:66px;display:flex;align-items:center;justify-content:center;flex-direction:column}
.inv-upload:hover{border-color:var(--pl);background:#eff6ff;color:var(--p)}
.inv-svc-table{border:2px solid var(--bdr);border-radius:12px;overflow:hidden}
.inv-svc-hdr{display:flex;align-items:center;gap:8px;background:var(--bg);padding:9px 12px;font-size:11px;font-weight:800;text-transform:uppercase;color:var(--muted);letter-spacing:.5px}
.inv-svc-row{display:flex;align-items:center;gap:8px;padding:8px 12px;border-bottom:1px solid var(--bdr)}
.inv-svc-row:last-child{border-bottom:none}
.inv-svc-name{flex:1;padding:8px 10px;border:2px solid var(--bdr);border-radius:8px;font-family:var(--font);font-size:13px;outline:none;transition:border-color .2s}
.inv-svc-name:focus{border-color:var(--pl)}
.inv-svc-amt{width:100px;padding:8px 10px;border:2px solid var(--bdr);border-radius:8px;font-family:var(--font);font-size:13px;font-weight:700;text-align:right;outline:none;transition:border-color .2s}
.inv-svc-amt:focus{border-color:var(--ok)}
.inv-del{width:32px;height:32px;background:#fee2e2;border:none;border-radius:7px;cursor:pointer;font-size:15px;display:flex;align-items:center;justify-content:center;transition:all .2s;flex-shrink:0}
.inv-del:hover{background:var(--err);color:#fff}
.inv-pay-box{background:#f8faff;border:2px solid var(--bdr);border-radius:12px;padding:14px 16px;display:flex;flex-direction:column;gap:10px}
.inv-pay-row{display:flex;align-items:center;justify-content:space-between;font-size:14px;font-weight:700}
.inv-pay-val{font-size:18px;font-weight:800;color:var(--p)}

/* Invoice print preview */
.inv-doc{font-family:'Baloo 2',sans-serif;background:#fff;border:1px solid #e2e8f0;border-radius:12px;padding:24px;font-size:13px}
.inv-doc-head{display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:18px;padding-bottom:16px;border-bottom:2px solid #e2e8f0;gap:10px}
.inv-doc-logo{width:60px;height:60px;border-radius:10px;object-fit:contain;border:1px solid #e2e8f0}
.inv-doc-shopname{font-size:17px;font-weight:800;color:#0f2247;line-height:1.2}
.inv-doc-meta{font-size:11px;color:#64748b;margin-top:3px;line-height:1.7}
.inv-doc-invno{text-align:right;flex-shrink:0}
.inv-doc-invbig{font-size:11px;font-weight:800;text-transform:uppercase;color:#64748b;letter-spacing:1px}
.inv-doc-num{font-size:16px;font-weight:800;color:#1a3a6e;font-family:'JetBrains Mono',monospace}
.inv-doc-cust{background:#f8faff;border-radius:10px;padding:12px 14px;margin-bottom:14px;display:flex;justify-content:space-between;gap:10px;flex-wrap:wrap}
.inv-doc-cust-name{font-size:15px;font-weight:800;color:#0f2247}
.inv-doc-cust-mob{font-size:12px;color:#64748b;margin-top:2px}
table.inv-tbl{width:100%;border-collapse:collapse;margin-bottom:14px}
table.inv-tbl thead tr{background:#0f2247}
table.inv-tbl thead th{color:#fff;padding:9px 12px;text-align:left;font-size:11px;font-weight:800;text-transform:uppercase;letter-spacing:.5px}
table.inv-tbl thead th:last-child{text-align:right}
table.inv-tbl tbody tr{border-bottom:1px solid #f1f5f9}
table.inv-tbl tbody tr:last-child{border-bottom:none}
table.inv-tbl tbody td{padding:9px 12px;font-size:13px}
table.inv-tbl tbody td:last-child{text-align:right;font-weight:700;color:#1a3a6e}
.inv-tot-box{background:#f8faff;border-radius:10px;padding:12px 14px;display:flex;flex-direction:column;gap:7px;margin-bottom:14px}
.inv-tot-row{display:flex;justify-content:space-between;font-size:13px}
.inv-tot-final{background:#0f2247;color:#fff;border-radius:9px;padding:10px 14px;display:flex;justify-content:space-between;font-size:15px;font-weight:800}
.inv-doc-foot{display:flex;justify-content:space-between;align-items:flex-end;margin-top:14px;padding-top:14px;border-top:2px dashed #e2e8f0;flex-wrap:wrap;gap:10px}
.inv-doc-qr{width:60px;height:60px;object-fit:contain;border-radius:8px;border:1px solid #e2e8f0}
.inv-doc-sig{height:40px;object-fit:contain}
.inv-doc-thankyou{font-size:12px;color:#64748b;text-align:center;margin-top:10px}

@media(max-width:768px){
  .inv-layout{grid-template-columns:1fr}
}
@media(max-width:480px){
  .inv-svc-row{flex-wrap:wrap}
  .inv-svc-name{width:100%}
}
.bill-prev{border:1px solid var(--bdr);border-radius:12px;padding:clamp(16px,4vw,28px);font-family:var(--font);background:#fff}
.bill-head{text-align:center;border-bottom:2px dashed var(--bdr);padding-bottom:14px;margin-bottom:14px}
.bill-shop{font-size:clamp(15px,3.5vw,20px);font-weight:800;color:var(--pd)}
.bill-sub{font-size:clamp(10px,2vw,12px);color:var(--muted)}
.bill-row{display:flex;justify-content:space-between;padding:6px 0;border-bottom:1px solid var(--bg);font-size:clamp(11px,2vw,14px)}
.bill-row label{color:var(--muted);font-weight:600}
.bill-tot{background:var(--p);color:#fff;border-radius:10px;padding:12px 16px;display:flex;justify-content:space-between;margin-top:12px;font-weight:800;font-size:clamp(13px,2.5vw,16px)}
.bill-foot{text-align:center;margin-top:14px;font-size:clamp(10px,2vw,12px);color:var(--muted);border-top:2px dashed var(--bdr);padding-top:12px}

/* ══════════════════ ACTIVITY ══════════════════ */
.log-item{display:flex;gap:12px;padding:12px 0;border-bottom:1px solid var(--bdr)}
.log-item:last-child{border-bottom:none}
.log-ico{width:clamp(32px,6vw,38px);height:clamp(32px,6vw,38px);border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:clamp(14px,3vw,17px);flex-shrink:0}
.log-txt{font-size:clamp(11px,2vw,13px);flex:1}
.log-time{font-size:clamp(9px,1.8vw,11px);color:var(--muted);white-space:nowrap}

/* ══════════════════ SECTION HEADER ══════════════════ */
.sec-hdr{display:flex;align-items:center;justify-content:space-between;margin-bottom:clamp(12px,3vw,18px);flex-wrap:wrap;gap:10px}
.sec-hdr h3{font-size:clamp(15px,3.5vw,18px);font-weight:800}

/* ══════════════════ MODAL ══════════════════ */
.overlay{position:fixed;inset:0;background:rgba(0,0,0,.52);z-index:1000;display:flex;align-items:center;justify-content:center;padding:16px;backdrop-filter:blur(3px);visibility:hidden;opacity:0;pointer-events:none;transition:opacity .2s}
.overlay.on{visibility:visible;opacity:1;pointer-events:all}
.modal{background:#fff;border-radius:20px;padding:clamp(20px,5vw,32px);width:100%;max-width:500px;max-height:90vh;overflow-y:auto;animation:popIn .35s ease;box-shadow:0 24px 70px rgba(0,0,0,.28)}
.modal-hdr{display:flex;align-items:center;justify-content:space-between;margin-bottom:20px;padding-bottom:14px;border-bottom:2px solid var(--bg)}
.modal-ttl{font-size:clamp(14px,3vw,18px);font-weight:800}
.m-close{width:34px;height:34px;background:var(--bg);border:none;border-radius:8px;cursor:pointer;font-size:17px;display:flex;align-items:center;justify-content:center}
.m-close:hover{background:var(--bdr)}

/* PIN */
.pin-dots{display:flex;gap:10px;justify-content:center;margin:18px 0}
.pin-dot{width:15px;height:15px;border-radius:50%;border:2px solid var(--p);background:transparent;transition:background .15s}
.pin-dot.on{background:var(--p)}
.pin-pad{display:grid;grid-template-columns:repeat(3,1fr);gap:9px;max-width:230px;margin:0 auto}
.kbtn{padding:clamp(12px,3vw,14px);background:var(--bg);border:2px solid var(--bdr);border-radius:11px;font-size:clamp(16px,4vw,18px);font-weight:700;cursor:pointer;transition:all .15s;font-family:var(--font)}
.kbtn:hover{background:var(--p);color:#fff;border-color:var(--p)}
.kbtn:active{transform:scale(.94)}

/* Steps */
.steps{display:flex;align-items:center;gap:7px;justify-content:center;margin-bottom:22px}
.step{width:30px;height:30px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:800}
.step.done{background:var(--ok);color:#fff}
.step.now{background:var(--p);color:#fff}
.step.wait{background:var(--bg);color:var(--muted);border:2px solid var(--bdr)}
.step-line{flex:1;height:2px;background:var(--bdr);border-radius:2px}
.step-line.done{background:var(--ok)}

/* ══════════════════ UPLOAD ZONE ══════════════════ */
.upload-zone{border:2px dashed var(--bdr);border-radius:11px;padding:clamp(18px,4vw,28px);text-align:center;cursor:pointer;transition:all .2s;color:var(--muted)}
.upload-zone:hover{border-color:var(--p);background:#f0f4ff;color:var(--p)}
.uz-ico{font-size:clamp(26px,6vw,34px);margin-bottom:6px}
.uz-txt{font-size:clamp(12px,2.5vw,14px)}

/* ══════════════════ BOTTOM NAV (mobile only) ══════════════════ */
.bot-nav{display:none;position:fixed;bottom:0;left:0;right:0;background:#fff;border-top:2px solid var(--bdr);z-index:200;padding:4px 0 env(safe-area-inset-bottom,4px);box-shadow:0 -4px 18px rgba(0,0,0,.07)}
.bot-items{display:flex}
.bn-item{flex:1;display:flex;flex-direction:column;align-items:center;gap:2px;padding:6px 2px;cursor:pointer;transition:all .2s;border:none;background:transparent;font-family:var(--font);color:var(--muted);position:relative}
.bn-item.on{color:var(--p)}
.bn-ico{font-size:clamp(18px,5vw,22px);line-height:1}
.bn-lbl{font-size:clamp(8px,2vw,10px);font-weight:700}
.bn-badge{position:absolute;top:3px;right:calc(50% - 16px);background:var(--err);color:#fff;font-size:9px;font-weight:800;padding:1px 4px;border-radius:8px;min-width:14px;text-align:center}

/* ══════════════════ TOAST ══════════════════ */
.toast{position:fixed;bottom:clamp(70px,12vh,24px);left:50%;transform:translateX(-50%) translateY(60px);background:#1e293b;color:#fff;padding:11px clamp(14px,4vw,22px);border-radius:10px;font-size:clamp(12px,2.5vw,14px);font-weight:600;z-index:9999;transition:transform .3s;display:flex;align-items:center;gap:9px;box-shadow:0 8px 28px rgba(0,0,0,.28);white-space:nowrap;max-width:90vw}
.toast.show{transform:translateX(-50%) translateY(0)}
.toast.ok{background:var(--ok)}.toast.err{background:var(--err)}.toast.warn{background:var(--warn);color:#1e293b}

/* ══════════════════ SIDEBAR OVERLAY ══════════════════ */
.s-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.42);z-index:99}
.s-overlay.on{display:block}

/* ══════════════════ RESPONSIVE BREAKPOINTS ══════════════════ */

/* Large desktop */
@media(min-width:1280px){
  .sidebar{width:260px}
  .stats{grid-template-columns:repeat(6,1fr)}
  .bill-layout{grid-template-columns:1fr 1fr}
}

/* Medium desktop / tablet landscape */
@media(max-width:1279px) and (min-width:1024px){
  .sidebar{width:230px}
  .stats{grid-template-columns:repeat(3,1fr)}
}

/* Tablet portrait */
@media(max-width:1023px) and (min-width:769px){
  .sidebar{width:200px}
  .s-item{font-size:12px;padding:9px 10px}
  .s-logo-text h2{font-size:11px}
  .stats{grid-template-columns:repeat(3,1fr)}
  .bill-layout{grid-template-columns:1fr}
  .tb-search input{width:100px}
}

/* Mobile */
@media(max-width:768px){
  .sidebar{
    position:fixed;top:0;left:0;bottom:0;
    transform:translateX(-100%);
    z-index:100;width:260px;
    box-shadow:4px 0 24px rgba(0,0,0,.25);
  }
  .sidebar.open{transform:translateX(0)}
  .ham{display:flex}
  .tb-search{display:none}
  .page-wrap{padding:10px 10px 80px}
  .stats{grid-template-columns:repeat(2,1fr);gap:9px}
  .stat{padding:12px 10px}
  .dash-grid{grid-template-columns:1fr}
  .bill-layout{grid-template-columns:1fr}
  .bot-nav{display:block}
  /* hide desktop table, show mobile cards */
  .dt-only{display:none!important}
  .mob-only{display:block!important}
  .fg-grid{grid-template-columns:1fr}
  .welcome::after{font-size:40px;right:10px}
  .f-actions{gap:8px}
  .f-actions .btn{flex:1;justify-content:center}
  .staff-grid{grid-template-columns:1fr}
  .sec-hdr{flex-direction:row}
  .srch-bar{margin-left:0;width:100%}
  .srch-bar input{width:100%}
  .filter-bar{gap:6px}
  .modal{padding:18px 14px;border-radius:16px}
  .tb-clock{font-size:12px;padding:5px 8px}
  .topbar{padding:0 10px;height:52px}
}

@media(max-width:400px){
  .stats{grid-template-columns:repeat(2,1fr);gap:7px}
  .stat-val{font-size:18px}
  .page-wrap{padding:8px 8px 78px}
}

.mob-only{display:none}
.dt-only{display:block}
</style>
</head>
<body>

<!-- ═══════ LOGIN ═══════ -->
<div id="loginPage">
  <div class="login-box">
    <div class="login-logo">
      <div class="login-icon">🏛️</div>
      <h1>Prince Soni CSC Centre</h1>
      <p>Management System</p>
    </div>
    <div class="type-tabs">
      <button class="type-tab on" onclick="setType('Admin',this)">👑 Admin</button>
      <button class="type-tab" onclick="setType('Staff',this)">👤 Staff</button>
    </div>
    <div class="err-msg" id="loginErr">❌ गलत Username या Password</div>
    <div class="f-group">
      <label class="f-label">Username</label>
      <input class="f-input" id="lu" placeholder="Username..." onkeydown="if(event.key==='Enter')doLogin()"/>
    </div>
    <div class="f-group">
      <label class="f-label">Password</label>
      <input class="f-input" type="password" id="lp" placeholder="Password..." onkeydown="if(event.key==='Enter')doLogin()"/>
    </div>
    <button class="btn-login" onclick="doLogin()">🔐 Login करें</button>
    <div style="text-align:center;margin-top:14px">
      <button class="btn-link" onclick="showFP()">🔑 Password भूल गए?</button>
    </div>
  </div>
</div>

<!-- ═══════ APP ═══════ -->
<div id="app">
  <div class="app-layout">

    <!-- Sidebar overlay -->
    <div class="s-overlay" id="sOverlay" onclick="closeSB()"></div>

    <!-- SIDEBAR -->
    <aside class="sidebar" id="sidebar">
      <div class="s-logo">
        <div class="s-logo-icon">🏛️</div>
        <div class="s-logo-text">
          <h2>Prince Soni CSC</h2>
          <p>Management System</p>
        </div>
      </div>
      <nav class="s-nav">
        <div class="s-sec">MAIN</div>
        <button class="s-item on" onclick="go('dash',this)"><span class="ico">📊</span>Dashboard</button>
        <button class="s-item" onclick="go('add',this)"><span class="ico">➕</span>Record Add करें</button>
        <button class="s-item" onclick="go('records',this)"><span class="ico">📋</span>All Records</button>
        <div class="s-sec">MANAGE</div>
        <button class="s-item" onclick="go('pending',this)"><span class="ico">⏰</span>Pending Work<span class="s-badge" id="sBadge">0</span></button>
        <button class="s-item" onclick="go('staff',this)"><span class="ico">👥</span>Staff Management</button>
        <button class="s-item" onclick="go('bill',this)"><span class="ico">🧾</span>Bill Generate</button>
        <div class="s-sec">REPORTS</div>
        <button class="s-item" onclick="go('activity',this)"><span class="ico">📜</span>Activity History</button>
        <button class="s-item" onclick="go('export',this)"><span class="ico">📤</span>Export / Backup</button>
      </nav>
      <div class="s-foot">
        <div class="s-user">
          <div class="s-avatar" id="sAv">P</div>
          <div class="s-user-info">
            <h4 id="sName">Prince Soni</h4>
            <p id="sRole">Admin</p>
          </div>
        </div>
        <button class="s-btn s-btn-pass" onclick="showCP()">🔑 Password Change</button>
        <button class="s-btn s-btn-out" onclick="showLogout()">🚪 Logout</button>
      </div>
    </aside>

    <!-- MAIN -->
    <div class="main">
      <!-- Topbar -->
      <div class="topbar">
        <div class="tb-left">
          <button class="ham" onclick="toggleSB()">☰</button>
          <div class="tb-title" id="pgTitle">Dashboard</div>
        </div>
        <div class="tb-right">
          <div class="tb-search">
            <span>🔍</span>
            <input placeholder="Search..." oninput="gSearch(this.value)" id="gSearchIn"/>
          </div>
          <div class="tb-clock" id="clock">00:00:00</div>
          <button class="tb-notif" onclick="toggleNotif()">🔔<div class="notif-dot"></div></button>
        </div>
      </div>

      <!-- Notif popup -->
      <div id="notifPop" style="display:none;position:absolute;top:62px;right:12px;background:#fff;border-radius:14px;padding:16px;width:min(300px,90vw);box-shadow:0 16px 50px rgba(0,0,0,.18);z-index:300;border:1px solid var(--bdr)">
        <div style="font-size:13px;font-weight:800;margin-bottom:10px">🔔 Notifications</div>
        <div class="act-item"><div class="act-dot" style="background:var(--warn)"></div><div class="act-txt">⚠️ Mohit Kumar का ₹500 pending है</div><div class="act-time">आज</div></div>
        <div class="act-item"><div class="act-dot" style="background:var(--ok)"></div><div class="act-txt">✅ Rahul Sharma payment received</div><div class="act-time">2h</div></div>
        <div class="act-item"><div class="act-dot" style="background:var(--p)"></div><div class="act-txt">📋 नया record add किया</div><div class="act-time">5h</div></div>
      </div>

      <!-- Pages -->
      <div class="page-wrap">

        <!-- DASHBOARD -->
        <div class="page on" id="pg-dash">
          <div class="welcome">
            <h2 id="wName">Welcome, Prince Soni! 👋</h2>
            <p>Prince Soni CSC Centre Management System</p>
            <div class="welcome-date" id="wDate"></div>
          </div>
          <div class="stats" id="statsGrid"></div>
          <div class="dash-grid">
            <div class="card">
              <div class="card-ttl">📈 Daily Income (This Week)</div>
              <div class="bars" id="barsEl"></div>
              <div class="bar-lbls" id="barLbls"></div>
            </div>
            <div class="card">
              <div class="card-ttl">⚠️ Payment Reminders</div>
              <div id="dashRem"></div>
            </div>
            <div class="card">
              <div class="card-ttl">⚡ Recent Activity</div>
              <div id="dashAct"></div>
            </div>
            <div class="card">
              <div class="card-ttl">👥 Staff Status</div>
              <div id="dashStaff"></div>
            </div>
          </div>
        </div>

        <!-- ADD RECORD -->
        <div class="page" id="pg-add">
          <div class="form-wrap">
            <div class="form-ttl">➕ नया Record Add करें</div>
            <div class="fg-grid">
              <div class="fg"><label class="f-label">Customer Name *</label><input class="f-input" id="rc_name" placeholder="पूरा नाम..."/></div>
              <div class="fg"><label class="f-label">Mobile Number *</label><input class="f-input" id="rc_mob" type="tel" maxlength="10" placeholder="10-digit mobile..."/></div>
              <div class="fg"><label class="f-label">Amount (₹) *</label><input class="f-input" id="rc_amt" type="number" placeholder="0"/></div>
              <div class="fg"><label class="f-label">Profession</label>
                <select class="f-select" id="rc_prof">
                  <option value="">-- Select --</option>
                  <option>CSC Operator</option><option>Data Entry Operator</option>
                  <option>Online Service Agent</option><option>Insurance Agent</option>
                  <option>Banking Correspondent</option><option>Document Verification</option>
                  <option>Computer Operator</option><option>Government Service Agent</option>
                </select>
              </div>
              <div class="fg"><label class="f-label">Date</label><input class="f-input" id="rc_date" type="date"/></div>
              <div class="fg"><label class="f-label">Time</label><input class="f-input" id="rc_time" type="time"/></div>
              <div class="fg"><label class="f-label">Work Status</label>
                <select class="f-select" id="rc_ws">
                  <option value="inprogress">🔄 In Progress</option>
                  <option value="completed">✅ Completed</option>
                  <option value="pending">⏳ Pending</option>
                </select>
              </div>
            </div>

            <!-- Service Table -->
            <div class="fg" style="margin-top:4px">
              <label class="f-label">Service Name * <span style="text-transform:none;font-weight:400;color:var(--ok);font-size:10px">✔ Unlimited Add/Remove</span></label>
              <div class="inv-svc-table">
                <div class="inv-svc-hdr">
                  <div style="flex:1">Service Name</div>
                  <div style="width:90px;text-align:center">Price (₹)</div>
                  <div style="width:36px"></div>
                </div>
                <div id="rc_svcRows"></div>
                <div style="padding:8px 8px 4px">
                  <button type="button" onclick="addRcRow()" class="btn btn-p" style="width:100%;justify-content:center;padding:9px;font-size:13px">➕ Service Add करें</button>
                </div>
                <div style="background:#f0fdf4;border-top:1px solid var(--bdr);padding:8px 12px;display:flex;justify-content:space-between;align-items:center;border-radius:0 0 10px 10px">
                  <span style="font-size:12px;font-weight:700;color:var(--muted)">Total Amount</span>
                  <span id="rc_svcTotal" style="font-size:16px;font-weight:800;color:var(--ok)">₹0</span>
                </div>
              </div>
              <input type="hidden" id="rc_sVal"/>
            </div>

            <!-- Payment Status -->
            <div class="fg" style="margin-top:4px">
              <label class="f-label">Payment Status *</label>
              <div class="pay-toggle">
                <div class="pay-opt ok" id="po1" onclick="setPS('paid')">✅ Paid</div>
                <div class="pay-opt" id="po2" onclick="setPS('pending')">⏳ Pending</div>
              </div>
            </div>
            <div id="pendFlds" style="display:none">
              <div class="fg-grid" style="margin-top:12px">
                <div class="fg"><label class="f-label">Pending Payment Date</label><input class="f-input" id="rc_pd" type="date"/></div>
                <div class="fg"><label class="f-label">Reminder Date</label><input class="f-input" id="rc_rd" type="date"/></div>
              </div>
            </div>
            <div class="fg" style="margin-top:4px"><label class="f-label">Notes</label><textarea class="f-textarea" id="rc_notes" placeholder="Notes..."></textarea></div>
            <div class="fg">
              <label class="f-label">Documents Upload</label>
              <div class="upload-zone" onclick="toast('File upload: Select document, photo or PDF','ok')">
                <div class="uz-ico">📎</div>
                <div class="uz-txt">Click to upload Document / Photo / PDF</div>
              </div>
            </div>
            <div class="f-actions">
              <button class="btn btn-p" onclick="addRec()">💾 Save करें</button>
              <button class="btn btn-sec" onclick="clearForm()">🗑️ Clear</button>
            </div>
          </div>
        </div>

        <!-- ALL RECORDS -->
        <div class="page" id="pg-records">
          <div class="sec-hdr">
            <h3>📋 All Records</h3>
            <div style="display:flex;gap:8px;flex-wrap:wrap">
              <button class="btn btn-ok bsm" onclick="exportExcel()" style="padding:9px 14px">📊 Excel</button>
              <button class="btn btn-p bsm" onclick="exportPDF()" style="padding:9px 14px">📄 PDF</button>
            </div>
          </div>
          <div class="filter-bar">
            <button class="fb on" onclick="filterRec('all',this)">All</button>
            <button class="fb" onclick="filterRec('today',this)">📅 Today</button>
            <button class="fb" onclick="filterRec('paid',this)">✅ Paid</button>
            <button class="fb" onclick="filterRec('pending',this)">⏳ Pending</button>
            <button class="fb" onclick="filterRec('completed',this)">🎯 Done</button>
            <div class="srch-bar"><span>🔍</span><input placeholder="Name/Mobile..." oninput="searchRec(this.value)"/></div>
          </div>
          <!-- Desktop table -->
          <div class="card dt-only">
            <div class="tbl-wrap">
              <table>
                <thead><tr><th>ID</th><th>Customer</th><th>Mobile</th><th>Service</th><th>Amount</th><th>Payment</th><th>Work</th><th>Date</th><th>⏰ Time</th><th>Actions</th></tr></thead>
                <tbody id="recTbl"></tbody>
              </table>
            </div>
          </div>
          <!-- Mobile cards -->
          <div class="mob-only" id="recCards"></div>
        </div>

        <!-- PENDING -->
        <div class="page" id="pg-pending">
          <div class="sec-hdr">
            <h3>⏰ Pending Work</h3>
            <button class="btn btn-p bsm" onclick="go('add',null)" style="padding:9px 16px">+ Add</button>
          </div>
          <div id="pendList"></div>
        </div>

        <!-- STAFF -->
        <div class="page" id="pg-staff">
          <div class="sec-hdr">
            <h3>👥 Staff Management</h3>
            <button class="btn btn-p bsm" onclick="showAddStaff()" style="padding:9px 16px">+ Add Staff</button>
          </div>
          <div class="staff-grid" id="staffGrid"></div>
        </div>

        <!-- BILL -->
        <div class="page" id="pg-bill">
          <div class="inv-layout">

            <!-- LEFT: FORM -->
            <div class="form-wrap" style="min-width:0">
              <div class="form-ttl">🧾 Invoice Generate करें</div>

              <!-- SECTION 1: Header Uploads -->
              <div class="inv-sec-hdr">① Invoice Header</div>
              <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:14px">
                <div>
                  <label class="f-label">Logo Upload (Optional)</label>
                  <div class="inv-upload" id="logoUploadBox" onclick="document.getElementById('logoInput').click()">
                    <img id="logoPreviewImg" src="" style="display:none;max-height:54px;max-width:100%;border-radius:6px;object-fit:contain"/>
                    <div id="logoUploadPrompt"><div style="font-size:22px">🏢</div><div style="font-size:11px;margin-top:3px">Logo Upload</div></div>
                  </div>
                  <input type="file" id="logoInput" accept="image/*" style="display:none" onchange="uploadImg('logo',this)"/>
                </div>
                <div>
                  <label class="f-label">QR Code Upload</label>
                  <div class="inv-upload" id="qrUploadBox" onclick="document.getElementById('qrInput').click()">
                    <img id="qrPreviewImg" src="" style="display:none;max-height:54px;max-width:100%;border-radius:6px;object-fit:contain"/>
                    <div id="qrUploadPrompt"><div style="font-size:22px">📱</div><div style="font-size:11px;margin-top:3px">QR Code</div></div>
                  </div>
                  <input type="file" id="qrInput" accept="image/*" style="display:none" onchange="uploadImg('qr',this)"/>
                </div>
              </div>

              <!-- SECTION 2: Customer Details -->
              <div class="inv-sec-hdr">② Customer Details</div>
              <div class="fg-grid" style="margin-bottom:4px">
                <div class="fg"><label class="f-label">Customer Name *</label><input class="f-input" id="inv_name" placeholder="Customer का नाम..."/></div>
                <div class="fg"><label class="f-label">Mobile Number</label><input class="f-input" id="inv_mob" type="tel" placeholder="Mobile..."/></div>
                <div class="fg"><label class="f-label">Date</label><input class="f-input" id="inv_date" type="date"/></div>
                <div class="fg">
                  <label class="f-label">Invoice No</label>
                  <div style="display:flex;gap:6px;align-items:center">
                    <input class="f-input" id="inv_no" placeholder="INV-0001" style="flex:1"/>
                    <button onclick="autoInvNo()" style="padding:11px 10px;background:var(--p);color:#fff;border:none;border-radius:10px;cursor:pointer;font-size:13px;white-space:nowrap;font-family:var(--font);font-weight:700">🔄 Auto</button>
                  </div>
                </div>
              </div>

              <!-- SECTION 3: Services Table -->
              <div class="inv-sec-hdr" style="margin-top:10px">③ Services</div>
              <div class="inv-svc-table">
                <div class="inv-svc-hdr">
                  <div style="flex:1">Service Name</div>
                  <div style="width:100px;text-align:center">Amount (₹)</div>
                  <div style="width:40px"></div>
                </div>
                <div id="inv_svcRows"></div>
                <div style="padding:8px">
                  <button class="btn btn-p" onclick="addInvRow()" style="width:100%;justify-content:center;padding:10px">➕ Service Add करें</button>
                </div>
              </div>

              <!-- SECTION 4: Payment -->
              <div class="inv-sec-hdr" style="margin-top:10px">④ Payment</div>
              <div class="inv-pay-box">
                <div class="inv-pay-row">
                  <span>💰 Total Amount</span>
                  <span class="inv-pay-val" id="inv_total">₹0</span>
                </div>
                <div class="inv-pay-row" style="padding:8px 0;border-bottom:1px dashed var(--bdr)">
                  <span>💵 Paid Amount</span>
                  <input id="inv_paid" type="number" min="0" placeholder="0" oninput="calcInvPay()"
                    style="width:110px;padding:7px 10px;border:2px solid var(--bdr);border-radius:8px;font-family:var(--font);font-size:14px;font-weight:700;text-align:right;outline:none;color:var(--ok)"
                    onfocus="this.style.borderColor='var(--ok)'" onblur="this.style.borderColor='var(--bdr)'"/>
                </div>
                <div class="inv-pay-row" style="font-size:16px;font-weight:800;padding-top:4px">
                  <span>⚠️ Remaining</span>
                  <span id="inv_rem" style="color:var(--err)">₹0</span>
                </div>
              </div>

              <!-- SECTION 5: Extra Uploads -->
              <div class="inv-sec-hdr" style="margin-top:10px">⑤ Extra Uploads</div>
              <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:14px">
                <div>
                  <label class="f-label">Signature Upload</label>
                  <div class="inv-upload" onclick="document.getElementById('sigInput').click()">
                    <img id="sigPreviewImg" src="" style="display:none;max-height:44px;max-width:100%;object-fit:contain;border-radius:4px"/>
                    <div id="sigUploadPrompt"><div style="font-size:20px">✍️</div><div style="font-size:11px;margin-top:2px">Signature</div></div>
                  </div>
                  <input type="file" id="sigInput" accept="image/*" style="display:none" onchange="uploadImg('sig',this)"/>
                </div>
                <div>
                  <label class="f-label">Stamp Upload</label>
                  <div class="inv-upload" onclick="document.getElementById('stampInput').click()">
                    <img id="stampPreviewImg" src="" style="display:none;max-height:44px;max-width:100%;object-fit:contain;border-radius:4px"/>
                    <div id="stampUploadPrompt"><div style="font-size:20px">🔖</div><div style="font-size:11px;margin-top:2px">Stamp</div></div>
                  </div>
                  <input type="file" id="stampInput" accept="image/*" style="display:none" onchange="uploadImg('stamp',this)"/>
                </div>
              </div>

              <!-- SECTION 6: Actions -->
              <div class="inv-sec-hdr">⑥ Actions</div>
              <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
                <button class="btn btn-p" onclick="prevInv()" style="justify-content:center">👁️ Preview</button>
                <button class="btn btn-ok" onclick="printInv()" style="justify-content:center">⬇️ Download / Print</button>
                <button class="btn btn-warn" onclick="waInv()" style="justify-content:center">💬 WhatsApp</button>
                <button class="btn btn-sec" onclick="clearInv()" style="justify-content:center">🗑️ Clear</button>
              </div>
            </div>

            <!-- RIGHT: LIVE PREVIEW -->
            <div style="min-width:0">
              <div class="card" style="position:sticky;top:10px">
                <div class="card-ttl">👁️ Live Preview
                  <button onclick="prevInv()" style="margin-left:auto;background:var(--p);color:#fff;border:none;padding:5px 12px;border-radius:7px;font-family:var(--font);font-size:12px;font-weight:700;cursor:pointer">🔄 Refresh</button>
                </div>
                <div id="invPrevBox">
                  <div style="text-align:center;padding:40px;color:var(--muted)">
                    <div style="font-size:48px;margin-bottom:10px">🧾</div>
                    <p style="font-size:14px">Details भरें और Preview देखें</p>
                  </div>
                </div>
              </div>
            </div>

          </div><!-- inv-layout -->
        </div>

        <!-- ACTIVITY -->
        <div class="page" id="pg-activity">
          <div class="card">
            <div class="card-ttl">📜 Activity History</div>
            <div id="actLog"></div>
          </div>
        </div>

        <!-- EXPORT -->
        <div class="page" id="pg-export">
          <div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(clamp(200px,40vw,300px),1fr));gap:clamp(10px,2.5vw,18px);margin-bottom:18px">
            <div class="card">
              <div class="card-ttl">📤 Export</div>
              <p style="color:var(--muted);font-size:13px;margin-bottom:16px">Records को export करें</p>
              <div style="display:flex;flex-direction:column;gap:10px">
                <button class="btn btn-p" onclick="exportPDF()">📄 PDF Export</button>
                <button class="btn btn-ok" onclick="exportExcel()">📊 Excel Export</button>
              </div>
            </div>
            <div class="card">
              <div class="card-ttl">💾 Backup</div>
              <p style="color:var(--muted);font-size:13px;margin-bottom:16px">Data backup लें</p>
              <div style="display:flex;flex-direction:column;gap:10px">
                <button class="btn btn-warn" onclick="dlBackup()">⬇️ Backup Download (PC/Mobile)</button>
                <button class="btn btn-ok" onclick="document.getElementById('importFile').click()">📥 Backup Import करें</button>
                <input type="file" id="importFile" accept=".json" style="display:none" onchange="importBackup(this)"/>
                <div style="background:#eff6ff;border-radius:8px;padding:10px 12px;font-size:12px;color:var(--p);margin-top:4px">
                  💡 <b>Mobile → PC Sync:</b> Mobile pe Backup Download करें → PC pe Import करें
                </div>
              </div>
            </div>
          </div>
          <div class="card">
            <div class="card-ttl">📊 Report Summary</div>
            <div class="stats" id="expStats" style="margin-bottom:0"></div>
          </div>
        </div>

      </div><!-- page-wrap -->
    </div><!-- main -->
  </div><!-- app-layout -->

  <!-- BOTTOM NAV -->
  <nav class="bot-nav">
    <div class="bot-items">
      <button class="bn-item on" id="bn-dash" onclick="go('dash',null);setBN('dash')"><span class="bn-ico">📊</span><span class="bn-lbl">Dashboard</span></button>
      <button class="bn-item" id="bn-add" onclick="go('add',null);setBN('add')"><span class="bn-ico">➕</span><span class="bn-lbl">Add</span></button>
      <button class="bn-item" id="bn-records" onclick="go('records',null);setBN('records')"><span class="bn-ico">📋</span><span class="bn-lbl">Records</span></button>
      <button class="bn-item" id="bn-pending" onclick="go('pending',null);setBN('pending')"><span class="bn-ico">⏰</span><span class="bn-lbl">Pending</span><span class="bn-badge" id="bnBadge">0</span></button>
      <button class="bn-item" id="bn-bill" onclick="go('bill',null);setBN('bill')"><span class="bn-ico">🧾</span><span class="bn-lbl">Bill</span></button>
    </div>
  </nav>
</div><!-- app -->

<!-- ═══════ MODALS ═══════ -->

<!-- Forgot Password -->
<div class="overlay" id="fpModal">
  <div class="modal" style="max-width:400px">
    <div class="modal-hdr"><div class="modal-ttl">🔑 Password Reset</div><button class="m-close" onclick="closeM('fpModal')">✕</button></div>
    <div class="steps"><div class="step now" id="sp1">1</div><div class="step-line" id="sl1"></div><div class="step wait" id="sp2">2</div><div class="step-line" id="sl2"></div><div class="step wait" id="sp3">3</div></div>
    <div id="fp1"><div class="fg"><label class="f-label">Username या Mobile</label><input class="f-input" id="fp_u" placeholder="Username..."/></div><button class="btn btn-p" style="width:100%" onclick="fpN1()">Next →</button></div>
    <div id="fp2" style="display:none"><p style="font-size:13px;color:var(--muted);text-align:center;margin-bottom:14px">📱 OTP Sent: ****7282 &nbsp; Demo OTP: <b>123456</b></p><div class="fg"><label class="f-label">OTP</label><input class="f-input" id="fp_otp" maxlength="6" placeholder="6-digit OTP" style="text-align:center;font-size:22px;letter-spacing:8px;font-weight:800"/></div><button class="btn btn-p" style="width:100%" onclick="fpN2()">Verify →</button></div>
    <div id="fp3" style="display:none"><div class="fg"><label class="f-label">New Password</label><input class="f-input" type="password" id="fp_np" placeholder="New password..."/></div><div class="fg"><label class="f-label">Confirm Password</label><input class="f-input" type="password" id="fp_cp" placeholder="Confirm..."/></div><button class="btn btn-p" style="width:100%" onclick="fpReset()">✅ Reset Password</button></div>
  </div>
</div>

<!-- PIN Modal -->
<div class="overlay" id="pinModal">
  <div class="modal" style="max-width:340px;text-align:center">
    <div class="modal-hdr"><div class="modal-ttl">🔒 Security PIN</div><button class="m-close" onclick="closeM('pinModal')">✕</button></div>
    <p style="font-size:13px;color:var(--muted);margin-bottom:14px" id="pinDesc">Delete के लिए PIN enter करें</p>
    <div class="pin-dots" id="pinDots"><div class="pin-dot"></div><div class="pin-dot"></div><div class="pin-dot"></div><div class="pin-dot"></div><div class="pin-dot"></div><div class="pin-dot"></div></div>
    <div class="pin-pad">
      <button class="kbtn" onclick="pk('1')">1</button><button class="kbtn" onclick="pk('2')">2</button><button class="kbtn" onclick="pk('3')">3</button>
      <button class="kbtn" onclick="pk('4')">4</button><button class="kbtn" onclick="pk('5')">5</button><button class="kbtn" onclick="pk('6')">6</button>
      <button class="kbtn" onclick="pk('7')">7</button><button class="kbtn" onclick="pk('8')">8</button><button class="kbtn" onclick="pk('9')">9</button>
      <button class="kbtn" onclick="pk('c')" style="font-size:12px">CLR</button><button class="kbtn" onclick="pk('0')">0</button><button class="kbtn" onclick="pk('b')">⌫</button>
    </div>
    <p style="font-size:12px;color:var(--err);margin-top:12px;min-height:18px" id="pinErr"></p>
  </div>
</div>

<!-- View Record -->
<div class="overlay" id="viewModal">
  <div class="modal"><div class="modal-hdr"><div class="modal-ttl">👁️ Record Details</div><button class="m-close" onclick="closeM('viewModal')">✕</button></div><div id="viewBody"></div></div>
</div>

<!-- Edit Record -->
<div class="overlay" id="editModal">
  <div class="modal"><div class="modal-hdr"><div class="modal-ttl">✏️ Record Edit</div><button class="m-close" onclick="closeM('editModal')">✕</button></div><div id="editBody"></div></div>
</div>

<!-- Add Staff -->
<div class="overlay" id="staffModal">
  <div class="modal">
    <div class="modal-hdr"><div class="modal-ttl">👤 Staff Add करें</div><button class="m-close" onclick="closeM('staffModal')">✕</button></div>
    <div class="fg-grid">
      <div class="fg"><label class="f-label">Staff Name</label><input class="f-input" id="st_n" placeholder="Full name..."/></div>
      <div class="fg"><label class="f-label">Mobile</label><input class="f-input" id="st_m" type="tel" placeholder="Mobile..."/></div>
      <div class="fg"><label class="f-label">Profession</label><select class="f-select" id="st_p"><option>CSC Operator</option><option>Data Entry Operator</option><option>Computer Operator</option><option>Online Service Agent</option></select></div>
      <div class="fg"><label class="f-label">Username</label><input class="f-input" id="st_u" placeholder="Username..."/></div>
      <div class="fg"><label class="f-label">Password</label><input class="f-input" id="st_pw" placeholder="Auto-generated..."/><button class="bsm bsm-sec" style="margin-top:6px" onclick="genPW()">🔄 Generate</button></div>
    </div>
    <div class="f-actions"><button class="btn btn-p" onclick="addStaff()">💾 Add Staff</button><button class="btn btn-sec" onclick="closeM('staffModal')">Cancel</button></div>
  </div>
</div>

<!-- Change Password -->
<div class="overlay" id="cpModal">
  <div class="modal" style="max-width:400px">
    <div class="modal-hdr"><div class="modal-ttl">🔑 Password Change</div><button class="m-close" onclick="closeM('cpModal')">✕</button></div>
    <div style="background:#eff6ff;border-radius:9px;padding:10px 14px;margin-bottom:16px;font-size:13px;color:var(--p)">👤 <strong id="cpUser">Prince</strong> | <strong id="cpRole">Admin</strong></div>
    <div class="fg"><label class="f-label">Current Password</label><input class="f-input" type="password" id="cp_cur" placeholder="Current password..."/></div>
    <div class="fg"><label class="f-label">New Password</label><input class="f-input" type="password" id="cp_new" placeholder="New password..."/></div>
    <div class="fg"><label class="f-label">Confirm Password</label><input class="f-input" type="password" id="cp_cf" placeholder="Confirm..."/></div>
    <div class="err-msg" id="cpErr" style="margin-bottom:12px"></div>
    <div class="f-actions"><button class="btn btn-p" style="flex:1" onclick="doCP()">✅ Change Password</button><button class="btn btn-sec" onclick="closeM('cpModal')">Cancel</button></div>
  </div>
</div>

<!-- Logout -->
<div class="overlay" id="logoutModal">
  <div class="modal" style="max-width:340px;text-align:center">
    <div style="font-size:54px;margin-bottom:10px">🚪</div>
    <div style="font-size:18px;font-weight:800;margin-bottom:8px">Logout करें?</div>
    <p style="font-size:14px;color:var(--muted);margin-bottom:22px"><strong id="logUser">Prince Soni</strong> के account से logout होंगे</p>
    <div style="display:flex;gap:10px"><button class="btn btn-sec" style="flex:1" onclick="closeM('logoutModal')">❌ Cancel</button><button class="btn btn-err" style="flex:1" onclick="doLogout()">🚪 Logout</button></div>
  </div>
</div>

<!-- Reminder Popup -->
<div id="remPop" style="display:none;position:fixed;bottom:clamp(70px,12vh,24px);right:12px;background:#fff;border-radius:14px;padding:18px;width:min(290px,90vw);box-shadow:0 16px 50px rgba(0,0,0,.2);z-index:500;border-left:4px solid var(--warn)">
  <div style="font-size:18px;margin-bottom:6px">⚠️ Payment Reminder</div>
  <div style="font-size:15px;font-weight:800" id="remN">—</div>
  <div style="font-size:13px;color:var(--muted);margin:4px 0 14px">Amount: <b id="remA">—</b></div>
  <div style="display:flex;gap:8px">
    <button class="bsm bsm-warn" style="flex:1" onclick="remLater()">🔔 Later</button>
    <button class="bsm bsm-ok" style="flex:1" onclick="remPaid()">✅ Mark Paid</button>
  </div>
</div>

<!-- Toast -->
<div class="toast" id="toastEl"></div>

<script>
// ════════════════════════════════════════
// DATA
// ════════════════════════════════════════
const SERVICES=[
  '🪪 Aadhar Card','🔄 Aadhar Update','💳 PAN Card','🔄 PAN Update',
  '📘 Passport Application','🔄 Passport Renewal','🗳️ Voter ID Card','🔄 Voter ID Update',
  '🚗 Driving License','🔄 DL Renewal','🍚 Ration Card','🔄 Ration Update',
  '📄 Income Certificate','📄 Caste Certificate','📄 Residence Certificate',
  '📄 Birth Certificate','📄 Death Certificate','📄 Marriage Certificate','📄 Character Certificate',
  '🌾 Land Record','🏠 Property Registration','🏦 Bank Account Opening','📒 Passbook Update',
  '🏦 Jan Dhan Account','🌾 PM Kisan Registration','🌾 PM Kisan Status',
  '💊 Ayushman Card','💊 Ayushman Bharat','👷 Labour Card','🛠️ E-Shram Card',
  '🛡️ Insurance Policy','🛡️ Life Insurance','👴 Pension Registration',
  '👴 Old Age Pension','👩 Widow Pension','♿ Disability Certificate',
  '💼 Job Card MNREGA','🎓 Scholarship Form','📝 Admission Form',
  '📝 Online Form Fill','📝 Govt Job Form','🚂 Railway Ticket','🚌 Bus Ticket',
  '📱 Mobile Recharge','📡 DTH Recharge','⚡ Electricity Bill','💧 Water Bill',
  '🔥 Gas Connection','📠 Photo Copy','🖼️ Lamination','⌨️ Typing Work',
  '💻 Data Entry','🌐 Email / Internet','🔧 Other Service'
];
const PIN='124411';
const SAMPLE_RECS=[
  {id:'PSC-001',name:'Rahul Sharma',mob:'9812345678',service:'Aadhar Card, PAN Card',prof:'Computer Operator',amt:800,ps:'paid',ws:'completed',date:'2026-03-12',time:'10:30',notes:'Urgent'},
  {id:'PSC-002',name:'Mohit Kumar',mob:'9876543210',service:'Aadhar Update',prof:'CSC Operator',amt:200,ps:'pending',ws:'pending',date:'2026-03-13',time:'11:00',notes:'',pd:'2026-03-20',rd:'2026-03-18'},
  {id:'PSC-003',name:'Sunita Devi',mob:'9988776655',service:'Income Certificate',prof:'Government Service Agent',amt:350,ps:'paid',ws:'completed',date:'2026-03-11',time:'14:20',notes:''},
];
const SAMPLE_STAFF=[
  {id:'STAFF101',name:'Ravi Kumar',mob:'9712345678',prof:'CSC Operator',user:'ravi',pw:'Ravi@2026',join:'2025-01-15'},
  {id:'STAFF102',name:'Sanjay Singh',mob:'9823456789',prof:'Data Entry Operator',user:'sanjay',pw:'Sanjay@2026',join:'2025-06-10'},
];

// ── localStorage helpers ──────────────────
function lsGet(key,def){
  try{const v=localStorage.getItem('csc_'+key);return v?JSON.parse(v):def;}
  catch(e){return def;}
}
function lsSet(key,val){
  try{localStorage.setItem('csc_'+key,JSON.stringify(val));}
  catch(e){console.warn('Storage full',e);}
}
function saveData(){
  lsSet('recs',recs);
  lsSet('staff',staffList);
  lsSet('actLog',actLog);
  lsSet('adminPW',adminPW);
  lsSet('billCtr',billCtr);
}
function loadData(){
  recs      = lsGet('recs',     SAMPLE_RECS);
  staffList = lsGet('staff',    SAMPLE_STAFF);
  actLog    = lsGet('actLog',   []);
  adminPW   = lsGet('adminPW',  'Prince@6864');
  billCtr   = lsGet('billCtr',  10);
}

// ── All variables declared FIRST ──────────
let recs=[], staffList=[], actLog=[];
let adminPW='Prince@6864';
let billCtr=10;
let curUser={};
let payStatus='paid';
let selSvc_rc=[], selSvc_bill=[];
let pinStr='', pinAction=null, pinTarget=null;
let recFilter='all';
let fpStep=1;
let userTypes='Admin';

// ── Now load from localStorage ─────────────
loadData();

// ════════════════════════════════════════
// LOGIN
// ════════════════════════════════════════
function setType(t,btn){
  userTypes=t;
  document.querySelectorAll('.type-tab').forEach(b=>b.classList.remove('on'));
  btn.classList.add('on');
}
function doLogin(){
  const u=document.getElementById('lu').value.trim();
  const p=document.getElementById('lp').value;
  const err=document.getElementById('loginErr');
  const box=document.querySelector('.login-box');
  if(userTypes==='Admin'){
    if(u==='Prince'&&p===adminPW){
      err.style.display='none';
      loginOK({name:'Prince Soni',role:'Admin',user:'Prince'});
    } else {
      err.style.display='block';
      box.classList.remove('shake');
      void box.offsetWidth;
      box.classList.add('shake');
      setTimeout(()=>box.classList.remove('shake'),500);
    }
  } else {
    const s=staffList.find(x=>x.user===u&&x.pw===p);
    if(s){
      err.style.display='none';
      loginOK({name:s.name,role:'Staff',user:s.user});
    } else {
      err.style.display='block';
      box.classList.remove('shake');
      void box.offsetWidth;
      box.classList.add('shake');
      setTimeout(()=>box.classList.remove('shake'),500);
    }
  }
}
function loginOK(u){
  curUser=u;
  loadData();
  document.getElementById('loginPage').style.display='none';
  document.getElementById('app').style.display='block';
  document.getElementById('sAv').textContent=u.name.charAt(0);
  document.getElementById('sName').textContent=u.name;
  document.getElementById('sRole').textContent=u.role;
  document.getElementById('wName').textContent='Welcome, '+u.name+'! 👋';
  logAct('add',u.name+' ने login किया');
  saveData();
  initApp();
}
function initApp(){
  const now=new Date();
  document.getElementById('wDate').textContent='📅 '+now.toLocaleDateString('hi-IN',{weekday:'long',year:'numeric',month:'long',day:'numeric'});
  const today=now.toISOString().split('T')[0];
  const time=now.toTimeString().split(':').slice(0,2).join(':');
  setVal('rc_date',today);setVal('rc_time',time);setVal('b_date',today);setVal('inv_date',today);
  initMS('rc');initMS('bill');
  autoInvNo();
  addInvRow();
  addRcRow();
  renderAll();startClock();
  updateBadge();
  setTimeout(()=>{
    const pend=recs.filter(r=>r.ps==='pending');
    if(pend.length){
      document.getElementById('remN').textContent=pend[0].name;
      document.getElementById('remA').textContent='₹'+pend[0].amt;
      document.getElementById('remPop').style.display='block';
    }
  },3000);
}
function setVal(id,v){const el=document.getElementById(id);if(el)el.value=v;}
function renderAll(){renderDash();renderRecs(recs);renderPending();renderStaff();renderActLog();renderExp();}

// ════════════════════════════════════════
// CLOCK
// ════════════════════════════════════════
function startClock(){
  function tick(){
    const n=new Date();
    const el=document.getElementById('clock');
    if(el) el.textContent=[n.getHours(),n.getMinutes(),n.getSeconds()].map(x=>String(x).padStart(2,'0')).join(':');
  }
  tick(); setInterval(tick,1000);
}

// ════════════════════════════════════════
// NAVIGATION
// ════════════════════════════════════════
const pgTitles={dash:'Dashboard',add:'Record Add करें',records:'All Records',pending:'Pending Work',staff:'Staff Management',bill:'Bill Generate',activity:'Activity History',export:'Export & Backup'};
function go(id,btn){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('on'));
  document.querySelectorAll('.s-item').forEach(n=>n.classList.remove('on'));
  const el=document.getElementById('pg-'+id);
  if(el) el.classList.add('on');
  if(btn) btn.classList.add('on');
  document.getElementById('pgTitle').textContent=pgTitles[id]||id;
  closeSB();
}
function setBN(id){
  document.querySelectorAll('.bn-item').forEach(b=>b.classList.remove('on'));
  const el=document.getElementById('bn-'+id);
  if(el) el.classList.add('on');
}
function toggleSB(){
  document.getElementById('sidebar').classList.toggle('open');
  document.getElementById('sOverlay').classList.toggle('on');
}
function closeSB(){
  document.getElementById('sidebar').classList.remove('open');
  document.getElementById('sOverlay').classList.remove('on');
}
function toggleNotif(){
  const el=document.getElementById('notifPop');
  el.style.display=el.style.display==='none'?'block':'none';
}

// ════════════════════════════════════════
// MULTI-SELECT SERVICE
// ════════════════════════════════════════
function initMS(ns){renderMSList(ns,'');}
function openMS(ns){
  document.getElementById(ns+'_sPanel').classList.add('open');
  document.getElementById(ns+'_sTags').classList.add('open');
}
function closeMS(ns){
  document.getElementById(ns+'_sPanel').classList.remove('open');
  document.getElementById(ns+'_sTags').classList.remove('open');
}
function filterMS(ns,q){renderMSList(ns,q);}
function getSel(ns){return ns==='rc'?selSvc_rc:selSvc_bill;}
function renderMSList(ns,filter){
  const sel=getSel(ns);
  const list=document.getElementById(ns+'_sList');
  if(!list) return;
  const filtered=SERVICES.filter(s=>s.toLowerCase().includes(filter.toLowerCase()));
  list.innerHTML=filtered.map(s=>{
    const on=sel.includes(s);
    const selCls=on?" sel":"";
    const chkCls=on?" on":"";
    const chk=on?"✓":"";
    const safeS=s.replace(/'/g,"&#39;").replace(/"/g,"&quot;");
    return "<div class=\"ms-opt"+selCls+"\" onclick=\"toggleSvc('"+ns+"','"+safeS+"')\">"
      +"<div class=\"ms-chk"+chkCls+"\">"+chk+"</div>"
      +"<span>"+s+"</span></div>";
  }).join("");
  const cnt=document.getElementById(ns+'_sCnt');
  if(cnt) cnt.textContent=sel.length+' selected';
}
function toggleSvc(ns,name){
  const sel=getSel(ns);
  const i=sel.indexOf(name);
  if(i===-1) sel.push(name); else sel.splice(i,1);
  renderMSList(ns,document.getElementById(ns+'_sIn')?.value||'');
  updateMSTags(ns);
}
function updateMSTags(ns){
  const sel=getSel(ns);
  const box=document.getElementById(ns+'_sTags');
  const ph=document.getElementById(ns+'_sPh');
  if(!box) return;
  const tags=box.querySelectorAll('.ms-tag');
  tags.forEach(t=>t.remove());
  if(ph) ph.style.display=sel.length?'none':'inline';
  sel.forEach(s=>{
    const tag=document.createElement('span');
    tag.className='ms-tag';
    tag.innerHTML=s+' <span onclick="removeSvc(\''+ns+'\',\''+s.replace(/'/g,"\\'")+'\',...arguments)">×</span>';
    box.insertBefore(tag,ph||null);
  });
  const hid=document.getElementById(ns+'_sVal');
  if(hid) hid.value=sel.map(s=>s.replace(/^[^\s]+\s/,'')).join(', ');
  const cnt=document.getElementById(ns+'_sCnt');
  if(cnt) cnt.textContent=sel.length+' selected';
}
function removeSvc(ns,name,e){
  if(e){e.stopPropagation();}
  const sel=getSel(ns);
  const i=sel.indexOf(name);
  if(i!==-1) sel.splice(i,1);
  renderMSList(ns,'');
  updateMSTags(ns);
}
function resetMS(ns){
  if(ns==='rc') selSvc_rc=[];
  else selSvc_bill=[];
  renderMSList(ns,'');
  updateMSTags(ns);
}

// ════════════════════════════════════════
// DASHBOARD
// ════════════════════════════════════════
function renderDash(){
  const paid=recs.filter(r=>r.ps==='paid');
  const pend=recs.filter(r=>r.ps==='pending');
  const done=recs.filter(r=>r.ws==='completed');
  const today=recs.filter(r=>r.date===new Date().toISOString().split('T')[0]);
  const statsData=[
    {ico:'📋',val:recs.length,lbl:'Total Records',c:'c1'},
    {ico:'💰',val:'₹'+paid.reduce((a,r)=>a+r.amt,0).toLocaleString('en-IN'),lbl:'Total Amount',c:'c2'},
    {ico:'⏳',val:'₹'+pend.reduce((a,r)=>a+r.amt,0).toLocaleString('en-IN'),lbl:'Pending Amount',c:'c3'},
    {ico:'🔴',val:pend.length,lbl:'Pending Work',c:'c4'},
    {ico:'✅',val:done.length,lbl:'Completed',c:'c5'},
    {ico:'📅',val:today.length,lbl:"Today's Work",c:'c6'},
  ];
  document.getElementById('statsGrid').innerHTML=statsData.map(s=>`<div class="stat ${s.c}"><div class="stat-ico">${s.ico}</div><div class="stat-val">${s.val}</div><div class="stat-lbl">${s.lbl}</div></div>`).join('');

  // Bars
  const days=['Mon','Tue','Wed','Thu','Fri','Sat','Sun'];
  const inc=[800,1200,650,1800,900,2100,500];
  const mx=Math.max(...inc);
  document.getElementById('barsEl').innerHTML=inc.map((v,i)=>`<div class="bar" style="height:${Math.round(v/mx*100)}%" title="${days[i]}: ₹${v}"></div>`).join('');
  document.getElementById('barLbls').innerHTML=days.map(d=>`<div class="bar-lbl">${d}</div>`).join('');

  // Reminders
  let rh='';
  pend.slice(0,3).forEach(r=>{
    rh+=`<div class="rem-item"><span style="font-size:20px">⚠️</span><div class="rem-info"><div class="rem-name">${r.name}</div><div class="rem-amt">₹${r.amt} • ${r.service}</div></div><button class="bsm bsm-ok" onclick="markPaid('${r.id}')">✅ Paid</button></div>`;
  });
  if(!pend.length) rh='<p style="color:var(--muted);font-size:13px;text-align:center;padding:18px">🎉 कोई pending नहीं!</p>';
  document.getElementById('dashRem').innerHTML=rh;

  // Activity
  document.getElementById('dashAct').innerHTML=actLog.slice(0,4).map(a=>{
    const c={add:'var(--ok)',del:'var(--err)',edit:'var(--p)',pay:'var(--acc)'}[a.type]||'var(--p)';
    return `<div class="act-item"><div class="act-dot" style="background:${c}"></div><div class="act-txt">${a.txt}</div><div class="act-time">${a.time}</div></div>`;
  }).join('');

  // Staff
  document.getElementById('dashStaff').innerHTML=staffList.map(s=>`
    <div class="act-item">
      <div class="s-avatar" style="width:32px;height:32px;border-radius:8px;font-size:13px;flex-shrink:0">${s.name.charAt(0)}</div>
      <div style="flex:1"><div style="font-size:13px;font-weight:700">${s.name}</div><div style="font-size:11px;color:var(--muted)">${s.prof}</div></div>
      <span class="badge bg-ok">Active</span>
    </div>`).join('');
}

// ════════════════════════════════════════
// RECORDS
// ════════════════════════════════════════
function renderRecs(data){
  // Desktop table
  const noRow=`<tr><td colspan="10" style="text-align:center;padding:36px;color:var(--muted)">कोई record नहीं मिला</td></tr>`;
  document.getElementById('recTbl').innerHTML=data.length?data.map(r=>recRow(r)).join(''):noRow;
  // Mobile cards
  document.getElementById('recCards').innerHTML=data.length?data.map(r=>recCard(r)).join(''):'<div style="text-align:center;padding:32px;color:var(--muted);background:#fff;border-radius:12px">कोई record नहीं मिला</div>';
}
function recRow(r){
  const ps=r.ps==='paid';
  const wsCls=r.ws==='completed'?'bg-done':r.ws==='inprogress'?'bg-prog':'bg-pend';
  const wsLbl=r.ws==='completed'?'Done':r.ws==='inprogress'?'Progress':'Pending';
  return `<tr>
    <td style="font-family:'JetBrains Mono';font-size:11px">${r.id}</td>
    <td><b>${r.name}</b></td><td>${r.mob}</td>
    <td style="max-width:140px;font-size:12px">${r.service}</td>
    <td style="font-weight:800;color:var(--p)">₹${r.amt}</td>
    <td><span class="badge ${ps?'bg-ok':'bg-pend'}">${ps?'✅ Paid':'⏳ Pending'}</span></td>
    <td><span class="badge ${wsCls}">${wsLbl}</span></td>
    <td style="white-space:nowrap;font-size:12px">${r.date}</td>
    <td style="font-family:'JetBrains Mono';font-size:12px;font-weight:700;color:var(--pd)">${r.time||'--:--'}</td>
    <td><div class="act-btns">
      <button class="bsm bsm-p" onclick="viewRec('${r.id}')">👁️</button>
      <button class="bsm bsm-sec" onclick="editRec('${r.id}')">✏️</button>
      <button class="bsm bsm-ok" onclick="updAmt('${r.id}')">💰</button>
      <button class="bsm bsm-warn" onclick="updSt('${r.id}')">🔄</button>
      <button class="bsm bsm-err" onclick="delRec('${r.id}')">🗑️</button>
      <button class="bsm bsm-p" onclick="genBill('${r.id}')">🧾</button>
    </div></td>
  </tr>`;
}
function recCard(r){
  const ps=r.ps==='paid';
  return `<div class="m-card" style="border-left-color:${ps?'var(--ok)':'var(--warn)'}">
    <div class="mc-top">
      <div><div class="mc-name">${r.name}</div><div class="mc-id">${r.id} • ${r.date} ${r.time?'• '+r.time:''}</div></div>
      <div class="mc-amt">₹${r.amt}</div>
    </div>
    <div class="mc-tags">
      <span class="mc-tag">📱 <b>${r.mob}</b></span>
      <span class="mc-tag">🔧 <b>${r.service.length>22?r.service.slice(0,22)+'...':r.service}</b></span>
      <span class="badge ${ps?'bg-ok':'bg-pend'}" style="font-size:10px">${ps?'✅ Paid':'⏳ Pending'}</span>
    </div>
    <div class="mc-actions">
      <button class="bsm bsm-p" onclick="viewRec('${r.id}')">👁️ View</button>
      <button class="bsm bsm-sec" onclick="editRec('${r.id}')">✏️ Edit</button>
      <button class="bsm bsm-ok" onclick="updAmt('${r.id}')">💰</button>
      <button class="bsm bsm-warn" onclick="updSt('${r.id}')">🔄</button>
      <button class="bsm bsm-p" onclick="genBill('${r.id}')">🧾 Bill</button>
      <button class="bsm bsm-err" onclick="delRec('${r.id}')">🗑️</button>
    </div>
  </div>`;
}
function filterRec(f,btn){
  recFilter=f;
  document.querySelectorAll('.fb').forEach(b=>b.classList.remove('on'));
  if(btn) btn.classList.add('on');
  const today=new Date().toISOString().split('T')[0];
  let data=recs;
  if(f==='today') data=recs.filter(r=>r.date===today);
  else if(f==='paid') data=recs.filter(r=>r.ps==='paid');
  else if(f==='pending') data=recs.filter(r=>r.ps==='pending');
  else if(f==='completed') data=recs.filter(r=>r.ws==='completed');
  renderRecs(data);
}
function searchRec(q){
  if(!q){filterRec(recFilter,null);return;}
  renderRecs(recs.filter(r=>r.name.toLowerCase().includes(q.toLowerCase())||r.mob.includes(q)));
}

// ════════════════════════════════════════
// ADD RECORD - SERVICE ROWS
// ════════════════════════════════════════
let rcRows=[];

function addRcRow(val,price){
  const id='rcr_'+Date.now()+'_'+Math.random().toString(36).slice(2,5);
  rcRows.push(id);
  const container=document.getElementById('rc_svcRows');
  const div=document.createElement('div');
  div.className='inv-svc-row';
  div.id=id;
  div.innerHTML=
    '<input class="inv-svc-name" placeholder="Service name..." value="'+(val||'')+'" oninput="syncRcSvc()" style="flex:1"/>'
    +'<input class="inv-svc-amt" type="number" min="0" placeholder="0" value="'+(price||'')+'" oninput="syncRcSvc()" style="width:90px"/>'
    +'<button type="button" class="inv-del" onclick="removeRcRow(\''+id+'\')">➖</button>';
  container.appendChild(div);
  div.querySelector('input').focus();
  syncRcSvc();
}

function removeRcRow(id){
  const el=document.getElementById(id); if(el) el.remove();
  rcRows=rcRows.filter(r=>r!==id);
  syncRcSvc();
}

function syncRcSvc(){
  const names=[];
  let total=0;
  const rows=document.querySelectorAll('#rc_svcRows .inv-svc-row');
  rows.forEach(row=>{
    const name=(row.querySelector('.inv-svc-name')?.value||'').trim();
    const amt=parseFloat(row.querySelector('.inv-svc-amt')?.value)||0;
    if(name) names.push(name);
    total+=amt;
  });
  document.getElementById('rc_sVal').value=names.join(', ');
  const totEl=document.getElementById('rc_svcTotal');
  if(totEl) totEl.textContent='₹'+total.toLocaleString('en-IN');
  // Auto-fill amount field
  const amtEl=document.getElementById('rc_amt');
  if(amtEl&&total>0) amtEl.value=total;
}

function getRcServices(){
  syncRcSvc();
  return document.getElementById('rc_sVal').value.trim();
}

function setPS(s){
  payStatus=s;
  document.getElementById('po1').className='pay-opt'+(s==='paid'?' ok':'');
  document.getElementById('po2').className='pay-opt'+(s==='pending'?' pend':'');
  document.getElementById('pendFlds').style.display=s==='pending'?'block':'none';
}

function addRec(){
  const name=document.getElementById('rc_name').value.trim();
  const mob=document.getElementById('rc_mob').value.trim();
  // Collect service rows with prices
  const svcRows=[];
  let totalFromRows=0;
  document.querySelectorAll('#rc_svcRows .inv-svc-row').forEach(row=>{
    const n=(row.querySelector('.inv-svc-name')?.value||'').trim();
    const p=parseFloat(row.querySelector('.inv-svc-amt')?.value)||0;
    if(n) svcRows.push({name:n,price:p});
    totalFromRows+=p;
  });
  const svc=svcRows.map(s=>s.name).join(', ');
  const amt=totalFromRows||parseFloat(document.getElementById('rc_amt').value)||0;
  if(!name){toast('⚠️ Customer Name भरें','warn');return;}
  if(!mob||mob.length!==10){toast('⚠️ 10-digit Mobile Number डालें','warn');return;}
  if(!svc){toast('⚠️ कम से कम एक Service add करें','warn');return;}
  if(!amt){toast('⚠️ Amount / Price भरें','warn');return;}
  billCtr++;
  const id='PSC-'+String(billCtr).padStart(3,'0');
  const rec={
    id,name,mob,service:svc,svcRows,
    prof:document.getElementById('rc_prof').value,
    amt,ps:payStatus,
    ws:document.getElementById('rc_ws').value,
    date:document.getElementById('rc_date').value,
    time:document.getElementById('rc_time').value,
    notes:document.getElementById('rc_notes').value,
    pd:document.getElementById('rc_pd').value,
    rd:document.getElementById('rc_rd').value,
  };
  recs.unshift(rec);
  logAct('add',curUser.name+' ने '+name+' का record add किया ₹'+amt);
  renderAll(); updateBadge(); saveData();
  toast('✅ Record save हो गया!','ok');
  clearForm();
  go('records',null);
}

function clearForm(){
  ['rc_name','rc_mob','rc_amt','rc_notes','rc_pd','rc_rd'].forEach(id=>{const el=document.getElementById(id);if(el)el.value='';});
  setVal('rc_prof',''); setVal('rc_ws','inprogress');
  setPS('paid');
  document.getElementById('rc_svcRows').innerHTML='';
  rcRows=[];
  setVal('rc_sVal','');
  addRcRow();
  const now=new Date();
  setVal('rc_date',now.toISOString().split('T')[0]);
  setVal('rc_time',now.toTimeString().split(':').slice(0,2).join(':'));
}

// ════════════════════════════════════════
// VIEW / EDIT / UPDATE
// ════════════════════════════════════════
function rRow(l,v){return `<div style="background:var(--bg);border-radius:8px;padding:9px 12px;margin-bottom:8px"><div style="font-size:10px;font-weight:800;color:var(--muted);text-transform:uppercase;letter-spacing:.5px;margin-bottom:2px">${l}</div><div style="font-size:14px;font-weight:600">${v}</div></div>`;}
function viewRec(id){
  const r=recs.find(x=>x.id===id); if(!r) return;
  document.getElementById('viewBody').innerHTML=`
    <div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(180px,1fr));gap:8px">
      ${rRow('🔖 ID',r.id)}${rRow('👤 Name',r.name)}
      ${rRow('📱 Mobile',r.mob)}${rRow('💰 Amount','₹'+r.amt)}
      ${rRow('💳 Payment',r.ps==='paid'?'✅ Paid':'⏳ Pending')}${rRow('📋 Work',r.ws)}
      ${rRow('📅 Date',r.date)}${rRow('⏰ Time',r.time||'-')}
    </div>
    ${rRow('🔧 Service',r.service)}
    ${r.notes?rRow('📝 Notes',r.notes):''}
    <div style="margin-top:14px;display:flex;gap:8px;flex-wrap:wrap">
      <button class="btn btn-p bsm" onclick="closeM('viewModal');genBill('${r.id}')" style="padding:9px 16px">🧾 Bill</button>
      <button class="btn btn-sec bsm" onclick="waRec('${r.id}')" style="padding:9px 16px">💬 WhatsApp</button>
    </div>`;
  openM('viewModal');
}
function editRec(id){
  const r=recs.find(x=>x.id===id); if(!r) return;
  document.getElementById('editBody').innerHTML=`
    <div class="fg-grid">
      <div class="fg"><label class="f-label">Name</label><input class="f-input" id="ed_n" value="${r.name}"/></div>
      <div class="fg"><label class="f-label">Mobile</label><input class="f-input" id="ed_m" value="${r.mob}"/></div>
      <div class="fg"><label class="f-label">Amount</label><input class="f-input" type="number" id="ed_a" value="${r.amt}"/></div>
      <div class="fg"><label class="f-label">Date</label><input class="f-input" type="date" id="ed_d" value="${r.date}"/></div>
      <div class="fg"><label class="f-label">Work Status</label>
        <select class="f-select" id="ed_ws">
          <option value="pending" ${r.ws==='pending'?'selected':''}>⏳ Pending</option>
          <option value="inprogress" ${r.ws==='inprogress'?'selected':''}>🔄 In Progress</option>
          <option value="completed" ${r.ws==='completed'?'selected':''}>✅ Completed</option>
        </select>
      </div>
      <div class="fg"><label class="f-label">Payment</label>
        <select class="f-select" id="ed_ps">
          <option value="paid" ${r.ps==='paid'?'selected':''}>✅ Paid</option>
          <option value="pending" ${r.ps==='pending'?'selected':''}>⏳ Pending</option>
        </select>
      </div>
    </div>
    <div class="f-actions">
      <button class="btn btn-p" onclick="saveEdit('${r.id}')">💾 Save</button>
      <button class="btn btn-sec" onclick="closeM('editModal')">Cancel</button>
    </div>`;
  openM('editModal');
}
function saveEdit(id){
  const r=recs.find(x=>x.id===id); if(!r) return;
  r.name=document.getElementById('ed_n').value;
  r.mob=document.getElementById('ed_m').value;
  r.amt=parseFloat(document.getElementById('ed_a').value)||r.amt;
  r.date=document.getElementById('ed_d').value;
  r.ws=document.getElementById('ed_ws').value;
  r.ps=document.getElementById('ed_ps').value;
  closeM('editModal');
  logAct('edit',curUser.name+' ने '+r.name+' का record edit किया');
  renderAll(); updateBadge(); saveData();
  toast('✅ Record update हुआ!','ok');
}
function updAmt(id){
  const r=recs.find(x=>x.id===id); if(!r) return;
  const v=prompt('New Amount: (Current ₹'+r.amt+')');
  if(v!==null&&!isNaN(parseFloat(v))){
    r.amt=parseFloat(v);
    logAct('pay',curUser.name+' ने '+r.name+' amount update ₹'+r.amt);
    renderAll(); saveData(); toast('💰 Amount update!','ok');
  }
}
function updSt(id){
  const r=recs.find(x=>x.id===id); if(!r) return;
  const opts=['pending','inprogress','completed'];
  r.ws=opts[(opts.indexOf(r.ws)+1)%3];
  logAct('edit',curUser.name+' ने '+r.name+' status: '+r.ws);
  renderAll(); saveData(); toast('🔄 Status: '+r.ws,'ok');
}

// ════════════════════════════════════════
// DELETE WITH PIN
// ════════════════════════════════════════
function delRec(id){pinAction='del';pinTarget=id;pinStr='';updPinDots();document.getElementById('pinErr').textContent='';openM('pinModal');}
function pk(k){
  if(k==='c') pinStr='';
  else if(k==='b') pinStr=pinStr.slice(0,-1);
  else if(pinStr.length<6) pinStr+=k;
  updPinDots();
  if(pinStr.length===6){
    setTimeout(()=>{
      if(pinStr===PIN){
        closeM('pinModal');
        if(pinAction==='del'){
          const r=recs.find(x=>x.id===pinTarget);
          if(r){logAct('del',curUser.name+' ने '+r.name+' delete किया');}
          recs=recs.filter(x=>x.id!==pinTarget);
          renderAll(); updateBadge(); saveData();
          toast('🗑️ Record delete!','err');
        }
      } else {
        document.getElementById('pinErr').textContent='❌ गलत PIN!';
        pinStr=''; updPinDots();
        document.querySelector('#pinModal .modal').style.animation='shake .4s ease';
        setTimeout(()=>document.querySelector('#pinModal .modal').style.animation='',500);
      }
    },150);
  }
}
function updPinDots(){
  document.querySelectorAll('.pin-dot').forEach((d,i)=>d.classList.toggle('on',i<pinStr.length));
}

// ════════════════════════════════════════
// INVOICE SYSTEM
// ════════════════════════════════════════
let invRows=[];
let invCtr=0;
let invImgs={logo:'',qr:'',sig:'',stamp:''};

function uploadImg(type,input){
  const file=input.files[0]; if(!file) return;
  const reader=new FileReader();
  reader.onload=e=>{
    invImgs[type]=e.target.result;
    const img=document.getElementById(type+'PreviewImg');
    const prompt=document.getElementById(type+'UploadPrompt');
    if(img){img.src=e.target.result;img.style.display='block';}
    if(prompt) prompt.style.display='none';
    toast('✅ '+type+' uploaded!','ok');
  };
  reader.readAsDataURL(file);
}

function autoInvNo(){
  invCtr++;
  setVal('inv_no','INV-'+String(invCtr).padStart(4,'0'));
}

function addInvRow(svc='',amt=''){
  const id='row_'+Date.now()+'_'+Math.random().toString(36).slice(2,6);
  invRows.push({id});
  const container=document.getElementById('inv_svcRows');
  const div=document.createElement('div');
  div.className='inv-svc-row';
  div.id=id;
  div.innerHTML=`
    <input class="inv-svc-name" placeholder="Service name..." value="${svc}" oninput="calcInvTotal()" style="flex:1"/>
    <span style="color:var(--muted);font-weight:700;flex-shrink:0">₹</span>
    <input class="inv-svc-amt" type="number" min="0" placeholder="0" value="${amt}" oninput="calcInvTotal()"/>
    <button class="inv-del" onclick="removeInvRow('${id}')">➖</button>`;
  container.appendChild(div);
  calcInvTotal();
}

function removeInvRow(id){
  const el=document.getElementById(id); if(el) el.remove();
  invRows=invRows.filter(r=>r.id!==id);
  calcInvTotal();
}

function calcInvTotal(){
  const amts=document.querySelectorAll('.inv-svc-amt');
  let total=0;
  amts.forEach(a=>total+=parseFloat(a.value)||0);
  document.getElementById('inv_total').textContent='₹'+total.toLocaleString('en-IN');
  calcInvPay(total);
}

function calcInvPay(total){
  if(total===undefined){
    const amts=document.querySelectorAll('.inv-svc-amt');
    total=0; amts.forEach(a=>total+=parseFloat(a.value)||0);
  }
  const paid=parseFloat(document.getElementById('inv_paid').value)||0;
  const rem=Math.max(0,total-paid);
  document.getElementById('inv_rem').textContent='₹'+rem.toLocaleString('en-IN');
  document.getElementById('inv_rem').style.color=rem>0?'var(--err)':'var(--ok)';
}

function getInvData(){
  const rows=[];
  document.querySelectorAll('.inv-svc-row').forEach(row=>{
    const name=row.querySelector('.inv-svc-name')?.value.trim()||'';
    const amt=parseFloat(row.querySelector('.inv-svc-amt')?.value)||0;
    if(name||amt) rows.push({name:name||'—',amt});
  });
  const total=rows.reduce((a,r)=>a+r.amt,0);
  const paid=parseFloat(document.getElementById('inv_paid').value)||0;
  return {
    name:document.getElementById('inv_name').value||'—',
    mob:document.getElementById('inv_mob').value||'—',
    date:document.getElementById('inv_date').value||new Date().toISOString().split('T')[0],
    invNo:document.getElementById('inv_no').value||'INV-0001',
    rows, total, paid, rem:Math.max(0,total-paid),
    logo:invImgs.logo, qr:invImgs.qr, sig:invImgs.sig, stamp:invImgs.stamp
  };
}

function fmtDate(d){
  if(!d) return '—';
  const [y,m,dy]=d.split('-');
  return (dy||'??')+'-'+(m||'??')+'-'+(y||'??');
}

function buildInvHTML(d){
  const logoEl=d.logo?`<img class="inv-doc-logo" src="${d.logo}"/>`:`<div style="width:60px;height:60px;background:linear-gradient(135deg,#0f2247,#2356b8);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:28px;color:#fff">🏛️</div>`;
  const svcRows=d.rows.length?d.rows.map((r,i)=>`<tr><td>${i+1}. ${r.name}</td><td style="text-align:right;font-weight:700;color:#1a3a6e">₹${r.amt.toLocaleString('en-IN')}</td></tr>`).join(''):`<tr><td colspan="2" style="text-align:center;color:#94a3b8">कोई service नहीं</td></tr>`;
  const qrEl=d.qr?`<img class="inv-doc-qr" src="${d.qr}"/>`:'';
  const sigEl=d.sig?`<div style="text-align:right"><img class="inv-doc-sig" src="${d.sig}"/><div style="font-size:11px;color:#64748b;margin-top:3px">Signature</div></div>`:'';
  const stampEl=d.stamp?`<img src="${d.stamp}" style="height:40px;object-fit:contain"/>`:'';
  const psColor=d.rem>0?'#ef4444':'#10b981';
  const psText=d.rem>0?'PENDING':'PAID';
  return `<div class="inv-doc" id="invDocPrint">
    <div class="inv-doc-head">
      <div style="display:flex;align-items:flex-start;gap:12px">
        ${logoEl}
        <div>
          <div class="inv-doc-shopname">Prince Soni CSC Centre</div>
          <div class="inv-doc-meta">CSC ID: 447655530012<br>📱 9729315282<br>📍 Baniyani, Rohtak</div>
        </div>
      </div>
      <div class="inv-doc-invno">
        <div class="inv-doc-invbig">Invoice</div>
        <div class="inv-doc-num">${d.invNo}</div>
        <div style="font-size:11px;color:#64748b;margin-top:4px">📅 ${fmtDate(d.date)}</div>
        <div style="margin-top:6px;background:${psColor};color:#fff;padding:3px 10px;border-radius:5px;font-size:11px;font-weight:800;text-align:center">${psText}</div>
      </div>
    </div>
    <div class="inv-doc-cust">
      <div>
        <div style="font-size:10px;font-weight:800;text-transform:uppercase;letter-spacing:.5px;color:#64748b;margin-bottom:3px">Bill To</div>
        <div class="inv-doc-cust-name">${d.name}</div>
        <div class="inv-doc-cust-mob">📱 ${d.mob}</div>
      </div>
      <div style="text-align:right">
        <div style="font-size:10px;font-weight:800;text-transform:uppercase;letter-spacing:.5px;color:#64748b;margin-bottom:3px">Invoice Date</div>
        <div style="font-size:13px;font-weight:700">${fmtDate(d.date)}</div>
      </div>
    </div>
    <table class="inv-tbl">
      <thead><tr><th>#  Service Name</th><th style="text-align:right">Amount</th></tr></thead>
      <tbody>${svcRows}</tbody>
    </table>
    <div class="inv-tot-box">
      <div class="inv-tot-row"><span style="color:#64748b">Total Amount</span><span style="font-weight:800">₹${d.total.toLocaleString('en-IN')}</span></div>
      <div class="inv-tot-row"><span style="color:#10b981">Paid Amount</span><span style="color:#10b981;font-weight:800">₹${d.paid.toLocaleString('en-IN')}</span></div>
      <div class="inv-tot-row" style="border-top:1px dashed #e2e8f0;padding-top:7px">
        <span style="color:${psColor}">Remaining</span><span style="color:${psColor};font-weight:800">₹${d.rem.toLocaleString('en-IN')}</span>
      </div>
    </div>
    <div class="inv-doc-foot">
      <div style="display:flex;align-items:flex-end;gap:12px">${qrEl}${stampEl}</div>
      ${sigEl}
    </div>
    <div class="inv-doc-thankyou">🙏 धन्यवाद! आपकी सेवा करके हमें खुशी हुई &nbsp;|&nbsp; Prince Soni CSC Centre &nbsp;|&nbsp; 📱 9729315282</div>
  </div>`;
}

function prevInv(){
  const d=getInvData();
  document.getElementById('invPrevBox').innerHTML=buildInvHTML(d);
  toast('👁️ Preview updated!','ok');
}

function printInv(){
  const d=getInvData();
  if(!d.name||d.name==='—'){toast('⚠️ Customer Name भरें','warn');return;}
  if(!d.rows.length){toast('⚠️ कम से कम एक Service add करें','warn');return;}
  const html=buildInvHTML(d);
  const css=[
    "*{margin:0;padding:0;box-sizing:border-box}",
    "body{font-family:'Baloo 2',sans-serif;background:#fff;display:flex;justify-content:center;padding:10px}",
    ".inv-doc{background:#fff;padding:24px;max-width:680px;width:100%;font-size:13px}",
    ".inv-doc-head{display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:18px;padding-bottom:16px;border-bottom:2px solid #e2e8f0;gap:10px}",
    ".inv-doc-logo{width:60px;height:60px;border-radius:10px;object-fit:contain;border:1px solid #e2e8f0}",
    ".inv-doc-shopname{font-size:18px;font-weight:800;color:#0f2247;line-height:1.2}",
    ".inv-doc-meta{font-size:11px;color:#64748b;margin-top:3px;line-height:1.8}",
    ".inv-doc-invno{text-align:right;flex-shrink:0}",
    ".inv-doc-num{font-size:17px;font-weight:800;color:#1a3a6e;font-family:monospace}",
    ".inv-doc-cust{background:#f8faff;border-radius:10px;padding:12px 14px;margin-bottom:14px;display:flex;justify-content:space-between;flex-wrap:wrap;gap:10px}",
    ".inv-doc-cust-name{font-size:15px;font-weight:800;color:#0f2247}",
    ".inv-doc-cust-mob{font-size:12px;color:#64748b;margin-top:2px}",
    "table.inv-tbl{width:100%;border-collapse:collapse;margin-bottom:14px}",
    "table.inv-tbl thead tr{background:#0f2247}",
    "table.inv-tbl thead th{color:#fff;padding:9px 12px;text-align:left;font-size:11px;font-weight:800;text-transform:uppercase}",
    "table.inv-tbl thead th:last-child{text-align:right}",
    "table.inv-tbl tbody tr{border-bottom:1px solid #f1f5f9}",
    "table.inv-tbl tbody td{padding:9px 12px;font-size:13px}",
    "table.inv-tbl tbody td:last-child{text-align:right;font-weight:700;color:#1a3a6e}",
    ".inv-tot-box{background:#f8faff;border-radius:10px;padding:12px 14px;display:flex;flex-direction:column;gap:7px;margin-bottom:14px}",
    ".inv-tot-row{display:flex;justify-content:space-between;font-size:13px}",
    ".inv-tot-final{background:#0f2247;color:#fff;border-radius:9px;padding:10px 14px;display:flex;justify-content:space-between;font-size:15px;font-weight:800}",
    ".inv-doc-foot{display:flex;justify-content:space-between;align-items:flex-end;margin-top:14px;padding-top:14px;border-top:2px dashed #e2e8f0;flex-wrap:wrap;gap:10px}",
    ".inv-doc-qr{width:65px;height:65px;object-fit:contain;border-radius:8px;border:1px solid #e2e8f0}",
    ".inv-doc-sig{height:44px;object-fit:contain}",
    ".inv-doc-thankyou{font-size:12px;color:#64748b;text-align:center;margin-top:10px;padding-top:10px;border-top:1px solid #f1f5f9}",
    "@page{size:A4;margin:10mm}",
    "@media print{body{padding:0}}"
  ].join("\n");
  const fileName = 'Invoice_'+d.invNo+'_'+d.name.replace(/\s+/g,'_')+'.pdf';
  const fullHTML = '<!DOCTYPE html><html><head><meta charset="UTF-8">'
    + '<title>'+fileName+'</title>'
    + '<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@400;600;700;800&display=swap" rel="stylesheet">'
    + '<style>' + css + '</style>'
    + '</head><body>' + html
    + '<script>window.onload=function(){setTimeout(function(){window.print();},600);}<' + '/script>'
    + '</body></html>';
  const blob = new Blob([fullHTML], {type:'text/html'});
  const url = URL.createObjectURL(blob);
  const win = window.open(url,'_blank');
  if(!win){
    // Popup blocked — fallback: direct download
    const a=document.createElement('a');
    a.href=url; a.download=fileName; a.click();
    toast('⬇️ Download हो रही है...','ok');
  } else {
    toast('🖨️ Print/Save dialog खुल रहा है...','ok');
  }
  setTimeout(()=>URL.revokeObjectURL(url), 30000);
}

function waInv(){
  const d=getInvData();
  const svcList=d.rows.map((r,i)=>`${i+1}. ${r.name}: ₹${r.amt}`).join('\n');
  window.open('https://wa.me/?text='+encodeURIComponent(
    `🏛️ *Prince Soni CSC Centre*\nCSC ID: 447655530012 | 📱 9729315282\nBaniyani, Rohtak\n\n📄 *Invoice: ${d.invNo}*\n📅 Date: ${fmtDate(d.date)}\n\n👤 *${d.name}*\n📱 ${d.mob}\n\n🔧 *Services:*\n${svcList||'—'}\n\n💰 Total: ₹${d.total.toLocaleString('en-IN')}\n✅ Paid: ₹${d.paid.toLocaleString('en-IN')}\n${d.rem>0?'⚠️ Remaining: ₹'+d.rem.toLocaleString('en-IN'):'✅ Fully Paid'}\n\nधन्यवाद 🙏`
  ),'_blank');
}

function clearInv(){
  setVal('inv_name','');setVal('inv_mob','');setVal('inv_paid','');
  setVal('inv_no','');
  document.getElementById('inv_svcRows').innerHTML='';
  invRows=[];invImgs={logo:'',qr:'',sig:'',stamp:''};
  ['logo','qr','sig','stamp'].forEach(t=>{
    const img=document.getElementById(t+'PreviewImg');
    const prompt=document.getElementById(t+'UploadPrompt');
    if(img){img.src='';img.style.display='none';}
    if(prompt) prompt.style.display='flex';
  });
  document.getElementById('inv_total').textContent='₹0';
  document.getElementById('inv_rem').textContent='₹0';
  document.getElementById('invPrevBox').innerHTML='<div style="text-align:center;padding:40px;color:var(--muted)"><div style="font-size:48px;margin-bottom:10px">🧾</div><p style="font-size:14px">Details भरें और Preview देखें</p></div>';
  toast('🗑️ Cleared!','ok');
}

function genBill(id){
  const r=recs.find(x=>x.id===id); if(!r) return;
  clearInv();
  setVal('inv_name',r.name);setVal('inv_mob',r.mob);setVal('inv_date',r.date);
  autoInvNo();
  if(r.svcRows&&r.svcRows.length){
    r.svcRows.forEach(s=>addInvRow(s.name,s.price||0));
  } else {
    r.service.split(', ').filter(Boolean).forEach(s=>addInvRow(s,r.amt||0));
  }
  if(r.ps==='paid') setVal('inv_paid',r.amt);
  calcInvTotal();
  // Auto print directly
  printInv();
}

function waRec(id){
  const r=recs.find(x=>x.id===id); if(!r) return;
  window.open('https://wa.me/?text='+encodeURIComponent(`🏛️ *Prince Soni CSC Centre*\n\n👤 ${r.name}\n📱 ${r.mob}\n🔧 ${r.service}\n💰 ₹${r.amt}\n💳 ${r.ps==='paid'?'✅ Paid':'⏳ Pending'}\n\nधन्यवाद 🙏`),'_blank');
}

// ════════════════════════════════════════
// PENDING
// ════════════════════════════════════════
function renderPending(){
  const pend=recs.filter(r=>r.ps==='pending');
  document.getElementById('pendList').innerHTML=pend.length?pend.map(r=>`
    <div class="pend-card">
      <span style="font-size:22px">⚠️</span>
      <div class="pend-info">
        <div class="pend-name">${r.name}</div>
        <div class="pend-det">📱 ${r.mob} • 🔧 ${r.service.length>25?r.service.slice(0,25)+'...':r.service}</div>
        ${r.pd?`<div class="pend-det">📅 Due: ${r.pd}</div>`:''}
      </div>
      <div style="text-align:right">
        <div class="pend-amt">₹${r.amt}</div>
        <button class="bsm bsm-ok" style="margin-top:6px" onclick="markPaid('${r.id}')">✅ Mark Paid</button>
      </div>
    </div>`).join(''):'<div class="card" style="text-align:center;padding:40px;color:var(--muted)"><div style="font-size:44px;margin-bottom:10px">🎉</div><p>कोई pending work नहीं!</p></div>';
}
function markPaid(id){
  const r=recs.find(x=>x.id===id); if(!r) return;
  r.ps='paid';
  logAct('pay',curUser.name+' ने '+r.name+' mark paid ₹'+r.amt);
  renderAll(); updateBadge(); saveData();
  toast('✅ Mark Paid!','ok');
}

// ════════════════════════════════════════
// STAFF
// ════════════════════════════════════════
function renderStaff(){
  document.getElementById('staffGrid').innerHTML=staffList.map(s=>`
    <div class="staff-card">
      <div class="st-av">${s.name.charAt(0)}</div>
      <div class="st-name">${s.name}</div>
      <div class="st-id">${s.id}</div>
      <div class="st-meta">
        <div class="st-row">📱 <b>${s.mob}</b></div>
        <div class="st-row">💼 <b>${s.prof}</b></div>
        <div class="st-row">👤 <b>${s.user}</b></div>
        <div class="st-row">🔑 <b>${s.pw}</b></div>
        <div class="st-row">📅 Joined: <b>${s.join}</b></div>
      </div>
      <div style="display:flex;gap:8px;margin-top:12px">
        <button class="bsm bsm-p" style="flex:1" onclick="toast('Edit: Coming soon!','warn')">✏️ Edit</button>
        <button class="bsm bsm-err" style="flex:1" onclick="delStaff('${s.id}')">🗑️ Delete</button>
      </div>
    </div>`).join('');
}
function showAddStaff(){genPW();openM('staffModal');}
function genPW(){
  const c='ABCDEFGHJKMNPQRSTWXYZabcdefghjkmnpqrstwxyz23456789';
  let p='';for(let i=0;i<8;i++)p+=c[Math.floor(Math.random()*c.length)];
  setVal('st_pw','Staff@'+p);
}
function addStaff(){
  const n=document.getElementById('st_n').value.trim();
  const m=document.getElementById('st_m').value.trim();
  if(!n||!m){toast('⚠️ Name और Mobile required','warn');return;}
  const id='STAFF'+String(100+staffList.length+1);
  staffList.push({id,name:n,mob:m,prof:document.getElementById('st_p').value,user:document.getElementById('st_u').value||n.toLowerCase().replace(' ',''),pw:document.getElementById('st_pw').value,join:new Date().toISOString().split('T')[0]});
  closeM('staffModal');renderStaff(); saveData();
  logAct('add',curUser.name+' ने staff add किया: '+n);
  toast('✅ Staff add! ID: '+id,'ok');
}
function delStaff(id){
  if(confirm('Delete this staff?')){
    staffList=staffList.filter(s=>s.id!==id);renderStaff();saveData();toast('🗑️ Staff deleted','err');
  }
}

// ════════════════════════════════════════
// ACTIVITY LOG
// ════════════════════════════════════════
function logAct(type,txt){
  actLog.unshift({type,txt,time:'अभी'});
  if(actLog.length>100) actLog=actLog.slice(0,100);
  lsSet('actLog',actLog);
  renderActLog();
}
function renderActLog(){
  const icos={add:'➕',del:'🗑️',edit:'✏️',pay:'💰'};
  const bgs={add:'#d1fae5',del:'#fee2e2',edit:'#dbeafe',pay:'#fef3c7'};
  document.getElementById('actLog').innerHTML=actLog.map(a=>`
    <div class="log-item">
      <div class="log-ico" style="background:${bgs[a.type]||'#f0f4ff'}">${icos[a.type]||'📋'}</div>
      <div class="log-txt">${a.txt}</div>
      <div class="log-time">${a.time}</div>
    </div>`).join('');
}

// ════════════════════════════════════════
// EXPORT
// ════════════════════════════════════════
function renderExp(){
  const paid=recs.filter(r=>r.ps==='paid');
  const pend=recs.filter(r=>r.ps==='pending');
  const items=[
    {ico:'📋',val:recs.length,lbl:'Total Records',c:'c1'},
    {ico:'✅',val:paid.length,lbl:'Paid Records',c:'c2'},
    {ico:'⏳',val:pend.length,lbl:'Pending',c:'c4'},
    {ico:'💰',val:'₹'+paid.reduce((a,r)=>a+r.amt,0).toLocaleString('en-IN'),lbl:'Total Income',c:'c3'},
    {ico:'📅',val:recs.filter(r=>r.date.startsWith('2026-03')).length,lbl:'This Month',c:'c5'},
    {ico:'👥',val:staffList.length,lbl:'Total Staff',c:'c6'},
  ];
  document.getElementById('expStats').innerHTML=items.map(s=>`<div class="stat ${s.c}" style="cursor:default"><div class="stat-ico">${s.ico}</div><div class="stat-val">${s.val}</div><div class="stat-lbl">${s.lbl}</div></div>`).join('');
}
function exportPDF(){toast('📄 Print dialog खुलेगा...','ok');setTimeout(()=>window.print(),400);}
function exportExcel(){toast('📊 Excel export coming soon!','warn');}
function dlBackup(){
  const d=JSON.stringify({recs,staffList,actLog,adminPW,billCtr},null,2);
  const a=document.createElement('a');
  a.href=URL.createObjectURL(new Blob([d],{type:'application/json'}));
  a.download='CSC_Backup_'+new Date().toISOString().split('T')[0]+'.json';
  a.click();
  toast('💾 Backup download हो गई!','ok');
}
function importBackup(input){
  const file=input.files[0]; if(!file) return;
  const reader=new FileReader();
  reader.onload=e=>{
    try{
      const d=JSON.parse(e.target.result);
      if(d.recs) recs=d.recs;
      if(d.staffList) staffList=d.staffList;
      if(d.actLog) actLog=d.actLog;
      if(d.adminPW) adminPW=d.adminPW;
      if(d.billCtr) billCtr=d.billCtr;
      saveData();
      renderAll(); updateBadge();
      toast('✅ Backup Import! '+recs.length+' records loaded','ok');
    }catch(err){
      toast('❌ Invalid backup file!','err');
    }
  };
  reader.readAsText(file);
  input.value='';
}

// ════════════════════════════════════════
// BADGE
// ════════════════════════════════════════
function updateBadge(){
  const n=recs.filter(r=>r.ps==='pending').length;
  ['sBadge','bnBadge'].forEach(id=>{const el=document.getElementById(id);if(el){el.textContent=n;el.style.display=n>0?'block':'none';}});
}

// ════════════════════════════════════════
// GLOBAL SEARCH
// ════════════════════════════════════════
function gSearch(q){
  if(!q) return;
  go('records',null);
  renderRecs(recs.filter(r=>r.name.toLowerCase().includes(q.toLowerCase())||r.mob.includes(q)||r.service.toLowerCase().includes(q.toLowerCase())));
}

// ════════════════════════════════════════
// FORGOT PASSWORD
// ════════════════════════════════════════
function showFP(){fpStep=1;updFPSteps();document.getElementById('fp1').style.display='block';document.getElementById('fp2').style.display='none';document.getElementById('fp3').style.display='none';openM('fpModal');}
function updFPSteps(){
  ['sp1','sp2','sp3'].forEach((id,i)=>{
    const el=document.getElementById(id);
    if(i+1<fpStep) el.className='step done',el.textContent='✓';
    else if(i+1===fpStep) el.className='step now',el.textContent=i+1;
    else el.className='step wait',el.textContent=i+1;
  });
  document.getElementById('sl1').className='step-line'+(fpStep>1?' done':'');
  document.getElementById('sl2').className='step-line'+(fpStep>2?' done':'');
}
function fpN1(){
  const u=document.getElementById('fp_u').value.trim();
  if(!u){toast('Username enter करें','warn');return;}
  if(u!=='Prince'&&!staffList.find(s=>s.user===u)){toast('User नहीं मिला','err');return;}
  fpStep=2; updFPSteps();
  document.getElementById('fp1').style.display='none';
  document.getElementById('fp2').style.display='block';
}
function fpN2(){
  if(document.getElementById('fp_otp').value!=='123456'){toast('गलत OTP','err');return;}
  fpStep=3; updFPSteps();
  document.getElementById('fp2').style.display='none';
  document.getElementById('fp3').style.display='block';
}
function fpReset(){
  const np=document.getElementById('fp_np').value;
  const cp=document.getElementById('fp_cp').value;
  if(!np||np!==cp){toast('Passwords match नहीं','err');return;}
  const u=document.getElementById('fp_u').value;
  if(u==='Prince') adminPW=np;
  else{const s=staffList.find(x=>x.user===u);if(s)s.pw=np;}
  closeM('fpModal'); saveData();
  toast('✅ Password Reset!','ok');
}

// ════════════════════════════════════════
// CHANGE PASSWORD
// ════════════════════════════════════════
function showCP(){
  ['cp_cur','cp_new','cp_cf'].forEach(id=>setVal(id,''));
  document.getElementById('cpErr').style.display='none';
  document.getElementById('cpUser').textContent=curUser.user;
  document.getElementById('cpRole').textContent=curUser.role;
  closeSB(); openM('cpModal');
}
function doCP(){
  const cur=document.getElementById('cp_cur').value;
  const nw=document.getElementById('cp_new').value;
  const cf=document.getElementById('cp_cf').value;
  const err=document.getElementById('cpErr');
  err.style.display='none';
  let ok=curUser.role==='Admin'?(cur===adminPW):(staffList.find(s=>s.user===curUser.user)?.pw===cur);
  if(!cur||!nw||!cf){err.textContent='⚠️ सभी fields भरें';err.style.display='block';return;}
  if(!ok){err.textContent='❌ Current Password गलत';err.style.display='block';return;}
  if(nw.length<6){err.textContent='⚠️ कम से कम 6 characters';err.style.display='block';return;}
  if(nw!==cf){err.textContent='❌ Passwords match नहीं';err.style.display='block';return;}
  if(curUser.role==='Admin') adminPW=nw;
  else{const s=staffList.find(x=>x.user===curUser.user);if(s)s.pw=nw;}
  closeM('cpModal');logAct('edit',curUser.name+' ने password change किया');
  saveData(); toast('✅ Password changed!','ok');
}

// ════════════════════════════════════════
// LOGOUT
// ════════════════════════════════════════
function showLogout(){document.getElementById('logUser').textContent=curUser.name;closeSB();openM('logoutModal');}
function doLogout(){
  saveData(); // logout se pehle data save karo
  closeM('logoutModal');
  selSvc_rc=[];selSvc_bill=[];
  rcRows=[];invRows=[];
  curUser={};
  document.getElementById('app').style.display='none';
  document.getElementById('loginPage').style.display='flex';
  setVal('lu','');setVal('lp','');
  document.getElementById('loginErr').style.display='none';
  setTimeout(()=>toast('👋 Logout हो गए! Data safe है ✅','ok'),200);
}

// ════════════════════════════════════════
// REMINDER
// ════════════════════════════════════════
function remLater(){document.getElementById('remPop').style.display='none';toast('🔔 Reminder Later','warn');}
function remPaid(){
  document.getElementById('remPop').style.display='none';
  const pend=recs.filter(r=>r.ps==='pending');
  if(pend.length) markPaid(pend[0].id);
}

// ════════════════════════════════════════
// MODAL HELPERS
// ════════════════════════════════════════
function openM(id){document.getElementById(id).classList.add('on');}
function closeM(id){document.getElementById(id).classList.remove('on');}

// ════════════════════════════════════════
// TOAST
// ════════════════════════════════════════
function toast(msg,type='ok'){
  const t=document.getElementById('toastEl');
  t.textContent=msg; t.className='toast '+type+' show';
  clearTimeout(t._t);
  t._t=setTimeout(()=>t.classList.remove('show'),3000);
}

// ════════════════════════════════════════
// OUTSIDE CLICK
// ════════════════════════════════════════
document.addEventListener('click',e=>{
  if(!e.target.closest('.tb-notif')&&!e.target.closest('#notifPop')) document.getElementById('notifPop').style.display='none';
  if(!e.target.closest('.ms-box')&&!e.target.closest('.ms-panel')){
    document.querySelectorAll('.ms-panel.open').forEach(p=>{
      p.classList.remove('open');
      p.previousElementSibling?.classList.remove('open');
    });
  }
  if(e.target.classList.contains('overlay')) document.querySelectorAll('.overlay.on').forEach(o=>o.classList.remove('on'));
});
</script>
</body></html>
