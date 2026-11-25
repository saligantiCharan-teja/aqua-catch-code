# aqua-catch-code

AquaCatch (code only)
100%
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#087da5">
  <title>AquaCatch — Fisheries Catch Management</title>
  <style>
/* AquaCatch's colors, spacing, and motion are kept here for easy changes. */
:root {
  color-scheme: light;
  --ink: #14364b;
  --muted-ink: #67808d;
  --ocean: #087da5;
  --deep-ocean: #07546f;
  --sky: #eaf7fb;
  --line: #dce9ee;
  --paper: #ffffff;
  --page: #f5fafb;
  --coral: #f07c68;
  --mint: #dff4ea;
  --shadow: 0 12px 32px rgb(19 74 99 / 8%);
  font-family: "Trebuchet MS", Arial, sans-serif;
  color: var(--ink);
  background: var(--page);
  font-synthesis: none;
  text-rendering: optimizeLegibility;
}
* { box-sizing: border-box; }
body { min-width: 320px; margin: 0; background: var(--page); }
a { color: inherit; }
.site-header { min-height: 76px; display: flex; align-items: center; justify-content: space-between; gap: 24px; padding: 0 max(24px, calc((100vw - 1180px) / 2)); background: var(--paper); border-bottom: 1px solid var(--line); }
.brand { display: inline-flex; align-items: center; gap: 10px; color: var(--deep-ocean); font-size: 21px; font-weight: 800; text-decoration: none; }
.brand-mark { display: grid; width: 34px; height: 34px; place-items: center; border-radius: 11px; background: var(--ocean); color: white; font-size: 26px; line-height: 1; }
.main-nav { display: flex; align-items: center; gap: 8px; }
.nav-link { padding: 10px 14px; border-radius: 8px; color: var(--muted-ink); font-size: 14px; font-weight: 700; text-decoration: none; transition: background .18s ease, color .18s ease; }
.nav-link:hover, .nav-link.active { background: var(--sky); color: var(--deep-ocean); }
.page-shell { width: min(1180px, calc(100% - 48px)); min-height: calc(100vh - 145px); margin: 0 auto; padding: 34px 0 56px; }
.page-view[hidden] { display: none; }
.ocean-banner { position: relative; min-height: 260px; overflow: hidden; display: flex; align-items: center; padding: 35px 42px; border-radius: 14px; background: linear-gradient(110deg, #e6f7fb 0%, #d4f0f7 53%, #b9e5f0 100%); }
.banner-copy { position: relative; z-index: 2; max-width: 460px; padding-bottom: 10px; }
.eyebrow { margin: 0 0 10px; color: var(--ocean); font-size: 11px; font-weight: 800; letter-spacing: 1.2px; }
h1, h2, p { margin-top: 0; }
.banner-copy h1 { max-width: 420px; margin: 0 0 12px; color: var(--deep-ocean); font-size: clamp(28px, 3vw, 39px); line-height: 1.12; }
.banner-copy > p:last-child { max-width: 360px; margin: 0; color: #537786; font-size: 15px; line-height: 1.6; }
.ocean-art { position: absolute; right: 0; bottom: 0; width: min(57%, 630px); height: 100%; overflow: visible; }
.sun { fill: #ffe29b; }
.distant-wave { fill: #99d5e4; }
.wave-back { fill: #42b4cf; animation: wave-drift 7s ease-in-out infinite alternate; }
.wave-front { fill: #087da5; animation: wave-drift 5.2s ease-in-out infinite alternate-reverse; }
.foam { fill: none; stroke: #d7f4f7; stroke-width: 3; stroke-linecap: round; opacity: .8; }
.mast { stroke: #235568; stroke-width: 5; stroke-linecap: round; }
.sail { fill: #fffdf3; stroke: #d4e5e8; stroke-width: 2; }
.sail-light { fill: #f4fbf9; }
.hull { fill: #e9775f; stroke: #b85646; stroke-width: 2; }
.boat-window { fill: #fff3cf; }
.boat { transform-origin: 295px 144px; animation: boat-rock 3.2s ease-in-out infinite; }
@keyframes wave-drift { from { transform: translateX(-5px); } to { transform: translateX(9px); } }
@keyframes boat-rock { 0%, 100% { transform: rotate(-1deg) translateY(1px); } 50% { transform: rotate(1.2deg) translateY(-3px); } }
.section-heading { display: flex; align-items: end; justify-content: space-between; gap: 16px; margin: 35px 0 17px; }
.section-heading .eyebrow { margin-bottom: 5px; }
.section-heading h2 { margin: 0; color: var(--ink); font-size: 22px; }
.text-link { color: var(--ocean); font-size: 13px; font-weight: 800; text-decoration: none; white-space: nowrap; }
.text-link:hover { color: var(--deep-ocean); text-decoration: underline; }
.summary-grid { display: grid; grid-template-columns: repeat(4, minmax(0, 1fr)); gap: 16px; }
.summary-card { min-height: 144px; padding: 19px 20px; border: 1px solid var(--line); border-radius: 12px; background: var(--paper); box-shadow: var(--shadow); }
.card-icon { display: grid; width: 34px; height: 34px; margin-bottom: 14px; place-items: center; border-radius: 10px; background: var(--sky); color: var(--ocean); font-size: 20px; font-weight: 800; }
.card-blue .card-icon { background: #e8effd; color: #4d70b6; }
.card-coral .card-icon { background: #fff0ed; color: var(--coral); }
.card-green .card-icon { background: var(--mint); color: #348467; }
.summary-card p { margin: 0 0 6px; color: var(--muted-ink); font-size: 13px; }
.summary-card strong { display: block; overflow-wrap: anywhere; color: var(--ink); font-size: 23px; line-height: 1.2; }
.recent-heading { margin-top: 36px; }
.table-wrap { overflow-x: auto; border: 1px solid var(--line); border-radius: 12px; background: var(--paper); box-shadow: var(--shadow); }
table { width: 100%; border-collapse: collapse; text-align: left; }
th, td { padding: 14px 16px; border-bottom: 1px solid #edf2f4; white-space: nowrap; }
th { background: #f8fbfc; color: var(--muted-ink); font-size: 11px; font-weight: 800; text-transform: uppercase; letter-spacing: .7px; }
td { color: #37596a; font-size: 13px; }
tbody tr:last-child td { border-bottom: 0; }
.fish-pill { display: inline-flex; align-items: center; padding: 5px 9px; border-radius: 20px; background: var(--sky); color: var(--deep-ocean); font-size: 12px; font-weight: 700; }
.empty-state { margin: 0; padding: 28px 20px; color: var(--muted-ink); text-align: center; font-size: 14px; }
.page-intro { margin: 16px 0 26px; }
.page-intro .eyebrow { margin-bottom: 8px; }
.page-intro h1 { margin: 0 0 8px; color: var(--deep-ocean); font-size: 32px; }
.page-intro > p:last-child, .records-intro p:last-child { margin: 0; color: var(--muted-ink); font-size: 14px; }
.catch-form { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 20px; padding: 27px; border: 1px solid var(--line); border-radius: 12px; background: var(--paper); box-shadow: var(--shadow); }
.catch-form label { display: flex; flex-direction: column; gap: 8px; color: #36586a; font-size: 13px; font-weight: 700; }
.catch-form input, .catch-form select, .search-box input { width: 100%; min-height: 45px; padding: 0 13px; border: 1px solid #cadce3; border-radius: 7px; outline: none; background: #fff; color: var(--ink); font: inherit; font-size: 14px; }
.catch-form input:focus, .catch-form select:focus, .search-box:focus-within { border-color: var(--ocean); box-shadow: 0 0 0 3px rgb(8 125 165 / 13%); }
.catch-form input::placeholder, .search-box input::placeholder { color: #9aadb6; }
.wide-field { grid-column: 1 / -1; }
.form-actions { display: flex; align-items: center; justify-content: space-between; gap: 14px; padding-top: 2px; }
.form-message { min-height: 20px; margin: 0; color: #287657; font-size: 13px; }
.form-message.error { color: #b44e40; }
.primary-button { min-height: 44px; padding: 0 18px; border: 0; border-radius: 7px; background: var(--ocean); color: #fff; font: inherit; font-size: 14px; font-weight: 800; cursor: pointer; transition: background .18s ease, transform .18s ease; }
.primary-button:hover { transform: translateY(-1px); background: var(--deep-ocean); }
.records-intro { display: flex; align-items: end; justify-content: space-between; gap: 24px; }
.search-box { position: relative; display: block; width: min(340px, 100%); border: 1px solid #cadce3; border-radius: 8px; background: var(--paper); }
.search-box input { min-height: 44px; padding-left: 40px; border: 0; background: transparent; }
.search-icon { position: absolute; top: 7px; left: 13px; z-index: 1; color: var(--muted-ink); font-size: 22px; }
.delete-button { border: 1px solid #f1c8c1; border-radius: 6px; padding: 6px 9px; background: #fff8f6; color: #a64d40; font: inherit; font-size: 12px; font-weight: 700; cursor: pointer; }
.delete-button:hover { background: #ffebe7; }
.site-footer { display: flex; justify-content: space-between; gap: 20px; padding: 20px max(24px, calc((100vw - 1180px) / 2)); border-top: 1px solid var(--line); background: var(--paper); color: var(--muted-ink); font-size: 12px; }
.site-footer span:first-child { color: var(--deep-ocean); font-weight: 800; }
.visually-hidden { position: absolute; width: 1px; height: 1px; padding: 0; margin: -1px; overflow: hidden; clip: rect(0, 0, 0, 0); white-space: nowrap; border: 0; }
@media (max-width: 780px) {
  .site-header { min-height: auto; flex-direction: column; align-items: flex-start; gap: 10px; padding: 15px 20px 10px; }
  .main-nav { width: 100%; overflow-x: auto; gap: 4px; }
  .nav-link { padding: 9px 11px; font-size: 13px; }
  .page-shell { width: min(100% - 32px, 600px); padding-top: 20px; }
  .ocean-banner { min-height: 310px; align-items: flex-start; padding: 28px 24px; }
  .banner-copy { max-width: 390px; }
  .banner-copy h1 { max-width: 340px; font-size: 31px; }
  .banner-copy > p:last-child { max-width: 290px; }
  .ocean-art { width: 100%; height: 61%; opacity: .95; }
  .summary-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 11px; }
  .summary-card { min-height: 130px; padding: 15px; }
  .summary-card strong { font-size: 20px; }
  .catch-form { gap: 16px; padding: 19px; }
  .records-intro { align-items: flex-start; flex-direction: column; }
  .search-box { width: 100%; }
  .site-footer { padding: 18px 20px; }
}
@media (max-width: 480px) {
  .page-shell { width: calc(100% - 28px); }
  .ocean-banner { min-height: 320px; padding: 24px 20px; }
  .banner-copy h1 { max-width: 285px; font-size: 28px; }
  .banner-copy > p:last-child { max-width: 250px; font-size: 14px; }
  .ocean-art { width: 115%; height: 58%; right: -25px; }
  .section-heading { align-items: flex-start; }
  .section-heading h2 { font-size: 20px; }
  .text-link { padding-top: 12px; font-size: 12px; }
  .summary-card { min-height: 121px; padding: 13px; }
  .summary-card p { font-size: 12px; }
  .summary-card strong { font-size: 18px; }
  .card-icon { width: 30px; height: 30px; margin-bottom: 11px; }
  .catch-form { grid-template-columns: 1fr; padding: 16px; }
  .wide-field { grid-column: auto; }
  .form-actions { align-items: stretch; flex-direction: column; }
  .primary-button { align-self: flex-end; }
  .page-intro h1 { font-size: 28px; }
  .site-footer { align-items: flex-start; flex-direction: column; gap: 5px; }
}
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { scroll-behavior: auto !important; animation-duration: .01ms !important; animation-iteration-count: 1 !important; transition-duration: .01ms !important; }
}

  </style>
</head>
<body>
  <header class="site-header">
    <a class="brand" href="#dashboard" aria-label="AquaCatch dashboard">
      <span class="brand-mark" aria-hidden="true">≈</span><span>AquaCatch</span>
    </a>
    <nav class="main-nav" aria-label="Main navigation">
      <a class="nav-link active" href="#dashboard" data-view="dashboard">Dashboard</a>
      <a class="nav-link" href="#add-catch" data-view="add-catch">Add Catch</a>
      <a class="nav-link" href="#catch-records" data-view="catch-records">Catch Records</a>
    </nav>
  </header>

  <main class="page-shell">
    <section id="dashboard" class="page-view" aria-labelledby="dashboard-title">
      <div class="ocean-banner" aria-label="Illustration of one fishing boat floating on the ocean">
        <div class="banner-copy">
          <p class="eyebrow">FISHERIES OVERVIEW</p>
          <h1 id="dashboard-title">A clearer view of every catch.</h1>
          <p>Track the day’s landings, trips, and earnings in one place.</p>
        </div>
        <svg class="ocean-art" viewBox="0 0 620 250" role="img" aria-label="One small fishing boat on layered blue waves">
          <circle class="sun" cx="500" cy="54" r="28" />
          <path class="distant-wave" d="M0 146 Q75 126 150 146 T300 146 T450 146 T620 146 V250 H0Z" />
          <path class="wave wave-back" d="M0 165 Q65 145 130 165 T260 165 T390 165 T520 165 T650 165 V250 H0Z" />
          <g class="boat">
            <path class="sail" d="M295 72 L295 137 L252 137Z" />
            <path class="sail sail-light" d="M303 88 L303 137 L339 137Z" />
            <path class="mast" d="M298 66 V143" />
            <path class="hull" d="M235 144 H357 L341 164 H256Z" />
            <path class="boat-window" d="M275 149 H286 V157 H275Z M294 149 H305 V157 H294Z" />
          </g>
          <path class="wave wave-front" d="M0 182 Q80 160 160 182 T320 182 T480 182 T640 182 V250 H0Z" />
          <path class="foam" d="M15 197 Q52 184 89 197 T163 197 M355 202 Q393 188 431 202 T507 202 M173 224 Q210 211 247 224" />
        </svg>
      </div>

      <div class="section-heading">
        <div><p class="eyebrow">AT A GLANCE</p><h2>Today’s numbers</h2></div>
        <a class="text-link" href="#catch-records" data-view="catch-records">View all records <span aria-hidden="true">→</span></a>
      </div>
      <div class="summary-grid" aria-live="polite">
        <article class="summary-card card-cyan"><span class="card-icon" aria-hidden="true">↗</span><p>Total Catch</p><strong id="total-catch">0 kg</strong></article>
        <article class="summary-card card-blue"><span class="card-icon" aria-hidden="true">⌁</span><p>Total Trips</p><strong id="total-trips">0</strong></article>
        <article class="summary-card card-coral"><span class="card-icon" aria-hidden="true">＋</span><p>Total Earnings</p><strong id="total-earnings">0.00</strong></article>
        <article class="summary-card card-green"><span class="card-icon" aria-hidden="true">◉</span><p>Most Caught Fish</p><strong id="most-caught">—</strong></article>
      </div>

      <div class="section-heading recent-heading">
        <div><p class="eyebrow">LATEST LANDINGS</p><h2>Recent catches</h2></div>
        <a class="text-link" href="#add-catch" data-view="add-catch">＋ Add a catch</a>
      </div>
      <div class="table-wrap">
        <table>
          <thead><tr><th>Date</th><th>Fish type</th><th>Fisherman</th><th>Quantity</th><th>Location</th></tr></thead>
          <tbody id="recent-table-body"></tbody>
        </table>
        <p class="empty-state" id="recent-empty" hidden>No catches yet. Add your first catch to get started.</p>
      </div>
    </section>

    <section id="add-catch" class="page-view" aria-labelledby="add-title" hidden>
      <div class="page-intro"><p class="eyebrow">NEW LANDING</p><h1 id="add-title">Add a catch</h1><p>Record the details of a completed fishing trip.</p></div>
      <form id="catch-form" class="catch-form">
        <label>Date <input name="date" type="date" required></label>
        <label>Boat name <input name="boat" type="text" placeholder="e.g. Sea Breeze" required maxlength="60"></label>
        <label>Fisherman name <input name="fisherman" type="text" placeholder="Full name" required maxlength="60"></label>
        <label>Fish type
          <select name="fish" required>
            <option value="">Select fish</option><option>Salmon</option><option>Tuna</option><option>Cod</option><option>Herring</option><option>Sardine</option><option>Mackerel</option><option>Tilapia</option><option>Shrimp</option><option>Other</option>
          </select>
        </label>
        <label>Quantity (kg) <input name="quantity" type="number" min="0.01" step="0.01" placeholder="0.00" required></label>
        <label>Price per kg <input name="price" type="number" min="0.01" step="0.01" placeholder="0.00" required></label>
        <label class="wide-field">Location <input name="location" type="text" placeholder="Port, bay, or fishing area" required maxlength="80"></label>
        <div class="form-actions wide-field"><p id="form-message" class="form-message" role="status" aria-live="polite"></p><button class="primary-button" type="submit">Save catch <span aria-hidden="true">→</span></button></div>
      </form>
    </section>

    <section id="catch-records" class="page-view" aria-labelledby="records-title" hidden>
      <div class="page-intro records-intro"><div><p class="eyebrow">CATCH HISTORY</p><h1 id="records-title">Catch records</h1><p>Search and manage your recorded landings.</p></div>
        <label class="search-box"><span class="search-icon" aria-hidden="true">⌕</span><span class="visually-hidden">Search by fish or fisherman</span><input id="record-search" type="search" placeholder="Search fish or fisherman…" autocomplete="off"></label>
      </div>
      <div class="table-wrap records-table-wrap">
        <table>
          <thead><tr><th>Date</th><th>Boat</th><th>Fisherman</th><th>Fish type</th><th>Quantity</th><th>Price/kg</th><th>Earnings</th><th>Location</th><th><span class="visually-hidden">Actions</span></th></tr></thead>
          <tbody id="records-table-body"></tbody>
        </table>
        <p class="empty-state" id="records-empty" hidden>No matching catches found.</p>
      </div>
    </section>
  </main>
  <footer class="site-footer"><span>AquaCatch</span><span>Catch records saved on this device</span></footer>
  <script>
// AquaCatch stores all catch records in this browser only.
const STORAGE_KEY = "aquacatch-records-v1";
const sampleCatches = [
  { id: "sample-1", date: "2026-11-17", boat: "Sea Breeze", fisherman: "Maya Chen", fish: "Salmon", quantity: 46.5, price: 8.25, location: "North Cove" },
  { id: "sample-2", date: "2026-11-16", boat: "Blue Fin", fisherman: "Noah Patel", fish: "Tuna", quantity: 72, price: 12.5, location: "Harbor Point" },
  { id: "sample-3", date: "2026-11-15", boat: "Sea Breeze", fisherman: "Maya Chen", fish: "Salmon", quantity: 38, price: 8.1, location: "North Cove" },
  { id: "sample-4", date: "2026-11-14", boat: "Morning Tide", fisherman: "Liam Okafor", fish: "Mackerel", quantity: 54.25, price: 6.4, location: "East Shoal" },
  { id: "sample-5", date: "2026-11-13", boat: "Blue Fin", fisherman: "Noah Patel", fish: "Tuna", quantity: 61.5, price: 12.25, location: "Harbor Point" }
];

const byId = (id) => document.getElementById(id);
const dateInput = document.querySelector('input[name="date"]');
const catchForm = byId("catch-form");
const formMessage = byId("form-message");

function loadCatches() {
  try {
    const saved = localStorage.getItem(STORAGE_KEY);
    if (saved === null) {
      localStorage.setItem(STORAGE_KEY, JSON.stringify(sampleCatches));
      return [...sampleCatches];
    }
    const records = JSON.parse(saved);
    return Array.isArray(records) ? records : [...sampleCatches];
  } catch (error) {
    console.warn("Catch records could not be loaded from this browser.", error);
    return [...sampleCatches];
  }
}

let catches = loadCatches();

function saveCatches() {
  try {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(catches));
    return true;
  } catch (error) {
    console.warn("Catch records could not be saved in this browser.", error);
    return false;
  }
}

function escapeHtml(value) {
  return String(value).replace(/[&<>"']/g, (character) => ({
    "&": "&amp;", "<": "&lt;", ">": "&gt;", '"': "&quot;", "'": "&#039;"
  })[character]);
}

function formatNumber(value) {
  return Number(value).toLocaleString(undefined, { maximumFractionDigits: 2 });
}

function formatDate(value) {
  const date = new Date(`${value}T00:00:00`);
  return Number.isNaN(date.getTime()) ? value : date.toLocaleDateString(undefined, { year: "numeric", month: "short", day: "numeric" });
}

function newestFirst(records) {
  return [...records].sort((a, b) => b.date.localeCompare(a.date) || String(b.id).localeCompare(String(a.id)));
}

function renderDashboard() {
  const totalQuantity = catches.reduce((sum, item) => sum + Number(item.quantity || 0), 0);
  const totalEarnings = catches.reduce((sum, item) => sum + Number(item.quantity || 0) * Number(item.price || 0), 0);
  const fishTotals = catches.reduce((totals, item) => {
    totals[item.fish] = (totals[item.fish] || 0) + Number(item.quantity || 0);
    return totals;
  }, {});
  const mostCaught = Object.entries(fishTotals).sort((a, b) => b[1] - a[1])[0];
  byId("total-catch").textContent = `${formatNumber(totalQuantity)} kg`;
  byId("total-trips").textContent = String(catches.length);
  byId("total-earnings").textContent = formatNumber(totalEarnings);
  byId("most-caught").textContent = mostCaught ? mostCaught[0] : "—";

  const recent = newestFirst(catches).slice(0, 5);
  byId("recent-table-body").innerHTML = recent.map((item) => `
    <tr><td>${escapeHtml(formatDate(item.date))}</td><td><span class="fish-pill">${escapeHtml(item.fish)}</span></td>
    <td>${escapeHtml(item.fisherman)}</td><td>${formatNumber(item.quantity)} kg</td><td>${escapeHtml(item.location)}</td></tr>`).join("");
  byId("recent-empty").hidden = recent.length > 0;
}

function renderRecords(searchTerm = "") {
  const query = searchTerm.trim().toLocaleLowerCase();
  const rows = newestFirst(catches).filter((item) =>
    `${item.fish} ${item.fisherman}`.toLocaleLowerCase().includes(query)
  );
  byId("records-table-body").innerHTML = rows.map((item) => `
    <tr><td>${escapeHtml(formatDate(item.date))}</td><td>${escapeHtml(item.boat)}</td>
    <td>${escapeHtml(item.fisherman)}</td><td><span class="fish-pill">${escapeHtml(item.fish)}</span></td>
    <td>${formatNumber(item.quantity)} kg</td><td>${formatNumber(item.price)}</td>
    <td>${formatNumber(Number(item.quantity) * Number(item.price))}</td><td>${escapeHtml(item.location)}</td>
    <td><button class="delete-button" type="button" data-delete-id="${escapeHtml(item.id)}" aria-label="Delete catch for ${escapeHtml(item.fish)} by ${escapeHtml(item.fisherman)}">Delete</button></td></tr>`).join("");
  byId("records-empty").hidden = rows.length > 0;
}

function showView(viewName) {
  document.querySelectorAll(".page-view").forEach((view) => {
    view.hidden = view.id !== viewName;
  });
  document.querySelectorAll(".nav-link").forEach((link) => {
    const active = link.dataset.view === viewName;
    link.classList.toggle("active", active);
    if (active) link.setAttribute("aria-current", "page");
    else link.removeAttribute("aria-current");
  });
  if (viewName === "dashboard") renderDashboard();
  if (viewName === "catch-records") renderRecords(byId("record-search").value);
  window.scrollTo({ top: 0, behavior: "smooth" });
}

document.querySelectorAll("[data-view]").forEach((link) => {
  link.addEventListener("click", (event) => {
    event.preventDefault();
    const viewName = link.dataset.view;
    showView(viewName);
    window.location.hash = viewName;
  });
});

window.addEventListener("hashchange", () => {
  const requestedView = window.location.hash.slice(1);
  showView(["dashboard", "add-catch", "catch-records"].includes(requestedView) ? requestedView : "dashboard");
});

byId("record-search").addEventListener("input", (event) => renderRecords(event.target.value));
byId("records-table-body").addEventListener("click", (event) => {
  const button = event.target.closest("[data-delete-id]");
  if (!button) return;
  catches = catches.filter((item) => String(item.id) !== button.dataset.deleteId);
  saveCatches();
  renderRecords(byId("record-search").value);
  renderDashboard();
});

catchForm.addEventListener("submit", (event) => {
  event.preventDefault();
  formMessage.textContent = "";
  formMessage.classList.remove("error");
  if (!catchForm.reportValidity()) return;

  const formData = new FormData(catchForm);
  const quantity = Number(formData.get("quantity"));
  const price = Number(formData.get("price"));
  if (!(quantity > 0) || !(price > 0)) {
    formMessage.textContent = "Quantity and price must be greater than zero.";
    formMessage.classList.add("error");
    return;
  }

  const record = {
    id: `catch-${Date.now()}-${Math.random().toString(36).slice(2, 8)}`,
    date: formData.get("date"), boat: formData.get("boat").trim(),
    fisherman: formData.get("fisherman").trim(), fish: formData.get("fish"),
    quantity, price, location: formData.get("location").trim()
  };
  catches.push(record);
  if (!saveCatches()) {
    catches.pop();
    formMessage.textContent = "Could not save. Please check browser storage settings.";
    formMessage.classList.add("error");
    return;
  }
  catchForm.reset();
  dateInput.value = new Date().toISOString().slice(0, 10);
  formMessage.textContent = "Catch saved successfully.";
  renderDashboard();
});

dateInput.value = new Date().toISOString().slice(0, 10);
showView(["dashboard", "add-catch", "catch-records"].includes(window.location.hash.slice(1)) ? window.location.hash.slice(1) : "dashboard");

  </script>
</body>
</html>
Page 1 of 1
