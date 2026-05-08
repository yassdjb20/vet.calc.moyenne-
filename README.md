<hi future vets>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Moyenne Vét. 2A</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;500&family=Syne:wght@400;600;700&display=swap');

  :root {
    --bg: #0f0f13;
    --surface: #18181f;
    --surface2: #1f1f28;
    --border: #2a2a36;
    --border2: #35354a;
    --accent: #7c6ef5;
    --accent2: #a394f7;
    --accent-dim: rgba(124,110,245,0.15);
    --green: #4ade80;
    --green-dim: rgba(74,222,128,0.12);
    --red: #f87171;
    --red-dim: rgba(248,113,113,0.12);
    --amber: #fbbf24;
    --amber-dim: rgba(251,191,36,0.12);
    --pink: #f472b6;
    --pink-dim: rgba(244,114,182,0.12);
    --text: #e8e8f0;
    --text2: #8888a8;
    --text3: #55556a;
    --mono: 'DM Mono', monospace;
    --sans: 'Syne', sans-serif;
    --r: 12px;
    --r-sm: 8px;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }

  html, body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    min-height: 100vh;
    font-size: 15px;
  }

  .app {
    max-width: 480px;
    margin: 0 auto;
    padding: 0 0 120px;
  }

  /* HEADER */
  .header {
    padding: 20px 16px 0;
    position: sticky;
    top: 0;
    background: var(--bg);
    z-index: 100;
    border-bottom: 1px solid var(--border);
    padding-bottom: 12px;
  }

  .header-top {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 4px;
  }

  .app-title {
    font-size: 18px;
    font-weight: 700;
    letter-spacing: -0.3px;
    color: var(--text);
  }

  .app-sub {
    font-size: 11px;
    color: var(--text3);
    font-family: var(--mono);
    letter-spacing: 0.5px;
    text-transform: uppercase;
  }

  .progress-bar {
    height: 3px;
    background: var(--border);
    border-radius: 99px;
    margin-top: 12px;
    overflow: hidden;
  }

  .progress-fill {
    height: 100%;
    background: var(--accent);
    border-radius: 99px;
    transition: width 0.4s ease;
    width: 0%;
  }

  .progress-label {
    font-size: 11px;
    font-family: var(--mono);
    color: var(--text3);
    margin-top: 4px;
    text-align: right;
  }

  /* RESULT STICKY BAR */
  .result-bar {
    position: sticky;
    top: 110px;
    z-index: 90;
    margin: 0 16px;
    background: var(--surface);
    border: 1px solid var(--border2);
    border-radius: var(--r);
    padding: 14px 16px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: 12px;
    transition: border-color 0.3s;
  }

  .result-bar.pass { border-color: var(--green); }
  .result-bar.fail { border-color: var(--red); }

  .result-left {}
  .result-label { font-size: 11px; color: var(--text3); font-family: var(--mono); text-transform: uppercase; letter-spacing: 0.5px; }
  .result-avg {
    font-size: 36px;
    font-weight: 700;
    font-family: var(--mono);
    letter-spacing: -1px;
    color: var(--text);
    line-height: 1;
    margin-top: 2px;
    transition: color 0.3s;
  }
  .result-avg.pass { color: var(--green); }
  .result-avg.fail { color: var(--red); }
  .result-avg.partial { color: var(--accent2); }

  .result-right { text-align: right; }
  .result-status {
    font-size: 13px;
    font-weight: 600;
    padding: 4px 12px;
    border-radius: 99px;
    font-family: var(--mono);
  }
  .result-status.pass { background: var(--green-dim); color: var(--green); }
  .result-status.fail { background: var(--red-dim); color: var(--red); }
  .result-status.neutral { background: var(--accent-dim); color: var(--accent2); }

  .result-mention {
    font-size: 11px;
    color: var(--text3);
    margin-top: 4px;
    font-family: var(--mono);
  }

  /* SECTION */
  .section {
    margin: 16px 16px 0;
  }

  .section-title {
    font-size: 11px;
    font-family: var(--mono);
    color: var(--text3);
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 8px;
    padding-left: 2px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* MODULE CARD */
  .mod-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r);
    margin-bottom: 8px;
    overflow: hidden;
    transition: border-color 0.2s;
  }

  .mod-card.annual { border-left: 3px solid var(--pink); }
  .mod-card.complete { border-color: var(--border2); }
  .mod-card.complete.ok { border-color: rgba(74,222,128,0.3); }
  .mod-card.complete.ko { border-color: rgba(248,113,113,0.3); }

  .mod-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 11px 14px;
    cursor: pointer;
    user-select: none;
  }

  .mod-header-left { flex: 1; min-width: 0; }

  .mod-name {
    font-size: 13px;
    font-weight: 600;
    color: var(--text);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .mod-meta {
    display: flex;
    align-items: center;
    gap: 6px;
    margin-top: 3px;
  }

  .badge {
    font-size: 10px;
    font-family: var(--mono);
    padding: 1px 6px;
    border-radius: 99px;
    font-weight: 500;
  }

  .badge-s1 { background: rgba(124,110,245,0.2); color: var(--accent2); }
  .badge-s2 { background: rgba(74,222,128,0.15); color: var(--green); }
  .badge-ann { background: var(--pink-dim); color: var(--pink); }
  .badge-coeff { background: var(--surface2); color: var(--text2); }

  .mod-note-display {
    font-size: 16px;
    font-family: var(--mono);
    font-weight: 500;
    min-width: 52px;
    text-align: right;
    color: var(--text3);
    transition: color 0.2s;
  }
  .mod-note-display.pass { color: var(--green); }
  .mod-note-display.fail { color: var(--red); }

  .chevron {
    width: 16px;
    height: 16px;
    margin-left: 8px;
    color: var(--text3);
    transition: transform 0.2s;
    flex-shrink: 0;
  }
  .chevron.open { transform: rotate(180deg); }

  /* INPUTS */
  .mod-inputs {
    padding: 0 14px 12px;
    display: none;
    gap: 10px;
  }
  .mod-inputs.open { display: flex; }

  .inp-group {
    flex: 1;
  }

  .inp-label {
    font-size: 10px;
    font-family: var(--mono);
    color: var(--text3);
    text-transform: uppercase;
    letter-spacing: 0.5px;
    margin-bottom: 5px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .inp-weight {
    color: var(--accent2);
  }

  input[type=number] {
    width: 100%;
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: var(--r-sm);
    color: var(--text);
    font-family: var(--mono);
    font-size: 16px;
    font-weight: 500;
    padding: 10px 10px;
    text-align: center;
    -moz-appearance: textfield;
    appearance: textfield;
    transition: border-color 0.2s, background 0.2s;
  }

  input[type=number]::-webkit-outer-spin-button,
  input[type=number]::-webkit-inner-spin-button { -webkit-appearance: none; }

  input[type=number]:focus {
    outline: none;
    border-color: var(--accent);
    background: rgba(124,110,245,0.08);
  }

  input[type=number]:disabled {
    opacity: 0.2;
    cursor: not-allowed;
  }

  input[type=number].invalid {
    border-color: var(--red);
    background: var(--red-dim);
  }

  /* STATS ROW */
  .stats-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 8px;
    margin: 16px 16px 0;
  }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--r);
    padding: 12px 14px;
  }

  .stat-label {
    font-size: 10px;
    font-family: var(--mono);
    color: var(--text3);
    text-transform: uppercase;
    letter-spacing: 0.5px;
    margin-bottom: 4px;
  }

  .stat-value {
    font-size: 20px;
    font-weight: 700;
    font-family: var(--mono);
    color: var(--text);
  }

  .stat-value span {
    font-size: 12px;
    font-weight: 400;
    color: var(--text3);
  }

  /* RESET BTN */
  .reset-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin: 20px 16px 0;
    padding: 14px;
    background: transparent;
    border: 1px solid var(--border2);
    border-radius: var(--r);
    color: var(--text2);
    font-family: var(--mono);
    font-size: 13px;
    cursor: pointer;
    transition: background 0.2s, color 0.2s;
    width: calc(100% - 32px);
  }

  .reset-btn:active {
    background: var(--surface2);
    color: var(--text);
  }

  /* SEPARATOR */
  .sep {
    height: 1px;
    background: var(--border);
    margin: 20px 16px 0;
  }
