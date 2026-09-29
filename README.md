# 🔎 Endex - Endpoint Reconnaissance Tool

<p align="center">
  <strong>Discover hidden endpoints, API routes and paths from JavaScript with a single click.</strong>
</p>

<p align="center">
  A lightweight browser bookmarklet for JavaScript endpoint discovery, web reconnaissance, bug bounty hunting and application security testing.
</p>

<p align="center">
  <a href="#-features">Features</a> •
  <a href="#-installation">Installation</a> •
  <a href="#-usage">Usage</a> •
  <a href="#-how-it-works">How It Works</a> •
  <a href="#-limitations">Limitations</a> •
  <a href="#-contributing">Contributing</a>
</p>

---

## 📌 What is Endex?

**Endex** is a browser-based **JavaScript endpoint reconnaissance and discovery tool** designed for bug hunters, penetration testers, application security engineers, developers and security researchers.

Endex works as a **JavaScript bookmarklet**. Once installed, you can run it directly on a webpage to extract endpoint-like paths referenced by the page source and JavaScript files.

It helps security researchers quickly identify interesting routes such as:

```text
/api/users
/api/login
/api/v1/auth
/api/graphql
/admin
/upload
/search?q=
/api/internal
```

Instead of manually opening and searching through multiple JavaScript files, Endex provides the discovered paths inside a clean interactive interface.

---

## ✨ Features

- 🔎 JavaScript endpoint discovery
- 🌐 Extract paths from the current webpage
- 📜 Scan external JavaScript files
- 🧹 Automatic duplicate removal
- 🔍 Live endpoint search and filtering
- 📋 Copy individual endpoints
- 📑 Copy all filtered endpoints
- ↗️ Open endpoints directly from the interface
- 📊 Endpoint count
- 🖥️ Clean dark cybersecurity-focused UI
- ⚡ Lightweight browser bookmarklet
- 🔐 No external server required
- 🧩 Works directly inside the browser
- 🎯 Useful for bug bounty and web application reconnaissance

---

## 🛠️ Use Cases

Endex can be useful during:

- Bug bounty reconnaissance
- Web application penetration testing
- API reconnaissance
- JavaScript analysis
- Application Security testing
- Security research
- Endpoint discovery
- Attack surface mapping
- Manual web reconnaissance
- JavaScript-based asset discovery

### Example

A JavaScript file might contain:

```javascript
fetch("/api/v1/users");
fetch("/api/v1/profile");
fetch("/api/admin/settings");
```

Endex can help surface paths such as:

```text
/api/v1/users
/api/v1/profile
/api/admin/settings
```

You can then manually investigate the discovered endpoints within the scope and authorization of your security testing.

---

# 🚀 Installation

Endex is a **bookmarklet**, so there is no package installation, Python environment or Node.js setup required.

## Method 1 — Create a Bookmark Manually

### Chrome / Chromium / Edge / Brave

1. Copy the Endex bookmarklet code.
2. Open your browser's bookmark manager.
3. Create a new bookmark.
4. Set the name to:

```text
Endex
```

5. Paste the JavaScript bookmarklet into the **URL** field.
6. Save the bookmark.

Your bookmark should look similar to:

```text
Name:
Endex

URL:
javascript:(function(){...})();
```

> ⚠️ Make sure the `javascript:` prefix is present.
>
> Some browsers remove the `javascript:` prefix when pasting into bookmark fields. If this happens, manually add it back.

---

# 📦 Bookmarklet

Copy the latest bookmarklet from the project source:

