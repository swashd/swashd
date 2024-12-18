<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, sans-serif;
      line-height: 1.6;
      max-width: 800px;
      margin: 0 auto;
      padding: 20px;
      background: #0d1117;
      color: #c9d1d9;
    }

    h1, h2, h3 {
      border-bottom: 1px solid #30363d;
      padding-bottom: 0.3em;
      color: #58a6ff;
    }

    dl {
      background: #161b22;
      padding: 20px;
      border-radius: 6px;
      border: 1px solid #30363d;
      margin: 20px 0;
      animation: fadeIn 0.5s ease-out;
    }

    dt {
      font-weight: bold;
      color: #58a6ff;
      margin-top: 10px;
    }

    dd {
      margin-left: 20px;
      color: #8b949e;
    }

    code {
      background: #1f2428;
      padding: 2px 5px;
      border-radius: 3px;
      font-family: 'SFMono-Regular', Consolas, 'Liberation Mono', Menlo, monospace;
      font-size: 85%;
    }

    .tag {
      display: inline-block;
      background: #1f6feb33;
      color: #58a6ff;
      padding: 2px 8px;
      border-radius: 15px;
      font-size: 85%;
      margin: 2px;
    }

    em {
      color: #58a6ff;
      font-style: normal;
      padding: 0 2px;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    #loading {
      text-align: center;
      padding: 20px;
      color: #8b949e;
    }
  </style>
</head>
<body>
  <div id="content"></div>
  <div id="loading">Loading more content...</div>

  <script>
    const definitions = [
      {
        term: "Microsoft Azure Expert",
        desc: "Specialized in cloud infrastructure and deployment with *5+ years* experience in Azure services."
      },
      {
        term: "PowerShell Automation",
        desc: "Created **200+** automation scripts for enterprise system management and deployment."
      },
      {
        term: "Security Implementation",
        desc: "Implemented <em>robust security protocols</em> across multiple enterprise environments."
      },
      {
        term: "Infrastructure Management",
        desc: "Managed hybrid cloud infrastructure for `500+` enterprise users."
      },
      {
        term: "Active Directory",
        desc: "Expert in AD management, GPO deployment, and user administration."
      },
      {
        term: "System Center Configuration",
        desc: "Deployed and managed SCCM for large-scale system administration."
      },
      {
        term: "Cloud Migration",
        desc: "Successfully migrated *50+* on-premise solutions to cloud infrastructure."
      },
      {
        term: "Certification Achievement",
        desc: "Obtained **4** Microsoft certifications in cloud and system administration."
      }
    ];

    const tags = [
      "Azure", "PowerShell", "Windows Server", "Active Directory", 
      "Cloud Computing", "Security", "Automation", "Microsoft 365",
      "System Center", "VMware", "Docker", "Kubernetes",
      "Exchange", "SharePoint", "Teams", "Intune"
    ];

    function createDefinitionList() {
      const dl = document.createElement('dl');
      
      // Get 3 random definitions
      const shuffled = [...definitions].sort(() => 0.5 - Math.random());
      const selected = shuffled.slice(0, 3);
      
      selected.forEach(def => {
        const dt = document.createElement('dt');
        dt.textContent = def.term;
        dl.appendChild(dt);

        const dd = document.createElement('dd');
        dd.innerHTML = def.desc
          .replace(/\*([^*]+)\*/g, '<em>$1</em>')
          .replace(/\*\*([^*]+)\*\*/g, '<strong>$1</strong>')
          .replace(/`([^`]+)`/g, '<code>$1</code>');
        
        // Add random tags
        const randomTags = tags
          .sort(() => 0.5 - Math.random())
          .slice(0, 3)
          .map(tag => `<span class="tag">${tag}</span>`)
          .join(' ');
        
        dd.innerHTML += '<br>' + randomTags;
        dl.appendChild(dd);
      });

      return dl;
    }

    function addContent() {
      const content = document.getElementById('content');
      content.appendChild(createDefinitionList());
    }

    // Initial load
    for (let i = 0; i < 5; i++) {
      addContent();
    }

    // Infinite scroll
    window.addEventListener('scroll', () => {
      if ((window.innerHeight + window.scrollY) >= document.body.offsetHeight - 500) {
        addContent();
      }
    });
  </script>
</body>
</html>