</style>
</head>
<body>

<div class="app">

  <!-- HEADER -->
  <div class="header">
    <div class="header-top">
      <div>
        <div class="app-title">Moyenne Annuelle</div>
        <div class="app-sub">Médecine vétérinaire — 2ème année</div>
      </div>
    </div>
    <div class="progress-bar"><div class="progress-fill" id="prog-fill"></div></div>
    <div class="progress-label" id="prog-label">0 / 17 modules</div>
  </div>

  <!-- RESULT BAR -->
  <div class="result-bar" id="result-bar">
    <div class="result-left">
      <div class="result-label">moyenne annuelle</div>
      <div class="result-avg" id="result-avg">—</div>
      <div style="font-size:11px;color:var(--text3);font-family:var(--mono);margin-top:2px;">/ 20 · coeff. total 38</div>
    </div>
    <div class="result-right">
      <div class="result-status neutral" id="result-status">En cours</div>
      <div class="result-mention" id="result-mention"></div>
    </div>
  </div>

  <!-- SEMESTRE 1 -->
  <div class="section">
    <div class="section-title">Semestre 1</div>

    <div class="mod-card" data-mod="bactg" data-coeff="2" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Bactériologie générale</div>
          <div class="mod-meta">
            <span class="badge badge-s1">S1</span>
            <span class="badge badge-coeff">coeff. 2</span>
          </div>
        </div>
        <div class="mod-note-display" id="nd-bactg">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group">
          <div class="inp-label">EMD <span class="inp-weight">×60%</span></div>
          <input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd">
        </div>
        <div class="inp-group">
          <div class="inp-label">CC <span class="inp-weight">×20%</span></div>
          <input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc">
        </div>
        <div class="inp-group">
          <div class="inp-label">TP <span class="inp-weight">×20%</span></div>
          <input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp">
        </div>
      </div>
    </div>

    <div class="mod-card" data-mod="virg" data-coeff="2" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Virologie générale</div>
          <div class="mod-meta"><span class="badge badge-s1">S1</span><span class="badge badge-coeff">coeff. 2</span></div>
        </div>
        <div class="mod-note-display" id="nd-virg">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×60%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card" data-mod="imv" data-coeff="2" data-emd="0.7" data-cc="0.3" data-tp="0">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Immuno-vaccinologie</div>
          <div class="mod-meta"><span class="badge badge-s1">S1</span><span class="badge badge-coeff">coeff. 2</span></div>
        </div>
        <div class="mod-note-display" id="nd-imv">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×70%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×30%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP</div><input type="number" disabled class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card" data-mod="hists" data-coeff="2" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Histologie spéciale</div>
          <div class="mod-meta"><span class="badge badge-s1">S1</span><span class="badge badge-coeff">coeff. 2</span></div>
        </div>
        <div class="mod-note-display" id="nd-hists">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×60%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card" data-mod="physio2" data-coeff="3" data-emd="0.7" data-cc="0.3" data-tp="0">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Physiologie 2</div>
          <div class="mod-meta"><span class="badge badge-s1">S1</span><span class="badge badge-coeff">coeff. 3</span></div>
        </div>
        <div class="mod-note-display" id="nd-physio2">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×70%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×30%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP</div><input type="number" disabled class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card" data-mod="ethnos" data-coeff="2" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Ethnologie spéciale</div>
          <div class="mod-meta"><span class="badge badge-s1">S1</span><span class="badge badge-coeff">coeff. 2</span></div>
        </div>
        <div class="mod-note-display" id="nd-ethnos">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×60%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp"></div>
      </div>
    </div>

    <!-- ANNUAL S1 -->
    <div class="mod-card annual" data-mod="anat2s1" data-coeff="2" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Anatomie 2</div>
          <div class="mod-meta"><span class="badge badge-ann">annuel</span><span class="badge badge-s1">S1</span><span class="badge badge-coeff">coeff. 2</span></div>
        </div>
        <div class="mod-note-display" id="nd-anat2s1">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×60%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card annual" data-mod="phyreps1" data-coeff="2" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Physio. reproduction</div>
          <div class="mod-meta"><span class="badge badge-ann">annuel</span><span class="badge badge-s1">S1</span><span class="badge badge-coeff">coeff. 2</span></div>
        </div>
        <div class="mod-note-display" id="nd-phyreps1">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×60%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card annual" data-mod="alims1" data-coeff="3" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Alimentation</div>
          <div class="mod-meta"><span class="badge badge-ann">annuel</span><span class="badge badge-s1">S1</span><span class="badge badge-coeff">coeff. 3</span></div>
        </div>
        <div class="mod-note-display" id="nd-alims1">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×60%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp"></div>
      </div>
    </div>
  </div>

  <div class="sep"></div>

  <!-- SEMESTRE 2 -->
  <div class="section">
    <div class="section-title">Semestre 2</div>

    <div class="mod-card annual" data-mod="anat2s2" data-coeff="2" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Anatomie 2</div>
          <div class="mod-meta"><span class="badge badge-ann">annuel</span><span class="badge badge-s2">S2</span><span class="badge badge-coeff">coeff. 2</span></div>
        </div>
        <div class="mod-note-display" id="nd-anat2s2">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×60%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card annual" data-mod="phyreps2" data-coeff="2" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Physio. reproduction</div>
          <div class="mod-meta"><span class="badge badge-ann">annuel</span><span class="badge badge-s2">S2</span><span class="badge badge-coeff">coeff. 2</span></div>
        </div>
        <div class="mod-note-display" id="nd-phyreps2">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×60%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card annual" data-mod="alims2" data-coeff="3" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Alimentation</div>
          <div class="mod-meta"><span class="badge badge-ann">annuel</span><span class="badge badge-s2">S2</span><span class="badge badge-coeff">coeff. 3</span></div>
        </div>
        <div class="mod-note-display" id="nd-alims2">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×60%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card" data-mod="epa" data-coeff="3" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Élevages et prod. animales</div>
          <div class="mod-meta"><span class="badge badge-s2">S2</span><span class="badge badge-coeff">coeff. 3</span></div>
        </div>
        <div class="mod-note-display" id="nd-epa">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×60%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card" data-mod="agb" data-coeff="3" data-emd="0.6" data-cc="0.2" data-tp="0.2">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Amél. génétique &amp; Biotechno.</div>
          <div class="mod-meta"><span class="badge badge-s2">S2</span><span class="badge badge-coeff">coeff. 3</span></div>
        </div>
        <div class="mod-note-display" id="nd-agb">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×60%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP <span class="inp-weight">×20%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card" data-mod="biostat" data-coeff="3" data-emd="0.7" data-cc="0.3" data-tp="0">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Biostatistiques</div>
          <div class="mod-meta"><span class="badge badge-s2">S2</span><span class="badge badge-coeff">coeff. 3</span></div>
        </div>
        <div class="mod-note-display" id="nd-biostat">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×70%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×30%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP</div><input type="number" disabled class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card" data-mod="ang" data-coeff="1" data-emd="0.7" data-cc="0.3" data-tp="0">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Anglais scientifique</div>
          <div class="mod-meta"><span class="badge badge-s2">S2</span><span class="badge badge-coeff">coeff. 1</span></div>
        </div>
        <div class="mod-note-display" id="nd-ang">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×70%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×30%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP</div><input type="number" disabled class="inp-tp"></div>
      </div>
    </div>

    <div class="mod-card" data-mod="bioinf" data-coeff="1" data-emd="0.7" data-cc="0.3" data-tp="0">
      <div class="mod-header" onclick="toggleCard(this)">
        <div class="mod-header-left">
          <div class="mod-name">Bio-informatique</div>
          <div class="mod-meta"><span class="badge badge-s2">S2</span><span class="badge badge-coeff">coeff. 1</span></div>
        </div>
        <div class="mod-note-display" id="nd-bioinf">—</div>
        <svg class="chevron" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="6 9 12 15 18 9"/></svg>
      </div>
      <div class="mod-inputs">
        <div class="inp-group"><div class="inp-label">EMD <span class="inp-weight">×70%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-emd"></div>
        <div class="inp-group"><div class="inp-label">CC <span class="inp-weight">×30%</span></div><input type="number" min="0" max="20" step="0.25" placeholder="—" class="inp-cc"></div>
        <div class="inp-group"><div class="inp-label">TP</div><input type="number" disabled class="inp-tp"></div>
      </div>
    </div>

  </div>

  <!-- STATS -->
  <div class="stats-row">
    <div class="stat-card">
      <div class="stat-label">Modules saisis</div>
      <div class="stat-value" id="nb-mods">0 <span>/ 17</span></div>
    </div>
    <div class="stat-card">
      <div class="stat-label">Coefficients</div>
      <div class="stat-value" id="nb-coeff">0 <span>/ 38</span></div>
    </div>
  </div>

  <button class="reset-btn" onclick="resetAll()">
    <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="1 4 1 10 7 10"/><path d="M3.51 15a9 9 0 1 0 .49-3.5"/></svg>
    Réinitialiser tout
  </button>