```javascript
javascript:(function(){var re=/(?<=("|'|`))\/[a-zA-Z0-9_?&=\/\-\x23\.]*(?=("|'|`))/g,res=new Set,ss=document.getElementsByTagName("script"),i,m;for(i=0;i<ss.length;i++){if(ss[i].src){fetch(ss[i].src).then(function(r){return r.text()}).then(function(t){for(var x of t.matchAll(re))res.add(x[0])}).catch(function(e){console.log("An error occurred:",e)})}}for(m of document.documentElement.outerHTML.matchAll(re))res.add(m[0]);function E(t,c,x){var e=document.createElement(t);e.style.cssText=c;if(x)e.textContent=x;return e}setTimeout(function(){var o=document.getElementById("endpoints-overlay");if(o)o.remove();var all=Array.from(res).sort(),cur=all,ov=E("div","position:fixed;inset:0;width:100vw;height:100vh;background:rgba(5,10,18,.78);backdrop-filter:blur(3px);z-index:2147483647;display:flex;align-items:center;justify-content:center;font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif"),pn=E("div","background:#0d1117;border:1px%20solid%20#263244;border-radius:14px;width:min(760px,92vw);height:min(760px,84vh);display:flex;flex-direction:column;overflow:hidden;box-shadow:0%2020px%2060px%20rgba(0,0,0,.55)%22),hd=E(%22div%22,%22display:flex;align-items:center;padding:15px%2018px;border-bottom:1px%20solid%20#202938;background:#111722%22),tt=E(%22div%22,%22display:flex;align-items:center;gap:11px;min-width:0%22),tc=E(%22div%22,%22display:flex;flex-direction:column;gap:2px;min-width:0%22),title=E(%22span%22,%22color:#e6edf3;font-weight:650;font-size:15px;line-height:18px%22,%22Endex%20-%20Endpoint%20Reconnaissance%20Tool%22),by=E(%22a%22,%22color:#66758a;font-size:10px;text-decoration:none;line-height:12px;cursor:pointer%22,%22by%20Shoaib%20Shaikh%22),cl=E(%22button%22,%22margin-left:auto;background:transparent;border:0;color:#718096;font-size:19px;cursor:pointer;padding:3px%205px;line-height:1;border-radius:6px%22,%22\u2715%22),sb=E(%22div%22,%22padding:12px%2018px;border-bottom:1px%20solid%20#202938;background:#0f141d%22),inp=E(%22input%22,%22width:100%;box-sizing:border-box;background:#090d13;color:#dce6f1;border:1px%20solid%20#263244;border-radius:8px;padding:9px%2011px;font-size:12px;outline:none%22),bd=E(%22div%22,%22overflow-y:auto;padding:10px%2014px;flex:1;background:#0b1017;scrollbar-width:thin;scrollbar-color:#344154%20#0b1017%22),ft=E(%22div%22,%22padding:10px%2016px;border-top:1px%20solid%20#202938;background:#111722;display:flex;align-items:center;justify-content:space-between%22),cnt=E(%22span%22,%22color:#7d8da3;font-size:11px;font-family:monospace%22),ca=E(%22button%22,%22background:#2563eb;color:#fff;border:1px%20solid%20#3b82f6;padding:6px%2013px;border-radius:7px;font-size:11px;font-weight:600;cursor:pointer%22,%22Copy%20all%22);function%20close(){ov.remove()}function%20render(){var%20q=inp.value.toLowerCase();cur=all.filter(function(p){return%20p.toLowerCase().indexOf(q)%3E-1});cnt.textContent=%22%F0%9F%8C%90%20%22+location.origin+%22%20%20%E2%80%A2%20%20%22+cur.length+%22%20/%20%22+all.length+%22%20endpoints%22;bd.textContent=%22%22;if(!cur.length){bd.appendChild(E(%22p%22,%22color:#64748b;font-size:13px;text-align:center;padding:40px%200%22,all.length?%22No%20matching%20endpoints.%22:%22No%20endpoints%20found.%22));return}cur.forEach(function(p){var%20r=E(%22div%22,%22display:flex;align-items:center;gap:7px;padding:5px%207px;margin:2px%200;border:1px%20solid%20transparent;border-radius:7px;transition:background%20.12s,border%20.12s%22),ps=E(%22span%22,%22flex:1;font-family:ui-monospace,SFMono-Regular,Menlo,monospace;font-size:12px;color:#c9d5e3;word-break:break-all;line-height:18px%22,p),cp=E(%22button%22,%22background:#151d29;color:#8fa4bc;border:1px%20solid%20#29374a;padding:4px%2010px;border-radius:5px;font-size:10px;cursor:pointer;flex-shrink:0%22,%22Copy%22),op=E(%22button%22,%22background:#1d4ed8;color:#fff;border:1px%20solid%20#2563eb;padding:4px%2010px;border-radius:5px;font-size:10px;font-weight:600;cursor:pointer;flex-shrink:0%22,%22Open%22);r.onmouseover=function(){r.style.background=%22#121b28%22;r.style.borderColor=%22#24354b%22};r.onmouseout=function(){r.style.background=%22transparent%22;r.style.borderColor=%22transparent%22};cp.onclick=function(e){e.stopPropagation();navigator.clipboard&&navigator.clipboard.writeText(p).then(function(){cp.textContent=%22Copied%22;cp.style.color=%22#4ade80%22;setTimeout(function(){cp.textContent=%22Copy%22;cp.style.color=%22#8fa4bc%22},1000)})};op.onclick=function(e){e.stopPropagation();window.open(location.origin+p,%22_blank%22,%22noopener%22)};r.append(cp,op,ps);bd.appendChild(r)})}by.href=%22https://github.com/shoaibls%22;by.target=%22_blank%22;by.rel=%22noopener%20noreferrer%22;tc.append(title,by);tt.append(E(%22span%22,%22width:9px;height:9px;border-radius:50%;background:#3b82f6;box-shadow:0%200%208px%20rgba(59,130,246,.65);display:inline-block;flex-shrink:0%22),tc);hd.append(tt,cl);cl.onclick=close;inp.type=%22text%22;inp.placeholder=%22Search%20endpoints...%22;inp.oninput=render;inp.onfocus=function(){inp.style.borderColor=%22#3b82f6%22;inp.style.boxShadow=%220%200%200%202px%20rgba(59,130,246,.12)%22};inp.onblur=function(){inp.style.borderColor=%22#263244%22;inp.style.boxShadow=%22none%22};inp.onkeydown=function(e){e.stopPropagation();if(e.key===%22Escape%22)close()};sb.appendChild(inp);ca.onclick=function(){navigator.clipboard&&navigator.clipboard.writeText(cur.join(%22\n%22));ca.textContent=%22Copied%22;setTimeout(function(){ca.textContent=%22Copy%20all%22},1000)};ft.append(cnt,ca);pn.append(hd,sb,bd,ft);ov.appendChild(pn);ov.onclick=function(e){if(e.target===ov)close()};document.body.appendChild(ov);render();inp.focus()},3000)})();
```

> The recommended approach is to keep the bookmarklet source in the repository and update it whenever a new Endex version is released.

---

# 🎯 Usage

Once Endex has been installed:

### 1. Open a target webpage

Navigate to the web application you are authorized to test.

### 2. Click the Endex bookmark

Click:

```text
Endex
```

from your browser bookmarks.

### 3. Wait for JavaScript analysis

Endex scans the current page and referenced JavaScript resources.

### 4. Review discovered endpoints

The interface displays discovered paths:

```text
/api/users
/api/auth/login
/api/graphql
/admin/dashboard
/upload
```

### 5. Search

Use the search box to quickly filter results:

```text
admin
api
graphql
upload
auth
user
```

### 6. Copy

Use **Copy** to copy an individual endpoint.

Use **Copy all** to copy the currently filtered results.

### 7. Open

Use **Open** to open an endpoint on the current host.

---

# 🔬 How It Works

Endex performs client-side analysis using JavaScript.

At a high level:

```text
                 ┌───────────────────┐
                 │    Target Page    │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │ Find JS Resources │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │ Fetch JS Content  │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │ Endpoint Matching │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │ Deduplicate Paths │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │ Search / Filter   │
                 └─────────┬─────────┘
                           │
                           ▼
                 ┌───────────────────┐
                 │ Copy / Open       │
                 └───────────────────┘
```

The scanner uses pattern matching to identify path-like strings from page content and JavaScript resources.

---

# 🧪 Example Workflow for Bug Hunters

A typical workflow could look like:

```text
Target
  ↓
Open web application
  ↓
Run Endex
  ↓
Discover JavaScript endpoints
  ↓
Search interesting keywords
  ↓
Copy endpoints
  ↓
Manually validate authorized targets
  ↓
Continue testing with your preferred security tools
```

Useful search terms include:

```text
api
admin
auth
login
user
account
internal
debug
upload
download
graphql
swagger
config
token
reset
password
```

> Endex is an endpoint discovery and reconnaissance tool. Discovery of an endpoint does not mean that the endpoint is vulnerable.

---

# 🔐 Responsible Use

Endex is intended for:

- Authorized penetration testing
- Bug bounty programs where testing is permitted
- Your own applications
- Security research with appropriate authorization
- Educational security testing environments

Only use Endex against systems you are authorized to test.

The author is not responsible for misuse of this tool.

---

# ⚠️ Limitations

Endex relies on browser-side access to JavaScript resources and pattern matching.

Some endpoints may not be discovered because:

- JavaScript is dynamically generated.
- Endpoint strings are constructed at runtime.
- JavaScript resources cannot be fetched because of browser security restrictions.
- Endpoints are generated from API responses.
- Strings are encoded or obfuscated.
- Endpoints are stored outside JavaScript.
- Authentication or application state is required.
- The endpoint is not represented as a recognizable path.

Therefore:

> **No endpoint discovery tool can guarantee complete endpoint coverage.**

Endex should be considered a reconnaissance aid rather than a complete application crawler.

---

# 🆚 Endex vs Traditional Endpoint Discovery

Endex focuses on a fast **browser-based JavaScript reconnaissance workflow**.

| Feature | Endex |
|---|---|
| Installation | Bookmarklet |
| Browser-based | ✅ |
| JavaScript endpoint discovery | ✅ |
| Live search | ✅ |
| Duplicate removal | ✅ |
| Copy endpoint | ✅ |
| Open endpoint | ✅ |
| No backend required | ✅ |
| Lightweight | ✅ |
| Bug bounty workflow | ✅ |

---

# 🧑‍💻 Development

Clone the repository:

```bash
git clone <YOUR_REPOSITORY_URL>
cd <YOUR_REPOSITORY_NAME>
```

The main project is a browser bookmarklet, so there is no mandatory dependency installation.

For development:

1. Modify the bookmarklet source.
2. Test it against authorized applications.
3. Verify browser compatibility.
4. Minify/update the bookmarklet.
5. Test the UI and endpoint extraction.
6. Commit your changes.

---

# 🤝 Contributing

Contributions are welcome!

If you have an idea for improving Endex:

1. Fork the repository.
2. Create a feature branch.

```bash
git checkout -b feature/improved-endpoint-detection
```

3. Make your changes.
4. Test the bookmarklet.
5. Commit your changes.

```bash
git commit -m "Improve endpoint detection"
```

6. Push the branch.

```bash
git push origin feature/improved-endpoint-detection
```

7. Open a Pull Request.

---

# 🌟 Why Endex?

Modern web applications frequently rely heavily on JavaScript and client-side APIs.

During reconnaissance, JavaScript files can reveal useful information about:

- API routes
- Authentication endpoints
- User-related endpoints
- Administrative routes
- Internal application paths
- GraphQL endpoints
- Upload/download functionality
- Application features

Endex provides a quick way to inspect these references directly from the browser without manually downloading and searching every JavaScript file.

---

# 📄 License

This project is licensed under the MIT License.

See the `LICENSE` file for details.

---

# 👨‍💻 Author

**Shoaib Shaikh**

Security Researcher • Application Security • Web Security

Built for security researchers, bug hunters and developers who want a lightweight way to discover JavaScript endpoints during reconnaissance.

---

## ⭐ Support the Project

If Endex is useful to you:

- ⭐ Star the repository
- 🐛 Report bugs
- 💡 Suggest features
- 🔧 Submit pull requests
- 📢 Share it with other security researchers

Every contribution helps improve the project.

---

<p align="center">
  <strong>Endex — Discover. Recon. Investigate.</strong>
</p>
