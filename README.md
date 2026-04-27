<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Tharaka Prasad — Developer Profile</title>
  <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }

    body {
      background: #010409;
      color: #e6edf3;
      font-family: 'Fira Code', monospace;
      min-height: 100vh;
      padding: 2rem 1rem;
    }

    .container {
      max-width: 860px;
      margin: 0 auto;
      background: #0d1117;
      border-radius: 14px;
      padding: 2rem 2rem;
      border: 1px solid #21262d;
    }

    .terminal-bar {
      display: flex; align-items: center; gap: 6px;
      margin-bottom: 2rem;
    }
    .dot { width: 13px; height: 13px; border-radius: 50%; }
    .dot-red { background: #ff5f56; }
    .dot-yellow { background: #ffbd2e; }
    .dot-green { background: #27c93f; }
    .terminal-title { margin-left: 12px; font-size: 13px; color: #6e7681; }

    .hero { margin-bottom: 2rem; }
    .prompt-line { display: flex; align-items: center; gap: 8px; font-size: 13px; color: #6e7681; margin-bottom: 0.4rem; }
    .prompt-symbol { color: #27c93f; font-weight: 700; }
    .hero-name { font-family: 'Space Mono', monospace; font-size: 2.4rem; font-weight: 700; color: #58a6ff; letter-spacing: -1px; }
    .hero-role { font-size: 0.9rem; color: #8b949e; margin-top: 6px; }
    .hero-role span { color: #79c0ff; }
    .hero-location { font-size: 0.8rem; color: #6e7681; margin-top: 8px; }
    .hero-location span { color: #3fb950; }

    .blink { animation: blink 1s step-end infinite; }
    @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }

    .stats-row { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; margin-bottom: 2rem; }
    .stat-card { background: #161b22; border: 1px solid #21262d; border-radius: 8px; padding: 12px; text-align: center; }
    .stat-number { font-size: 1.6rem; font-weight: 700; }
    .stat-label { font-size: 11px; color: #6e7681; margin-top: 2px; }

    .section { margin-bottom: 2rem; }
    .section-header { display: flex; align-items: center; gap: 8px; margin-bottom: 1rem; font-size: 0.75rem; color: #6e7681; text-transform: uppercase; letter-spacing: 2px; }
    .section-header::after { content: ''; flex: 1; height: 1px; background: #21262d; }

    .skills-grid { display: flex; flex-wrap: wrap; gap: 8px; }
    .skill-tag {
      font-size: 12px; padding: 4px 12px; border-radius: 4px;
      border: 1px solid; font-family: 'Fira Code', monospace;
      transition: transform 0.15s, box-shadow 0.15s;
    }
    .skill-tag:hover { transform: translateY(-2px); box-shadow: 0 4px 12px rgba(0,0,0,0.4); }
    .tag-c { background: #0d2137; color: #79c0ff; border-color: #1f4b6e; }
    .tag-py { background: #12261a; color: #3fb950; border-color: #1f5032; }
    .tag-php { background: #1e1040; color: #bc8cff; border-color: #4b2ea0; }
    .tag-js { background: #2a2000; color: #e3b341; border-color: #5a4000; }
    .tag-react { background: #001a2a; color: #58a6ff; border-color: #1a4060; }
    .tag-db { background: #2a0a0a; color: #f85149; border-color: #5a1a1a; }
    .tag-tool { background: #1a1a1a; color: #8b949e; border-color: #333; }
    .tag-java { background: #2a1000; color: #ff8c00; border-color: #5a2800; }

    .projects-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 12px; }
    .project-card {
      background: #161b22; border: 1px solid #21262d; border-radius: 8px; padding: 14px 16px;
      transition: border-color 0.2s, transform 0.2s;
    }
    .project-card:hover { border-color: #58a6ff; transform: translateY(-3px); }
    .project-name { font-size: 14px; font-weight: 500; color: #58a6ff; margin-bottom: 6px; }
    .project-desc { font-size: 12px; color: #8b949e; line-height: 1.6; }
    .project-tags { display: flex; flex-wrap: wrap; gap: 4px; margin-top: 10px; }
    .project-lang { font-size: 11px; padding: 2px 7px; border-radius: 3px; background: #21262d; color: #8b949e; }

    .cert-list { display: flex; flex-direction: column; gap: 8px; }
    .cert-item { display: flex; align-items: flex-start; gap: 12px; background: #161b22; border: 1px solid #21262d; border-radius: 6px; padding: 12px 14px; }
    .cert-icon { font-size: 16px; width: 22px; text-align: center; }
    .cert-name { font-size: 13px; color: #e6edf3; }
    .cert-sub { font-size: 11px; color: #8b949e; margin-top: 2px; }

    .exp-list { display: flex; flex-direction: column; gap: 12px; }
    .exp-card { background: #161b22; border: 1px solid #21262d; border-left: 3px solid #27c93f; border-radius: 0 8px 8px 0; padding: 12px 16px; }
    .exp-company { font-size: 14px; color: #3fb950; font-weight: 600; }
    .exp-role { font-size: 12px; color: #58a6ff; }
    .exp-year { font-size: 11px; color: #6e7681; margin-top: 3px; }
    .exp-desc { font-size: 12px; color: #8b949e; margin-top: 8px; line-height: 1.6; }

    .links-row { display: flex; flex-wrap: wrap; gap: 10px; }
    .link-btn {
      display: flex; align-items: center; gap: 8px; padding: 9px 16px;
      background: #161b22; border: 1px solid #21262d; border-radius: 6px;
      text-decoration: none; color: #e6edf3; font-family: 'Fira Code', monospace; font-size: 13px;
      transition: border-color 0.2s, background 0.2s, color 0.2s;
    }
    .link-btn:hover { border-color: #58a6ff; background: #0d2137; color: #79c0ff; }

    .footer { text-align: center; margin-top: 2.5rem; padding-top: 1.5rem; border-top: 1px solid #21262d; }
    .footer p { font-size: 12px; color: #6e7681; }
    .footer span { color: #27c93f; }
  </style>
</head>
<body>
  <div class="container">

    <div class="terminal-bar">
      <div class="dot dot-red"></div>
      <div class="dot dot-yellow"></div>
      <div class="dot dot-green"></div>
      <span class="terminal-title">~/tharaka-prasad — bash</span>
    </div>

    <!-- Hero -->
    <div class="hero">
      <div class="prompt-line">
        <span class="prompt-symbol">$</span>
        <span>whoami</span>
      </div>
      <div class="hero-name">Tharaka Prasad<span class="blink">_</span></div>
      <div class="hero-role">Full-Stack Developer &nbsp;·&nbsp; <span>BIT (Hons) Networking &amp; Mobile Computing</span></div>
      <div class="hero-location" style="margin-top:8px;">📍 <span>Bandarawela, Sri Lanka</span> &nbsp;·&nbsp; Open to opportunities</div>
    </div>

    <!-- Stats -->
    <div class="stats-row">
      <div class="stat-card">
        <div class="stat-number" style="color:#3fb950;">4+</div>
        <div class="stat-label">Projects</div>
      </div>
      <div class="stat-card">
        <div class="stat-number" style="color:#f0883e;">2</div>
        <div class="stat-label">Companies</div>
      </div>
      <div class="stat-card">
        <div class="stat-number" style="color:#bc8cff;">3</div>
        <div class="stat-label">Cisco Certs</div>
      </div>
    </div>

    <!-- Tech Stack -->
    <div class="section">
      <div class="section-header">// tech stack</div>
      <div class="skills-grid">
        <span class="skill-tag tag-c">C</span>
        <span class="skill-tag tag-c">C++</span>
        <span class="skill-tag tag-py">Python</span>
        <span class="skill-tag tag-java">Java</span>
        <span class="skill-tag tag-php">PHP</span>
        <span class="skill-tag tag-php">Laravel</span>
        <span class="skill-tag tag-js">JavaScript</span>
        <span class="skill-tag tag-react">React</span>
        <span class="skill-tag tag-react">HTML</span>
        <span class="skill-tag tag-react">CSS</span>
        <span class="skill-tag tag-db">MySQL</span>
        <span class="skill-tag tag-tool">Packet Tracer</span>
        <span class="skill-tag tag-tool">ESP32</span>
        <span class="skill-tag tag-py">ML / Scikit-learn</span>
      </div>
    </div>

    <!-- Projects -->
    <div class="section">
      <div class="section-header">// projects</div>
      <div class="projects-grid">
        <div class="project-card">
          <div class="project-name">Student Registration System</div>
          <div class="project-desc">Full-stack student management with CRUD operations and reporting.</div>
          <div class="project-tags"><span class="project-lang">Laravel</span><span class="project-lang">MySQL</span></div>
        </div>
        <div class="project-card">
          <div class="project-name">CCNA Packet Tracer Labs</div>
          <div class="project-desc">VLAN configs, Telnet setups, and advanced routing simulations.</div>
          <div class="project-tags"><span class="project-lang">Cisco</span><span class="project-lang">Networking</span></div>
        </div>
        <div class="project-card">
          <div class="project-name">Sustainability App</div>
          <div class="project-desc">Back-end API for sustainability reporting with Laravel &amp; reporting tools.</div>
          <div class="project-tags"><span class="project-lang">Laravel</span><span class="project-lang">API</span></div>
        </div>
        <div class="project-card">
          <div class="project-name">IoT Rose Tunnel Monitor</div>
          <div class="project-desc">Real-time sensor monitoring for rose cultivation environments.</div>
          <div class="project-tags"><span class="project-lang">ESP32</span><span class="project-lang">Laravel</span><span class="project-lang">MySQL</span></div>
        </div>
      </div>
    </div>

    <!-- Research & Certs -->
    <div class="section">
      <div class="section-header">// research &amp; certifications</div>
      <div class="cert-list">
        <div class="cert-item">
          <div class="cert-icon" style="color:#bc8cff;">★</div>
          <div>
            <div class="cert-name">Dengue Fever Prediction using Machine Learning</div>
            <div class="cert-sub">Research · Horizon Campus Symposium, 2024</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-icon" style="color:#f0883e;">◈</div>
          <div>
            <div class="cert-name">Introduction to IoT</div>
            <div class="cert-sub">Cisco Certification</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-icon" style="color:#f0883e;">◈</div>
          <div>
            <div class="cert-name">Switching, Routing &amp; Wireless Essentials</div>
            <div class="cert-sub">Cisco Certification</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-icon" style="color:#f0883e;">◈</div>
          <div>
            <div class="cert-name">Enterprise Networking, Security &amp; Automation</div>
            <div class="cert-sub">Cisco Certification</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Experience -->
    <div class="section">
      <div class="section-header">// experience</div>
      <div class="exp-list">
        <div class="exp-card">
          <div class="exp-company">Axcertro Pvt Ltd</div>
          <div class="exp-role">Intern Developer</div>
          <div class="exp-year">2024</div>
          <div class="exp-desc">Developed and maintained Laravel applications, collaborated with design teams, and optimized system performance.</div>
        </div>
        <div class="exp-card" style="border-left-color:#58a6ff;">
          <div class="exp-company" style="color:#58a6ff;">Sky Smart Technology</div>
          <div class="exp-role">Associate Developer</div>
          <div class="exp-year">2025</div>
          <div class="exp-desc">Built REST APIs, tracked data pipelines, and maintained system performance across live environments.</div>
        </div>
      </div>
    </div>

    <!-- Connect -->
    <div class="section">
      <div class="section-header">// connect</div>
      <div class="links-row">
        <a href="https://github.com/tharaka-prasad" class="link-btn" target="_blank">⌥ GitHub</a>
        <a href="https://www.linkedin.com/in/tharaka-prasad-0408bb241/" class="link-btn" target="_blank">⌘ LinkedIn</a>
        <a href="mailto:tharakaprasad04@gmail.com" class="link-btn">@ Email</a>
      </div>
    </div>

    <!-- Footer -->
    <div class="footer">
      <p><span>$ echo</span> "Let's build something amazing together 🚀"</p>
      <p style="margin-top:6px; font-size:11px; color:#484f58;">tharaka-prasad · Bandarawela, Sri Lanka</p>
    </div>

  </div>
</body>
</html>
