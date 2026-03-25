<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Formulaire Client — La Boite Kreativ</title>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,700;1,300&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --orange: #F5A623;
      --orange-dark: #D4891A;
      --orange-glow: rgba(245,166,35,0.18);
      --black: #111111;
      --card: #1A1A1A;
      --card2: #222222;
      --border: rgba(245,166,35,0.25);
      --text: #F0F0F0;
      --muted: #888888;
      --radius: 12px;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background: var(--black);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      min-height: 100vh;
      padding: 0;
      overflow-x: hidden;
    }

    /* BG decoration */
    body::before {
      content: '';
      position: fixed;
      top: -200px; right: -200px;
      width: 600px; height: 600px;
      background: radial-gradient(circle, rgba(245,166,35,0.12) 0%, transparent 70%);
      pointer-events: none;
      z-index: 0;
    }
    body::after {
      content: '';
      position: fixed;
      bottom: -200px; left: -200px;
      width: 500px; height: 500px;
      background: radial-gradient(circle, rgba(245,166,35,0.08) 0%, transparent 70%);
      pointer-events: none;
      z-index: 0;
    }

    .wrapper {
      max-width: 780px;
      margin: 0 auto;
      padding: 40px 20px 80px;
      position: relative;
      z-index: 1;
    }

    /* HEADER */
    header {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      margin-bottom: 48px;
      padding-bottom: 28px;
      border-bottom: 1px solid var(--border);
      text-align: center;
    }

    .logo-box {
      width: 54px; height: 54px;
      background: var(--orange);
      border-radius: 10px;
      display: flex; align-items: center; justify-content: center;
      font-size: 26px;
      flex-shrink: 0;
      box-shadow: 0 4px 20px rgba(245,166,35,0.4);
    }

    .logo-text h1 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 28px;
      letter-spacing: 2px;
      color: var(--orange);
      line-height: 1;
    }
    .logo-text p {
      font-size: 13px;
      color: var(--muted);
      margin-top: 3px;
      font-style: normal;
      text-align: center;
    }

    .header-right {
      text-align: center;
    }
    .header-right .badge {
      background: var(--orange-glow);
      border: 1px solid var(--border);
      color: var(--orange);
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 1.5px;
      padding: 4px 12px;
      border-radius: 20px;
      text-transform: uppercase;
    }
    .header-right p {
      font-size: 12px;
      color: var(--muted);
      margin-top: 6px;
    }

    /* SECTION TITLE */
    .section-title {
      display: flex;
      align-items: center;
      gap: 10px;
      margin: 36px 0 18px;
    }
    .section-title .icon {
      width: 34px; height: 34px;
      background: var(--orange-glow);
      border: 1px solid var(--border);
      border-radius: 8px;
      display: flex; align-items: center; justify-content: center;
      font-size: 16px;
    }
    .section-title h2 {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 20px;
      letter-spacing: 2px;
      color: var(--orange);
    }
    .section-line {
      flex: 1;
      height: 1px;
      background: var(--border);
    }

    /* CARD */
    .card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 28px;
      margin-bottom: 16px;
    }

    /* FORM GRID */
    .form-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }
    .form-grid .full { grid-column: 1 / -1; }

    .field {
      display: flex;
      flex-direction: column;
      gap: 7px;
    }

    label {
      font-size: 12px;
      font-weight: 700;
      letter-spacing: 1px;
      text-transform: uppercase;
      color: var(--muted);
    }
    label .req { color: var(--orange); margin-left: 3px; }

    input, select, textarea {
      background: var(--card2);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 8px;
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      font-size: 14px;
      padding: 11px 14px;
      outline: none;
      transition: border-color 0.2s, box-shadow 0.2s;
      width: 100%;
    }
    input::placeholder, textarea::placeholder { color: #555; }
    input:focus, select:focus, textarea:focus {
      border-color: var(--orange);
      box-shadow: 0 0 0 3px rgba(245,166,35,0.12);
    }
    select {
      appearance: none;
      background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath fill='%23F5A623' d='M1 1l5 5 5-5'/%3E%3C/svg%3E");
      background-repeat: no-repeat;
      background-position: right 14px center;
      cursor: pointer;
    }
    select option { background: #1A1A1A; }
    textarea { resize: vertical; min-height: 90px; }

    /* SERVICE CHECKBOXES */
    .services-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 10px;
    }

    .service-check {
      display: flex;
      align-items: center;
      gap: 10px;
      background: var(--card2);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 8px;
      padding: 10px 14px;
      cursor: pointer;
      transition: border-color 0.2s, background 0.2s;
      user-select: none;
    }
    .service-check:hover { border-color: var(--orange); }
    .service-check input[type="checkbox"] {
      width: 18px; height: 18px;
      accent-color: var(--orange);
      cursor: pointer;
      flex-shrink: 0;
      padding: 0;
    }
    .service-check.checked {
      border-color: var(--orange);
      background: var(--orange-glow);
    }
    .service-check span {
      font-size: 13px;
      font-weight: 500;
      color: var(--text);
    }
    .service-check .sicon { font-size: 16px; }

    /* BUDGET SLIDER */
    .budget-display {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 32px;
      color: var(--orange);
      letter-spacing: 2px;
      margin-bottom: 10px;
    }
    .budget-display span { font-size: 16px; color: var(--muted); margin-left: 6px; }

    input[type="range"] {
      -webkit-appearance: none;
      height: 4px;
      border-radius: 2px;
      background: linear-gradient(to right, var(--orange) 0%, var(--orange) 30%, #333 30%);
      border: none;
      padding: 0;
      box-shadow: none;
      cursor: pointer;
    }
    input[type="range"]::-webkit-slider-thumb {
      -webkit-appearance: none;
      width: 20px; height: 20px;
      background: var(--orange);
      border-radius: 50%;
      box-shadow: 0 0 10px rgba(245,166,35,0.5);
      cursor: pointer;
    }
    input[type="range"]:focus { box-shadow: none; border: none; }

    .range-labels {
      display: flex;
      justify-content: space-between;
      font-size: 11px;
      color: var(--muted);
      margin-top: 6px;
    }

    /* RADIO FORFAITS */
    .forfait-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
    }
    .forfait-card {
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 10px;
      padding: 14px 12px;
      cursor: pointer;
      transition: all 0.2s;
      text-align: center;
      position: relative;
    }
    .forfait-card:hover { border-color: var(--orange); }
    .forfait-card input[type="radio"] { display: none; }
    .forfait-card.selected {
      border-color: var(--orange);
      background: var(--orange-glow);
    }
    .forfait-card .badge-top {
      position: absolute;
      top: -9px; left: 50%; transform: translateX(-50%);
      background: var(--orange);
      color: var(--black);
      font-size: 9px;
      font-weight: 800;
      letter-spacing: 1px;
      padding: 2px 8px;
      border-radius: 20px;
      white-space: nowrap;
    }
    .forfait-card .fname {
      font-family: 'Bebas Neue', sans-serif;
      font-size: 18px;
      letter-spacing: 1px;
      color: var(--text);
      margin-bottom: 4px;
    }
    .forfait-card .fdesc {
      font-size: 11px;
      color: var(--muted);
      line-height: 1.4;
    }

    /* COMMENT FIELD */
    .char-count {
      text-align: right;
      font-size: 11px;
      color: var(--muted);
      margin-top: 4px;
    }

    /* SOURCE RADIO */
    .source-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
    }
    .source-tag {
      padding: 7px 14px;
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: 20px;
      font-size: 12px;
      cursor: pointer;
      transition: all 0.2s;
      user-select: none;
    }
    .source-tag:hover { border-color: var(--orange); color: var(--orange); }
    .source-tag.selected {
      background: var(--orange);
      border-color: var(--orange);
      color: var(--black);
      font-weight: 700;
    }

    /* LOGO UPLOAD */
    .logo-upload-zone {
      border: 2px dashed var(--border);
      border-radius: var(--radius);
      padding: 28px 20px;
      text-align: center;
      cursor: pointer;
      transition: border-color 0.2s, background 0.2s;
      position: relative;
      background: var(--card2);
    }
    .logo-upload-zone:hover { border-color: var(--orange); background: var(--orange-glow); }
    .logo-upload-zone input[type="file"] {
      position: absolute; inset: 0; opacity: 0; cursor: pointer; width: 100%; height: 100%;
    }
    .logo-upload-zone .upload-icon { font-size: 32px; margin-bottom: 8px; }
    .logo-upload-zone .upload-text { font-size: 13px; color: var(--muted); }
    .logo-upload-zone .upload-text strong { color: var(--orange); }
    .logo-preview {
      display: none;
      margin-top: 14px;
      align-items: center;
      gap: 12px;
      background: var(--card2);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 10px 14px;
    }
    .logo-preview.show { display: flex; }
    .logo-preview img { height: 48px; max-width: 160px; object-fit: contain; border-radius: 4px; }
    .logo-preview .logo-filename { font-size: 12px; color: var(--muted); flex: 1; }
    .logo-preview .logo-remove {
      background: none; border: none; color: #e74c3c; cursor: pointer; font-size: 18px; padding: 0 4px;
    }

    /* COULEURS */
    .colors-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }
    .color-field {
      display: flex;
      flex-direction: column;
      gap: 7px;
    }
    .color-input-wrap {
      display: flex;
      align-items: center;
      gap: 10px;
      background: var(--card2);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 8px;
      padding: 8px 14px;
      transition: border-color 0.2s;
    }
    .color-input-wrap:focus-within { border-color: var(--orange); box-shadow: 0 0 0 3px rgba(245,166,35,0.12); }
    .color-input-wrap input[type="color"] {
      width: 32px; height: 32px; border: none; border-radius: 6px; cursor: pointer;
      background: none; padding: 0; box-shadow: none; flex-shrink: 0;
    }
    .color-input-wrap input[type="text"] {
      border: none; background: none; padding: 0; font-size: 13px; color: var(--text);
      width: 100%; font-family: monospace; box-shadow: none;
    }
    .color-input-wrap input[type="text"]:focus { box-shadow: none; border: none; }
    .color-swatch-row {
      display: flex; gap: 8px; flex-wrap: wrap; margin-top: 6px;
    }
    .color-swatch {
      width: 28px; height: 28px; border-radius: 6px; cursor: pointer;
      border: 2px solid transparent; transition: transform 0.15s, border-color 0.15s;
    }
    .color-swatch:hover { transform: scale(1.2); border-color: var(--orange); }

    /* RÉSEAUX SOCIAUX */
    .social-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 12px;
    }
    .social-field {
      display: flex;
      flex-direction: column;
      gap: 7px;
    }
    .social-input-wrap {
      display: flex;
      align-items: center;
      gap: 10px;
      background: var(--card2);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 8px;
      padding: 9px 14px;
      transition: border-color 0.2s;
    }
    .social-input-wrap:focus-within { border-color: var(--orange); box-shadow: 0 0 0 3px rgba(245,166,35,0.12); }
    .social-input-wrap .social-icon { font-size: 18px; flex-shrink: 0; }
    .social-input-wrap input {
      border: none; background: none; padding: 0; font-size: 13px; color: var(--text);
      width: 100%; box-shadow: none;
    }
    .social-input-wrap input::placeholder { color: #555; }
    .social-input-wrap input:focus { box-shadow: none; border: none; }

    /* SUBMIT */
    .submit-area {
      margin-top: 36px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 16px;
    }

    .btn-submit {
      background: var(--orange);
      color: var(--black);
      border: none;
      border-radius: 10px;
      font-family: 'Bebas Neue', sans-serif;
      font-size: 22px;
      letter-spacing: 3px;
      padding: 16px 60px;
      cursor: pointer;
      transition: transform 0.15s, box-shadow 0.2s;
      box-shadow: 0 4px 24px rgba(245,166,35,0.35);
      width: 100%;
      max-width: 380px;
    }
    .btn-submit:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 32px rgba(245,166,35,0.5);
    }
    .btn-submit:active { transform: translateY(0); }

    .submit-note {
      font-size: 12px;
      color: var(--muted);
      text-align: center;
      line-height: 1.6;
    }

    /* SUCCESS MESSAGE */
    .success-msg {
      display: none;
      background: linear-gradient(135deg, #1a2e1a, #0f1f0f);
      border: 1px solid #2ecc71;
      border-radius: var(--radius);
      padding: 32px;
      text-align: center;
      margin-top: 20px;
    }
    .success-msg.show { display: block; animation: fadeIn 0.4s ease; }
    .success-msg .tick { font-size: 48px; margin-bottom: 12px; }
    .success-msg h3 { font-family: 'Bebas Neue', sans-serif; font-size: 28px; color: #2ecc71; letter-spacing: 2px; }
    .success-msg p { color: #aaa; margin-top: 8px; font-size: 14px; line-height: 1.6; }

    @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }

    /* FOOTER */
    footer {
      text-align: center;
      padding: 28px 20px 0;
      border-top: 1px solid var(--border);
      margin-top: 40px;
    }
    footer p { font-size: 12px; color: var(--muted); line-height: 1.7; }
    footer strong { color: var(--orange); }

    .btn-admin {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      background: transparent;
      border: 1px solid var(--border);
      border-radius: 8px;
      color: var(--muted);
      font-family: 'DM Sans', sans-serif;
      font-size: 12px;
      font-weight: 600;
      letter-spacing: 0.8px;
      padding: 7px 14px;
      cursor: pointer;
      text-decoration: none;
      transition: all 0.2s;
      margin-top: 8px;
    }
    .btn-admin:hover {
      border-color: var(--orange);
      color: var(--orange);
      background: var(--orange-glow);
    }
    .btn-admin .admin-icon { font-size: 14px; }

    @media (max-width: 560px) {
      .form-grid { grid-template-columns: 1fr; }
      .services-grid { grid-template-columns: 1fr; }
      .forfait-grid { grid-template-columns: 1fr; }
      header { flex-wrap: wrap; }
      .header-right { margin-left: 0; }
    }
  </style>
</head>
<body>
<div class="wrapper">

  <!-- HEADER -->
  <header>
    <div class="logo-box" style="background:#000;box-shadow:none;width:180px;height:80px;padding:6px;border-radius:10px;">
      <img src="data:image/jpeg;base64,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zzgAAAAAABX7777777777777777777778ADygTwhjwAAADygBSyDwQTyBTwBTwhzygwQAAAAAAABX7777777777777777777778ADygTSzjwAAADzzzgADTTzAhTwATTyDzTzwgAAAAAABX7777777777777777777778AAAADBBAAAAAAAADAAABBAABACABCAAADBAAAAAAAABX777777777777777zMz7778AAgQAAAAAAAAAAQwAAAAAAAAAAADwwAAAAAAAAAAAABX777777777777zS/2b77778ADygAAAAAAAAACzAAAAAAAAAwgBDygAAAAAAAAAAAABX7777777776y/wA8he+++++/AA8oAMMIEIAoAIkkAAAA4IAI0sAAMIIMIAMMAAAAAAAV+++++++++++88oV++++++/AA8ss8gAU84oc808sI048sIc08sA8oQ8AEcgAAAAAAAV+++++++++++9F9v1+++++/AA8888AAU8wAU8Mc8gY0M8IA8oAA8oQ8oQ4AAAAAAAAV++++++++++/t+vcA/wDvvvvwAPOMLKAFPAANKOMOMPJJPKANLAAPKAMPPPAAAAAAAAFfvvvvvvvvvvvvvvvvvvvvvwAPOBPPCFPAAENLHJAPLGPKAHPOCPKAENPOAAAAAAAAEtv/AL7777777777777777j1EABCAADDBCAAADBDAADDCDCAADAADCAABDAAAAAAAAAAAADDb/77777777777j1OAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADDb/77777j1OAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADDbz1OAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAD/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" alt="La Boite Kreativ" style="height:100%;width:100%;object-fit:contain;border-radius:6px;"/>
    </div>
    <div class="logo-text">
      <h1 style="display:none;">La Boite Kreativ</h1>
      <p>Nous donnons vie à vos rêves</p>
    </div>
    <div class="header-right">
      <span class="badge">Formulaire Client</span>
      <br/>
      <a href="Admin_LaBoiteKreativ.html" class="btn-admin" title="Accéder au panneau administrateur">
        <span class="admin-icon">🔐</span> Espace Admin
      </a>
    </div>
  </header>

  <form id="clientForm" novalidate>

    <!-- 1. INFOS PERSONNELLES -->
    <div class="section-title">
      <div class="icon">👤</div>
      <h2>Informations Personnelles</h2>
      <div class="section-line"></div>
    </div>
    <div class="card">
      <div class="form-grid">
        <div class="field">
          <label>Nom complet <span class="req">*</span></label>
          <input type="text" id="nom" placeholder="Ex: Kouadio Jean-Pierre" required />
        </div>
        <div class="field">
          <label>Entreprise / Structure</label>
          <input type="text" id="entreprise" placeholder="Nom de votre entreprise" />
        </div>
        <div class="field">
          <label>Téléphone <span class="req">*</span></label>
          <input type="tel" id="telephone" placeholder="+225 07 XX XX XX XX" required />
        </div>
        <div class="field">
          <label>Email</label>
          <input type="email" id="email" placeholder="votre@email.com" />
        </div>
        <div class="field full">
          <label>Secteur d'activité</label>
          <select id="secteur">
            <option value="">-- Sélectionnez votre secteur --</option>
            <option>Commerce & Retail</option>
            <option>Restauration & Hôtellerie</option>
            <option>Immobilier & BTP</option>
            <option>Santé & Beauté</option>
            <option>Mode & Textile</option>
            <option>Technologie & Informatique</option>
            <option>Éducation & Formation</option>
            <option>Événementiel</option>
            <option>Transport & Logistique</option>
            <option>Agriculture & Agroalimentaire</option>
            <option>Services aux entreprises</option>
            <option>Autre</option>
          </select>
        </div>
      </div>
    </div>

    <!-- 2. SERVICES SOUHAITÉS -->
    <div class="section-title">
      <div class="icon">🎯</div>
      <h2>Services Souhaités</h2>
      <div class="section-line"></div>
    </div>
    <div class="card">
      <div style="font-size:12px;font-weight:700;letter-spacing:1px;color:var(--orange);text-transform:uppercase;margin-bottom:10px;">🖨️ Print &amp; Design</div>
      <div class="services-grid" id="servicesGrid" style="margin-bottom:18px;">
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Flyers" />
          <span class="sicon">🗒️</span>
          <div><span>Flyers</span><br/><span class="service-price" data-service="Flyers" style="font-size:11px;color:var(--muted);">dès 10 000 FCFA</span></div>
        </label>
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Brochures" />
          <span class="sicon">📋</span>
          <div><span>Brochures</span><br/><span class="service-price" data-service="Brochures" style="font-size:11px;color:var(--muted);">dès 30 000 FCFA</span></div>
        </label>
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Maquettes" />
          <span class="sicon">✏️</span>
          <div><span>Maquettes</span><br/><span class="service-price" data-service="Maquettes" style="font-size:11px;color:var(--muted);">dès 25 000 FCFA</span></div>
        </label>
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Carte de Visite" />
          <span class="sicon">💼</span>
          <div><span>Carte de Visite</span><br/><span class="service-price" data-service="Carte de Visite" style="font-size:11px;color:var(--muted);">dès 10 000 FCFA</span></div>
        </label>
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Affiches Publicitaires" />
          <span class="sicon">📌</span>
          <div><span>Affiches Publicitaires</span><br/><span class="service-price" data-service="Affiches Publicitaires" style="font-size:11px;color:var(--muted);">dès 10 000 FCFA</span></div>
        </label>
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Identité Visuelle" />
          <span class="sicon">🎨</span>
          <div><span>Identité Visuelle</span><br/><span class="service-price" data-service="Identité Visuelle" style="font-size:11px;color:var(--muted);">dès 80 000 FCFA</span></div>
        </label>
      </div>
      <div style="font-size:12px;font-weight:700;letter-spacing:1px;color:var(--orange);text-transform:uppercase;margin-bottom:10px;">🎬 Vidéo &amp; Audio</div>
      <div class="services-grid" style="margin-bottom:18px;">
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Réalisation de Vidéos" />
          <span class="sicon">🎬</span>
          <div><span>Réalisation Vidéo</span><br/><span class="service-price" data-service="Réalisation de Vidéos" style="font-size:11px;color:var(--muted);">dès 30 000 FCFA</span></div>
        </label>
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Vidéos avec IA" />
          <span class="sicon">🤖</span>
          <div><span>Vidéo avec IA</span><br/><span class="service-price" data-service="Vidéos avec IA" style="font-size:11px;color:var(--muted);">dès 20 000 FCFA</span></div>
        </label>
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Voix-Off" />
          <span class="sicon">🎙️</span>
          <div><span>Voix-Off</span><br/><span class="service-price" data-service="Voix-Off" style="font-size:11px;color:var(--muted);">dès 15 000 FCFA</span></div>
        </label>
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Prise de vue Drone" />
          <span class="sicon">🚁</span>
          <div><span>Drone</span><br/><span class="service-price" data-service="Prise de vue Drone" style="font-size:11px;color:var(--muted);">dès 75 000 FCFA</span></div>
        </label>
      </div>
      <div style="font-size:12px;font-weight:700;letter-spacing:1px;color:var(--orange);text-transform:uppercase;margin-bottom:10px;">📱 Réseaux &amp; Événementiel</div>
      <div class="services-grid">
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Gestion de Pages" />
          <span class="sicon">📱</span>
          <div><span>Gestion de Pages</span><br/><span class="service-price" data-service="Gestion de Pages" style="font-size:11px;color:var(--muted);">dès 50 000 FCFA/mois</span></div>
        </label>
        <label class="service-check" onclick="toggleService(this)">
          <input type="checkbox" name="services" value="Couverture Événementielle" />
          <span class="sicon">🎪</span>
          <div><span>Couverture Événementielle</span><br/><span class="service-price" data-service="Couverture Événementielle" style="font-size:11px;color:var(--muted);">dès 50 000 FCFA</span></div>
        </label>
      </div>
    </div>

    <!-- 3. FORFAIT -->
    <div class="section-title">
      <div class="icon">⭐</div>
      <h2>Forfait Souhaité</h2>
      <div class="section-line"></div>
    </div>
    <div class="card">
      <div class="forfait-grid" id="forfaitGrid">
        <div class="forfait-card" onclick="selectForfait(this, 'Base')">
          <input type="radio" name="forfait" value="Base" />
          <div class="fname">BASE</div>
          <div class="fdesc" style="margin-bottom:8px;">Essentiel, livraison standard</div>
          <div style="font-size:11px;color:var(--muted);line-height:1.8;text-align:left;">
            🗒️ Flyers dès <b style="color:var(--orange)">10 000</b><br/>
            📋 Brochures dès <b style="color:var(--orange)">30 000</b><br/>
            🎬 Vidéo dès <b style="color:var(--orange)">30 000</b><br/>
            📱 Pages dès <b style="color:var(--orange)">50 000</b>/mois<br/>
            🎪 Événement dès <b style="color:var(--orange)">50 000</b>
          </div>
        </div>
        <div class="forfait-card" onclick="selectForfait(this, 'Standard')">
          <input type="radio" name="forfait" value="Standard" />
          <div class="fname">STANDARD</div>
          <div class="fdesc" style="margin-bottom:8px;">Qualité supérieure, révisions incluses</div>
          <div style="font-size:11px;color:var(--muted);line-height:1.8;text-align:left;">
            🗒️ Flyers dès <b style="color:var(--orange)">30 000</b><br/>
            📋 Brochures dès <b style="color:var(--orange)">65 000</b><br/>
            🎬 Vidéo dès <b style="color:var(--orange)">200 000</b><br/>
            📱 Pages dès <b style="color:var(--orange)">100 000</b>/mois<br/>
            🎪 Événement dès <b style="color:var(--orange)">100 000</b>
          </div>
        </div>
        <div class="forfait-card" onclick="selectForfait(this, 'Premium')">
          <span class="badge-top">⭐ TOP</span>
          <input type="radio" name="forfait" value="Premium" />
          <div class="fname">PREMIUM</div>
          <div class="fdesc" style="margin-bottom:8px;">Haut de gamme, révisions illimitées</div>
          <div style="font-size:11px;color:var(--muted);line-height:1.8;text-align:left;">
            🗒️ Flyers dès <b style="color:var(--orange)">50 000</b><br/>
            📋 Brochures dès <b style="color:var(--orange)">120 000</b><br/>
            🎬 Vidéo dès <b style="color:var(--orange)">400 000</b><br/>
            📱 Pages dès <b style="color:var(--orange)">200 000</b>/mois<br/>
            🎪 Événement dès <b style="color:var(--orange)">180 000</b>
          </div>
        </div>
      </div>
      <p style="font-size:11px;color:var(--muted);margin-top:14px;text-align:center;">💡 Tarifs en FCFA. Devis personnalisé disponible. Tarifs négociables pour projets long terme.</p>
    </div>

    <!-- 4. BUDGET -->
    <div class="section-title">
      <div class="icon">💰</div>
      <h2>Budget Estimé</h2>
      <div class="section-line"></div>
    </div>
    <div class="card">
      <div id="budgetForfaitBadge" style="font-size:11px;color:var(--muted);margin-bottom:10px;text-align:center;letter-spacing:1px;">
        🎯 Sélectionnez un forfait pour adapter la plage de budget
      </div>
      <div class="budget-display" id="budgetDisplay">50 000 <span>FCFA</span></div>
      <input type="range" id="budgetSlider" min="10000" max="500000" step="5000" value="50000"
        oninput="updateBudget(this.value)" />
      <div class="range-labels">
        <span>10 000 FCFA</span>
        <span>250 000 FCFA</span>
        <span>500 000+ FCFA</span>
      </div>
    </div>

    <!-- 5. DÉLAI -->
    <div class="section-title">
      <div class="icon">📅</div>
      <h2>Délai Souhaité</h2>
      <div class="section-line"></div>
    </div>
    <div class="card">
      <div class="form-grid">
        <div class="field">
          <label>Délai de livraison</label>
          <select id="delai">
            <option value="">-- Sélectionnez un délai --</option>
            <option>Urgent (24–48h)</option>
            <option>Rapide (3–5 jours)</option>
            <option>Normal (1–2 semaines)</option>
            <option>Flexible (+ de 2 semaines)</option>
          </select>
        </div>
        <div class="field">
          <label>Date de début souhaitée</label>
          <input type="date" id="dateDebut" />
        </div>
      </div>
    </div>

    <!-- 6. DESCRIPTION DU PROJET -->
    <div class="section-title">
      <div class="icon">📝</div>
      <h2>Description du Projet</h2>
      <div class="section-line"></div>
    </div>
    <div class="card">
      <div class="field">
        <label>Décrivez votre projet <span class="req">*</span></label>
        <textarea id="description" maxlength="800" required
          placeholder="Décrivez votre projet en détail : objectif, cible visée, style souhaité, références éventuelles..."
          oninput="updateChar(this)"></textarea>
        <div class="char-count" id="charCount">0 / 800 caractères</div>
      </div>
    </div>

    <!-- 7. COMMENT VOUS AVEZ CONNU L'AGENCE -->
    <div class="section-title">
      <div class="icon">📣</div>
      <h2>Comment nous avez-vous connus ?</h2>
      <div class="section-line"></div>
    </div>
    <div class="card">
      <div class="source-grid" id="sourceGrid">
        <div class="source-tag" onclick="toggleSource(this)">📸 Instagram</div>
        <div class="source-tag" onclick="toggleSource(this)">🎵 TikTok</div>
        <div class="source-tag" onclick="toggleSource(this)">👍 Facebook</div>
        <div class="source-tag" onclick="toggleSource(this)">💼 LinkedIn</div>
        <div class="source-tag" onclick="toggleSource(this)">🗣️ Bouche à oreille</div>
        <div class="source-tag" onclick="toggleSource(this)">🔍 Google</div>
        <div class="source-tag" onclick="toggleSource(this)">📲 WhatsApp</div>
        <div class="source-tag" onclick="toggleSource(this)">🎪 Événement</div>
        <div class="source-tag" onclick="toggleSource(this)">👥 Recommandation</div>
        <div class="source-tag" onclick="toggleSource(this)">Autre</div>
      </div>
    </div>

    <!-- 8. LOGO DU CLIENT -->
    <div class="section-title">
      <div class="icon">🖼️</div>
      <h2>Logo de votre Entreprise</h2>
      <div class="section-line"></div>
    </div>
    <div class="card">
      <div class="logo-upload-zone" id="logoZone">
        <input type="file" id="logoFile" accept="image/*" onchange="handleLogoUpload(this)" />
        <div class="upload-icon">📁</div>
        <div class="upload-text">
          <strong>Cliquez pour importer votre logo</strong><br/>
          PNG, JPG, SVG acceptés — max 5 Mo
        </div>
      </div>
      <div class="logo-preview" id="logoPreview">
        <img id="logoPreviewImg" src="" alt="Logo client" />
        <span class="logo-filename" id="logoFilename"></span>
        <button type="button" class="logo-remove" onclick="removeLogo()" title="Supprimer">✕</button>
      </div>
      <p style="font-size:11px;color:var(--muted);margin-top:10px;">💡 Votre logo nous aide à adapter nos créations à votre identité visuelle.</p>
    </div>

    <!-- 9. COULEURS DE L'ENTREPRISE -->
    <div class="section-title">
      <div class="icon">🎨</div>
      <h2>Couleurs de votre Entreprise</h2>
      <div class="section-line"></div>
    </div>
    <div class="card">
      <div class="colors-grid">
        <div class="color-field">
          <label>Couleur principale</label>
          <div class="color-input-wrap">
            <input type="color" id="couleurPrincipale" value="#F5A623" oninput="syncColorText('couleurPrincipale','couleurPrincipaleHex')" />
            <input type="text" id="couleurPrincipaleHex" value="#F5A623" maxlength="7" placeholder="#000000" oninput="syncColorPicker('couleurPrincipale','couleurPrincipaleHex')" />
          </div>
        </div>
        <div class="color-field">
          <label>Couleur secondaire</label>
          <div class="color-input-wrap">
            <input type="color" id="couleurSecondaire" value="#111111" oninput="syncColorText('couleurSecondaire','couleurSecondaireHex')" />
            <input type="text" id="couleurSecondaireHex" value="#111111" maxlength="7" placeholder="#000000" oninput="syncColorPicker('couleurSecondaire','couleurSecondaireHex')" />
          </div>
        </div>
        <div class="color-field">
          <label>Couleur d'accent</label>
          <div class="color-input-wrap">
            <input type="color" id="couleurAccent" value="#FFFFFF" oninput="syncColorText('couleurAccent','couleurAccentHex')" />
            <input type="text" id="couleurAccentHex" value="#FFFFFF" maxlength="7" placeholder="#000000" oninput="syncColorPicker('couleurAccent','couleurAccentHex')" />
          </div>
        </div>
        <div class="color-field">
          <label>Couleur de fond</label>
          <div class="color-input-wrap">
            <input type="color" id="couleurFond" value="#F0F0F0" oninput="syncColorText('couleurFond','couleurFondHex')" />
            <input type="text" id="couleurFondHex" value="#F0F0F0" maxlength="7" placeholder="#000000" oninput="syncColorPicker('couleurFond','couleurFondHex')" />
          </div>
        </div>
      </div>
      <p style="font-size:11px;color:var(--muted);margin-top:14px;">💡 Choisissez les couleurs via le sélecteur ou saisissez un code hexadécimal (ex: #FF5733)</p>
      <div style="margin-top:12px;">
        <label style="font-size:12px;font-weight:700;letter-spacing:1px;color:var(--muted);text-transform:uppercase;">Teintes rapides</label>
        <div class="color-swatch-row" id="swatchRow">
          <div class="color-swatch" style="background:#E74C3C" title="#E74C3C" onclick="applySwatchColor('#E74C3C')"></div>
          <div class="color-swatch" style="background:#E67E22" title="#E67E22" onclick="applySwatchColor('#E67E22')"></div>
          <div class="color-swatch" style="background:#F1C40F" title="#F1C40F" onclick="applySwatchColor('#F1C40F')"></div>
          <div class="color-swatch" style="background:#2ECC71" title="#2ECC71" onclick="applySwatchColor('#2ECC71')"></div>
          <div class="color-swatch" style="background:#1ABC9C" title="#1ABC9C" onclick="applySwatchColor('#1ABC9C')"></div>
          <div class="color-swatch" style="background:#3498DB" title="#3498DB" onclick="applySwatchColor('#3498DB')"></div>
          <div class="color-swatch" style="background:#9B59B6" title="#9B59B6" onclick="applySwatchColor('#9B59B6')"></div>
          <div class="color-swatch" style="background:#E91E8C" title="#E91E8C" onclick="applySwatchColor('#E91E8C')"></div>
          <div class="color-swatch" style="background:#000000" title="#000000" onclick="applySwatchColor('#000000')"></div>
          <div class="color-swatch" style="background:#FFFFFF;border:1px solid #444;" title="#FFFFFF" onclick="applySwatchColor('#FFFFFF')"></div>
        </div>
        <p style="font-size:10px;color:var(--muted);margin-top:5px;">Cliquez sur une teinte pour l'appliquer à la couleur principale</p>
      </div>
    </div>

    <!-- 10. RÉSEAUX SOCIAUX -->
    <div class="section-title">
      <div class="icon">🌐</div>
      <h2>Réseaux Sociaux & Web</h2>
      <div class="section-line"></div>
    </div>
    <div class="card">
      <div class="social-grid">
        <div class="social-field">
          <label>Facebook</label>
          <div class="social-input-wrap">
            <span class="social-icon">👍</span>
            <input type="url" id="socialFacebook" placeholder="https://facebook.com/votreprofil" />
          </div>
        </div>
        <div class="social-field">
          <label>Instagram</label>
          <div class="social-input-wrap">
            <span class="social-icon">📸</span>
            <input type="url" id="socialInstagram" placeholder="https://instagram.com/votreprofil" />
          </div>
        </div>
        <div class="social-field">
          <label>TikTok</label>
          <div class="social-input-wrap">
            <span class="social-icon">🎵</span>
            <input type="url" id="socialTiktok" placeholder="https://tiktok.com/@votreprofil" />
          </div>
        </div>
        <div class="social-field">
          <label>LinkedIn</label>
          <div class="social-input-wrap">
            <span class="social-icon">💼</span>
            <input type="url" id="socialLinkedin" placeholder="https://linkedin.com/in/votreprofil" />
          </div>
        </div>
        <div class="social-field">
          <label>WhatsApp Business</label>
          <div class="social-input-wrap">
            <span class="social-icon">📲</span>
            <input type="tel" id="socialWhatsapp" placeholder="+225 07 XX XX XX XX" />
          </div>
        </div>
        <div class="social-field">
          <label>Site Web</label>
          <div class="social-input-wrap">
            <span class="social-icon">🌍</span>
            <input type="url" id="socialSite" placeholder="https://www.votresite.com" />
          </div>
        </div>
      </div>
      <p style="font-size:11px;color:var(--muted);margin-top:14px;">💡 Ces informations nous permettent d'adapter nos créations à votre présence en ligne.</p>
    </div>

    <!-- SUBMIT -->

    <div class="submit-area">
      <button type="submit" class="btn-submit">ENVOYER MA DEMANDE →</button>
      <p class="submit-note">
        Nous vous contacterons dans les <strong style="color:var(--orange)">24 heures</strong> suivant votre demande.<br/>
        +225 07 68 86 27 44 &nbsp;|&nbsp; +225 07 49 39 44 66
      </p>
    </div>

    <!-- SUCCESS -->
    <div class="success-msg" id="successMsg">
      <div class="tick">✅</div>
      <h3>Demande Envoyée !</h3>
      <p>Merci pour votre confiance.<br/>Notre équipe vous contactera dans les <strong>24 heures</strong>.</p>
    </div>

  </form>

  <footer>
    <p>
      <strong>La Boite Kreativ</strong> — Abidjan, Côte d'Ivoire<br/>
      +225 07 68 86 27 44 &nbsp;/&nbsp; +225 07 49 39 44 66
    </p>
  </footer>

</div>

<script>
  function toggleService(label) {
    label.classList.toggle('checked');
  }

  // Prix des services par forfait
  const servicePrices = {
    'Base': {
      'Flyers':                   'dès 10 000 FCFA',
      'Brochures':                'dès 30 000 FCFA',
      'Maquettes':                'dès 25 000 FCFA',
      'Carte de Visite':          'dès 10 000 FCFA',
      'Affiches Publicitaires':   'dès 10 000 FCFA',
      'Identité Visuelle':        'dès 80 000 FCFA',
      'Réalisation de Vidéos':    'dès 30 000 FCFA',
      'Vidéos avec IA':           'dès 20 000 FCFA',
      'Voix-Off':                 'dès 15 000 FCFA',
      'Prise de vue Drone':       'dès 75 000 FCFA',
      'Gestion de Pages':         'dès 50 000 FCFA/mois',
      'Couverture Événementielle':'dès 50 000 FCFA',
    },
    'Standard': {
      'Flyers':                   'dès 30 000 FCFA',
      'Brochures':                'dès 65 000 FCFA',
      'Maquettes':                'dès 50 000 FCFA',
      'Carte de Visite':          'dès 25 000 FCFA',
      'Affiches Publicitaires':   'dès 25 000 FCFA',
      'Identité Visuelle':        'dès 150 000 FCFA',
      'Réalisation de Vidéos':    'dès 200 000 FCFA',
      'Vidéos avec IA':           'dès 80 000 FCFA',
      'Voix-Off':                 'dès 40 000 FCFA',
      'Prise de vue Drone':       'dès 150 000 FCFA',
      'Gestion de Pages':         'dès 100 000 FCFA/mois',
      'Couverture Événementielle':'dès 100 000 FCFA',
    },
    'Premium': {
      'Flyers':                   'dès 50 000 FCFA',
      'Brochures':                'dès 120 000 FCFA',
      'Maquettes':                'dès 100 000 FCFA',
      'Carte de Visite':          'dès 50 000 FCFA',
      'Affiches Publicitaires':   'dès 50 000 FCFA',
      'Identité Visuelle':        'dès 300 000 FCFA',
      'Réalisation de Vidéos':    'dès 400 000 FCFA',
      'Vidéos avec IA':           'dès 150 000 FCFA',
      'Voix-Off':                 'dès 80 000 FCFA',
      'Prise de vue Drone':       'dès 250 000 FCFA',
      'Gestion de Pages':         'dès 200 000 FCFA/mois',
      'Couverture Événementielle':'dès 180 000 FCFA',
    }
  };

  function updateServicePrices(forfait) {
    const prices = servicePrices[forfait];
    if (!prices) return;
    document.querySelectorAll('.service-price').forEach(el => {
      const key = el.getAttribute('data-service');
      if (prices[key]) {
        el.textContent = prices[key];
        el.style.transition = 'color 0.25s';
        el.style.color = 'var(--orange)';
        setTimeout(() => { el.style.color = 'var(--muted)'; }, 700);
      }
    });
  }

  // Plages de budget par forfait
  const forfaitBudgets = {
    'Base':     { min: 10000,  max: 100000, step: 5000,  default: 30000  },
    'Standard': { min: 30000,  max: 300000, step: 10000, default: 100000 },
    'Premium':  { min: 50000,  max: 600000, step: 25000, default: 200000 },
    'default':  { min: 10000,  max: 500000, step: 5000,  default: 50000  }
  };

  function selectForfait(el, val) {
    document.querySelectorAll('.forfait-card').forEach(c => c.classList.remove('selected'));
    el.classList.add('selected');
    el.querySelector('input[type="radio"]').checked = true;
    // Mettre à jour les prix des services
    updateServicePrices(val);


    // Adapter le slider budget au forfait choisi
    const cfg = forfaitBudgets[val] || forfaitBudgets['default'];
    const slider = document.getElementById('budgetSlider');
    slider.min   = cfg.min;
    slider.max   = cfg.max;
    slider.step  = cfg.step;
    slider.value = cfg.default;

    // Mettre à jour les labels de plage
    const labels = document.querySelectorAll('.range-labels span');
    labels[0].textContent = cfg.min.toLocaleString('fr-FR') + ' FCFA';
    labels[1].textContent = Math.round((cfg.min + cfg.max) / 2).toLocaleString('fr-FR') + ' FCFA';
    labels[2].textContent = cfg.max.toLocaleString('fr-FR') + '+ FCFA';

    // Mettre à jour l'affichage du budget
    updateBudget(cfg.default);

    // Mettre à jour le badge forfait actif
    const badges = { 'Base': '🟡 Forfait BASE activé', 'Standard': '🟠 Forfait STANDARD activé', 'Premium': '⭐ Forfait PREMIUM activé' };
    document.getElementById('budgetForfaitBadge').innerHTML =
      `<span style="color:var(--orange);font-weight:700;">${badges[val] || val}</span> &nbsp;—&nbsp; Plage : <b>${cfg.min.toLocaleString('fr-FR')}</b> → <b>${cfg.max.toLocaleString('fr-FR')} FCFA</b>`;

    // Petite animation de feedback
    const budgetSection = document.getElementById('budgetDisplay');
    budgetSection.style.transition = 'transform 0.15s, opacity 0.15s';
    budgetSection.style.transform = 'scale(1.08)';
    budgetSection.style.opacity = '0.7';
    setTimeout(() => {
      budgetSection.style.transform = 'scale(1)';
      budgetSection.style.opacity = '1';
    }, 180);
  }

  function updateBudget(val) {
    const num = parseInt(val).toLocaleString('fr-FR');
    document.getElementById('budgetDisplay').innerHTML = `${num} <span>FCFA</span>`;
    const slider = document.getElementById('budgetSlider');
    const min = parseInt(slider.min);
    const max = parseInt(slider.max);
    const pct = ((val - min) / (max - min)) * 100;
    slider.style.background =
      `linear-gradient(to right, var(--orange) 0%, var(--orange) ${pct}%, #333 ${pct}%)`;
  }

  function updateChar(el) {
    document.getElementById('charCount').textContent = `${el.value.length} / 800 caractères`;
  }

  function toggleSource(el) {
    el.classList.toggle('selected');
  }

  // ===== LOGO =====
  function handleLogoUpload(input) {
    if (!input.files || !input.files[0]) return;
    const file = input.files[0];
    if (file.size > 5 * 1024 * 1024) { alert('⚠️ Le fichier est trop lourd (max 5 Mo).'); return; }
    const reader = new FileReader();
    reader.onload = function(e) {
      document.getElementById('logoPreviewImg').src = e.target.result;
      document.getElementById('logoFilename').textContent = file.name;
      document.getElementById('logoPreview').classList.add('show');
      document.getElementById('logoZone').style.borderColor = 'var(--orange)';
      document.getElementById('logoZone').style.background = 'var(--orange-glow)';
    };
    reader.readAsDataURL(file);
  }
  function removeLogo() {
    document.getElementById('logoFile').value = '';
    document.getElementById('logoPreviewImg').src = '';
    document.getElementById('logoPreview').classList.remove('show');
    document.getElementById('logoZone').style.borderColor = '';
    document.getElementById('logoZone').style.background = '';
  }

  // ===== COULEURS =====
  function syncColorText(pickerId, hexId) {
    document.getElementById(hexId).value = document.getElementById(pickerId).value;
  }
  function syncColorPicker(pickerId, hexId) {
    const val = document.getElementById(hexId).value;
    if (/^#[0-9A-Fa-f]{6}$/.test(val)) {
      document.getElementById(pickerId).value = val;
    }
  }
  let swatchTarget = 'couleurPrincipale';
  function applySwatchColor(hex) {
    document.getElementById(swatchTarget).value = hex;
    document.getElementById(swatchTarget + 'Hex').value = hex;
  }
  document.querySelectorAll('.color-input-wrap input[type="color"]').forEach(el => {
    el.addEventListener('focus', () => { swatchTarget = el.id; });
  });

  document.getElementById('clientForm').addEventListener('submit', function(e) {
    e.preventDefault();

    const nom = document.getElementById('nom').value.trim();
    const tel = document.getElementById('telephone').value.trim();
    const desc = document.getElementById('description').value.trim();

    if (!nom || !tel || !desc) {
      alert('⚠️ Veuillez remplir les champs obligatoires : Nom, Téléphone et Description du projet.');
      return;
    }

    // Collect data
    const entreprise = document.getElementById('entreprise').value.trim();
    const email = document.getElementById('email').value.trim();
    const secteur = document.getElementById('secteur').value;
    const delai = document.getElementById('delai').value;
    const dateDebut = document.getElementById('dateDebut').value;
    const budget = document.getElementById('budgetDisplay').innerText.replace('\n', ' ');

    const services = [...document.querySelectorAll('input[name="services"]:checked')]
      .map(c => c.value).join(', ') || 'Non précisé';

    const forfait = document.querySelector('input[name="forfait"]:checked');
    const forfaitVal = forfait ? forfait.value : 'Non sélectionné';

    const sources = [...document.querySelectorAll('.source-tag.selected')]
      .map(s => s.innerText).join(', ') || 'Non précisé';

    const logoFile = document.getElementById('logoFile');
    const logoName = (logoFile && logoFile.files[0]) ? logoFile.files[0].name : 'Non fourni';

    const couleurPrincipale = document.getElementById('couleurPrincipaleHex').value || 'Non précisé';
    const couleurSecondaire = document.getElementById('couleurSecondaireHex').value || 'Non précisé';
    const couleurAccent = document.getElementById('couleurAccentHex').value || 'Non précisé';
    const couleurFond = document.getElementById('couleurFondHex').value || 'Non précisé';

    const facebook = document.getElementById('socialFacebook').value.trim() || 'Non précisé';
    const instagram = document.getElementById('socialInstagram').value.trim() || 'Non précisé';
    const tiktok = document.getElementById('socialTiktok').value.trim() || 'Non précisé';
    const linkedin = document.getElementById('socialLinkedin').value.trim() || 'Non précisé';
    const whatsappBiz = document.getElementById('socialWhatsapp').value.trim() || 'Non précisé';
    const siteWeb = document.getElementById('socialSite').value.trim() || 'Non précisé';

    // Build WhatsApp message
    const msg =
`🟧 *NOUVELLE DEMANDE CLIENT*
━━━━━━━━━━━━━━━━━━━━
👤 *Nom :* ${nom}
🏢 *Entreprise :* ${entreprise || 'Non précisé'}
📞 *Téléphone :* ${tel}
📧 *Email :* ${email || 'Non précisé'}
🏭 *Secteur :* ${secteur || 'Non précisé'}

━━━━━━━━━━━━━━━━━━━━
🎯 *Services souhaités :*
${services}

⭐ *Forfait :* ${forfaitVal}
💰 *Budget :* ${budget}
📅 *Délai :* ${delai || 'Non précisé'}
🗓️ *Date de début :* ${dateDebut || 'Non précisé'}

━━━━━━━━━━━━━━━━━━━━
📝 *Description du projet :*
${desc}

📣 *Connu via :* ${sources}

━━━━━━━━━━━━━━━━━━━━
🖼️ *Logo fourni :* ${logoName}

🎨 *Couleurs de l'entreprise :*
  • Principale : ${couleurPrincipale}
  • Secondaire : ${couleurSecondaire}
  • Accent : ${couleurAccent}
  • Fond : ${couleurFond}

🌐 *Réseaux sociaux & Web :*
  • Facebook : ${facebook}
  • Instagram : ${instagram}
  • TikTok : ${tiktok}
  • LinkedIn : ${linkedin}
  • WhatsApp Business : ${whatsappBiz}
  • Site Web : ${siteWeb}
━━━━━━━━━━━━━━━━━━━━
_Formulaire La Boite Kreativ_`;

    // ===== SAUVEGARDE DANS LE PANEL ADMIN =====
    function uid() {
      return Date.now().toString(36) + Math.random().toString(36).substr(2, 5);
    }
    function fmtDate(d) {
      return d.toLocaleDateString('fr-FR', { day: '2-digit', month: '2-digit', year: 'numeric' });
    }
    function getData() {
      try { return JSON.parse(localStorage.getItem('lbk_demandes') || '[]'); } catch { return []; }
    }
    function setData(arr) {
      localStorage.setItem('lbk_demandes', JSON.stringify(arr));
    }

    const newDemande = {
      id: uid(),
      date: fmtDate(new Date()),
      nom,
      entreprise: entreprise || '',
      tel,
      email: email || '',
      secteur: secteur || '',
      services: services !== 'Non précisé' ? services : '',
      forfait: forfaitVal !== 'Non sélectionné' ? forfaitVal : '',
      budget,
      delai: delai || '',
      dateDebut: dateDebut || '',
      description: desc,
      couleur1: couleurPrincipale !== 'Non précisé' ? couleurPrincipale : '',
      couleur2: couleurSecondaire !== 'Non précisé' ? couleurSecondaire : '',
      couleurAccent: couleurAccent !== 'Non précisé' ? couleurAccent : '',
      couleurFond: couleurFond !== 'Non précisé' ? couleurFond : '',
      facebook: facebook !== 'Non précisé' ? facebook : '',
      instagram: instagram !== 'Non précisé' ? instagram : '',
      tiktok: tiktok !== 'Non précisé' ? tiktok : '',
      linkedin: linkedin !== 'Non précisé' ? linkedin : '',
      whatsappBiz: whatsappBiz !== 'Non précisé' ? whatsappBiz : '',
      site: siteWeb !== 'Non précisé' ? siteWeb : '',
      source: sources !== 'Non précisé' ? sources : '',
      logoNom: logoName,
      statut: 'Nouveau',
      notes: '',
    };
    const existingData = getData();
    existingData.push(newDemande);
    setData(existingData);
    // ===== FIN SAUVEGARDE =====

    // Envoyer aux 2 numéros WhatsApp
    const phones = ['2250768862744', '2250749394466'];
    phones.forEach(phone => window.open(`https://wa.me/${phone}?text=${encodeURIComponent(msg)}`, '_blank'));

    // Envoyer par Email (Gmail)
    const subject = encodeURIComponent('🟧 Nouvelle demande client - La Boite Kreativ');
    const body = encodeURIComponent(msg);
    window.open(`https://mail.google.com/mail/?view=cm&fs=1&to=laboiteKreativ@gmail.com&su=${subject}&body=${body}`, '_blank');

    // Show success
    document.getElementById('successMsg').classList.add('show');
    document.querySelector('.submit-area').style.display = 'none';
    document.getElementById('successMsg').scrollIntoView({ behavior: 'smooth' });
  });
</script>
</body>
</html>