</div>

<script>
const TOTAL = 38, TOTAL_MODS = 17;

function toggleCard(header) {
  const inputs = header.nextElementSibling;
  const chevron = header.querySelector('.chevron');
  const isOpen = inputs.classList.contains('open');
  inputs.classList.toggle('open', !isOpen);
  chevron.classList.toggle('open', !isOpen);
}

function calcNote(card) {
  const emdW = parseFloat(card.dataset.emd);
  const ccW  = parseFloat(card.dataset.cc);
  const tpW  = parseFloat(card.dataset.tp);
  const emdI = card.querySelector('.inp-emd');
  const ccI  = card.querySelector('.inp-cc');
  const tpI  = card.querySelector('.inp-tp');
  const emd = emdI && emdI.value !== '' ? parseFloat(emdI.value) : null;
  const cc  = ccI  && ccI.value  !== '' ? parseFloat(ccI.value)  : null;
  const tp  = (!tpI || tpI.disabled) ? 0 : (tpI.value !== '' ? parseFloat(tpI.value) : null);
  if (emd === null || cc === null) return null;
  if (tpW > 0 && tp === null) return null;
  return Math.min(20, Math.max(0, emd * emdW + cc * ccW + (tpW > 0 ? tp * tpW : 0)));
}

function getMention(avg) {
  if (avg >= 16) return 'Très bien';
  if (avg >= 14) return 'Bien';
  if (avg >= 12) return 'Assez bien';
  if (avg >= 10) return 'Passable';
  return 'Ajourné';
}

