#   
<!DOCTYPE html>  
<html lang="en">  
<head>  
  <meta charset="UTF-8" />  
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />  
  <title>Sprinkled Nutella — AR Menu</title>  
  <script type="module" src="https://ajax.googleapis.com/ajax/libs/model-viewer/3.4.0/model-viewer.min.js"></script>  
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">  
  <style>  
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }  
  
    :root {  
      --cream: #fdf6ec;  
      --warm-white: #fefaf4;  
      --brown-dark: #3b1f0e;  
      --brown-mid: #7a4528;  
      --brown-light: #c4865a;  
      --caramel: #e8a96a;  
      --sprinkle-pink: #f4a0b5;  
      --sprinkle-blue: #a0c4f4;  
      --sprinkle-green: #a0e0b0;  
      --nutella: #6b3422;  
    }  
  
    html, body {  
      height: 100%;  
      background: var(--cream);  
      font-family: 'DM Sans', sans-serif;  
      color: var(--brown-dark);  
      overflow-x: hidden;  
    }  
  
    body::before {  
      content: '';  
      position: fixed;  
      inset: 0;  
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.03'/%3E%3C/svg%3E");  
      pointer-events: none;  
      z-index: 100;  
      opacity: 0.4;  
    }  
  
    .blob { position: fixed; border-radius: 50%; filter: blur(80px); opacity: 0.18; pointer-events: none; z-index: 0; }  
    .blob-1 { width: 400px; height: 400px; background: var(--caramel); top: -100px; right: -100px; }  
    .blob-2 { width: 300px; height: 300px; background: var(--brown-light); bottom: 100px; left: -80px; }  
  
    .page { position: relative; z-index: 1; min-height: 100vh; display: flex; flex-direction: column; align-items: center; padding: 0 0 60px 0; }  
  
    .header { width: 100%; padding: 28px 28px 0; display: flex; justify-content: space-between; align-items: center; animation: fadeDown 0.6s ease both; }  
    .brand-tag { font-family: 'DM Sans', sans-serif; font-size: 11px; font-weight: 500; letter-spacing: 0.2em; text-transform: uppercase; color: var(--brown-light); background: rgba(196,134,90,0.12); padding: 6px 14px; border-radius: 20px; }  
    .menu-badge { font-size: 11px; font-weight: 500; letter-spacing: 0.15em; text-transform: uppercase; color: var(--brown-mid); opacity: 0.6; }  
  
    .viewer-wrap { width: 100%; max-width: 480px; padding: 0 20px; margin-top: 24px; animation: fadeUp 0.7s 0.1s ease both; }  
    model-viewer { width: 100%; height: 360px; background: transparent; border-radius: 28px; --progress-bar-color: var(--caramel); --progress-mask: transparent; }  
    model-viewer::part(default-ar-button) { display: none; }  
  
    .sprinkles-deco { display: flex; justify-content: center; gap: 8px; margin-top: 16px; animation: fadeUp 0.7s 0.2s ease both; }  
    .sprinkle { width: 28px; height: 8px; border-radius: 4px; }  
    .s1 { background: var(--sprinkle-pink); transform: rotate(-20deg); }  
    .s2 { background: var(--sprinkle-blue); transform: rotate(15deg); }  
    .s3 { background: var(--sprinkle-green); transform: rotate(-10deg); }  
    .s4 { background: var(--caramel); transform: rotate(25deg); }  
    .s5 { background: var(--sprinkle-pink); transform: rotate(-30deg); }  
  
    .dish-name { font-family: 'Playfair Display', serif; font-size: 38px; font-weight: 700; color: var(--brown-dark); text-align: center; line-height: 1.1; padding: 0 28px; margin-top: 20px; animation: fadeUp 0.7s 0.25s ease both; }  
    .dish-name span { font-style: italic; color: var(--brown-mid); }  
    .taste-line { font-size: 14px; color: var(--brown-light); text-align: center; margin-top: 8px; letter-spacing: 0.04em; animation: fadeUp 0.7s 0.3s ease both; }  
  
    .info-card { width: calc(100% - 40px); max-width: 440px; background: var(--warm-white); border-radius: 24px; margin-top: 28px; padding: 28px; box-shadow: 0 4px 40px rgba(59,31,14,0.07), 0 1px 4px rgba(59,31,14,0.05); border: 1px solid rgba(196,134,90,0.15); animation: fadeUp 0.7s 0.35s ease both; }  
    .info-section { margin-bottom: 24px; }  
    .info-section:last-child { margin-bottom: 0; }  
    .info-label { font-size: 10px; font-weight:  