function updateAll() {
  let sumNC = 0, sumC = 0, nb = 0;
  document.querySelectorAll('.mod-card').forEach(card => {
    const mod   = card.dataset.mod;
    const coeff = parseInt(card.dataset.coeff);
    const note  = calcNote(card);
    const nd    = document.getElementById('nd-' + mod);
    if (!nd) return;
    if (note === null) {
      nd.textContent = '—';
      nd.className = 'mod-note-display';
      card.classList.remove('complete', 'ok', 'ko');
    } else {
      nd.textContent = note.toFixed(2);
      nd.className = 'mod-note-display ' + (note >= 10 ? 'pass' : 'fail');
      card.classList.add('complete');
      card.classList.toggle('ok', note >= 10);
      card.classList.toggle('ko', note < 10);
      sumNC += note * coeff;
      sumC  += coeff;
      nb++;
    }
  });

  document.getElementById('nb-mods').innerHTML  = nb + ' <span>/ ' + TOTAL_MODS + '</span>';
  document.getElementById('nb-coeff').innerHTML = sumC + ' <span>/ ' + TOTAL + '</span>';
  document.getElementById('prog-fill').style.width = Math.round(nb / TOTAL_MODS * 100) + '%';
  document.getElementById('prog-label').textContent = nb + ' / ' + TOTAL_MODS + ' modules';

  const avgEl  = document.getElementById('result-avg');
  const statEl = document.getElementById('result-status');
  const menEl  = document.getElementById('result-mention');
  const barEl  = document.getElementById('result-bar');

  if (sumC === 0) {
    avgEl.textContent  = '—';
    avgEl.className    = 'result-avg';
    statEl.textContent = 'En cours';
    statEl.className   = 'result-status neutral';
    barEl.className    = 'result-bar';
    menEl.textContent  = '';
    return;
  }

  const avg = sumNC / sumC;
  avgEl.textContent = avg.toFixed(2);

  if (nb < TOTAL_MODS) {
    avgEl.className    = 'result-avg partial';
    statEl.textContent = 'Partiel';
    statEl.className   = 'result-status neutral';
    barEl.className    = 'result-bar';
    menEl.textContent  = getMention(avg) + ' (provisoire)';
  } else {
    const pass = avg >= 10;
    avgEl.className    = 'result-avg ' + (pass ? 'pass' : 'fail');
    statEl.textContent = pass ? 'Admis' : 'Ajourné';
    statEl.className   = 'result-status ' + (pass ? 'pass' : 'fail');
    barEl.className    = 'result-bar ' + (pass ? 'pass' : 'fail');
    menEl.textContent  = getMention(avg);
  }
}

function resetAll() {
  document.querySelectorAll('input[type=number]').forEach(i => { if (!i.disabled) i.value = ''; });
  document.querySelectorAll('.mod-inputs.open').forEach(d => {
    d.classList.remove('open');
    d.previousElementSibling.querySelector('.chevron').classList.remove('open');
  });
  updateAll();
}

document.querySelectorAll('input[type=number]').forEach(i => i.addEventListener('input', updateAll));
</script>
</body>
</html>
