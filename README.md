# MetaPWN |    Adversary Emulation & Metadata Intelligence Platform

<p align="center">
  <img src="https://img.shields.io/badge/version-1.0.0-ff2d55?style=flat-square&labelColor=0a0a0a" alt="version">
  <img src="https://img.shields.io/badge/modules-600+-ff2d55?style=flat-square&labelColor=0a0a0a" alt="modules">
  <img src="https://img.shields.io/badge/pillars-46-ff2d55?style=flat-square&labelColor=0a0a0a" alt="pillars">
  <img src="https://img.shields.io/badge/python-3.9+-ff2d55?style=flat-square&labelColor=0a0a0a" alt="python">
  <img src="https://img.shields.io/badge/platform-linux%20%7C%20macos%20%7C%20windows-ff2d55?style=flat-square&labelColor=0a0a0a" alt="platform">
  <img src="https://img.shields.io/badge/license-authorized%20use%20only-critical?style=flat-square&labelColor=0a0a0a" alt="license">
</p>

<p align="center">
  <b>AUTHOR</b>&nbsp;&nbsp;SYLHETYHACKVENGER&nbsp;&nbsp;·&nbsp;&nbsp;<b>HANDLE</b>&nbsp;&nbsp;<a href="https://github.com/THE-ERROR808">THE-ERROR808</a>
</p>

---

MetaPWN is a unified, single-file offensive security and metadata intelligence platform written in pure Python. It consolidates universal metadata extraction, web and protocol reconnaissance, credential attacks, exploitation primitives, post-exploitation, cloud and container abuse, digital forensics, OSINT, and image and media analysis into a single interactive operator console.

Every capability is exposed as a module grouped under one of 46 pillars (A → AT). Modules auto-register on import, dispatch by target type, and persist artifacts into structured per-pillar input/ and output/ trees. Reports are emitted in JSON, CSV, XML, STIX 2.1, and MISP formats.

⚠️ Authorized use only. MetaPWN is designed exclusively for authorized red-team engagements, penetration tests, forensic investigations, and OSINT research conducted with explicit written permission. Unauthorized use is illegal.

<p align="center">
  <img src="https://quickchart.io/chart?c=%7B%22type%22%3A%22radar%22%2C%22data%22%3A%7B%22labels%22%3A%5B%22Recon%22%2C%22Weaponize%22%2C%22Delivery%22%2C%22Exploit%22%2C%22Install%22%2C%22C2%22%2C%22Actions%22%2C%22Exfil%22%2C%22Forensics%22%2C%22OSINT%22%5D%2C%22datasets%22%3A%5B%7B%22label%22%3A%22MetaPWN%22%2C%22data%22%3A%5B98%2C92%2C80%2C88%2C85%2C82%2C90%2C88%2C96%2C95%5D%2C%22backgroundColor%22%3A%22rgba%28255%2C45%2C85%2C0.25%29%22%2C%22borderColor%22%3A%22%23ff2d55%22%2C%22borderWidth%22%3A3%2C%22pointBackgroundColor%22%3A%22%23ff2d55%22%2C%22pointBorderColor%22%3A%22%23fff%22%2C%22pointRadius%22%3A5%7D%2C%7B%22label%22%3A%22Industry%20Avg%22%2C%22data%22%3A%5B70%2C55%2C60%2C65%2C50%2C55%2C60%2C55%2C40%2C60%5D%2C%22backgroundColor%22%3A%22rgba%280%2C200%2C255%2C0.15%29%22%2C%22borderColor%22%3A%22%2300c8ff%22%2C%22borderWidth%22%3A2%2C%22pointBackgroundColor%22%3A%22%2300c8ff%22%2C%22pointBorderColor%22%3A%22%23fff%22%2C%22pointRadius%22%3A4%7D%5D%7D%2C%22options%22%3A%7B%22plugins%22%3A%7B%22title%22%3A%7B%22display%22%3Atrue%2C%22text%22%3A%22MetaPWN%20%E2%80%94%20Kill%20Chain%20Coverage%20vs%20Industry%20Average%22%2C%22color%22%3A%22%23ff2d55%22%2C%22font%22%3A%7B%22size%22%3A16%7D%7D%2C%22legend%22%3A%7B%22labels%22%3A%7B%22color%22%3A%22%23eee%22%2C%22font%22%3A%7B%22size%22%3A12%7D%7D%7D%7D%2C%22scales%22%3A%7B%22r%22%3A%7B%22angleLines%22%3A%7B%22color%22%3A%22%23555%22%7D%2C%22grid%22%3A%7B%22color%22%3A%22%23555%22%7D%2C%22pointLabels%22%3A%7B%22color%22%3A%22%23eee%22%2C%22font%22%3A%7B%22size%22%3A13%2C%22weight%22%3A%22bold%22%7D%7D%2C%22ticks%22%3A%7B%22color%22%3A%22%23888%22%2C%22backdropColor%22%3A%22transparent%22%2C%22stepSize%22%3A20%7D%2C%22min%22%3A0%2C%22max%22%3A100%7D%7D%7D%7D&w=900&h=700&bkg=%230d0d0d&f=png" alt="MetaPWN Kill Chain Coverage Radar Chart">
</p>

Table of Contents

· Highlights
· Architecture
· Pillar Reference
· Installation
· Quick Start
· Command Reference
· Reports & Artifacts
· Data Layout
· Extending MetaPWN
· Optional Dependencies
· Safety Features
· Legal Notice

---

Highlights

Category Capability
Formats 150+ file formats across documents, media, images, archives, mobile, binaries, and forensic images
Pillars 46 pillars, 600+ modules, single-file deployment
Targets URL, domain, IP, port, file path, hash, token, JWT, GPS coordinates
Dispatch Auto-classification and auto-routing to relevant pillars
Reports JSON, CSV, XML, STIX 2.1, MISP, partial-on-interrupt
Runtime Rate limiting, HTTP cache, cookie jar, checkpointing, graceful shutdown
Extensibility Drop-in Python plugins, JSON rule engine, scope file, kill switch
Dependencies Pure Python core, optional libs degrade gracefully

---

Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                          MetaPWN  REPL                              │
│                    (Interactive Operator Console)                   │
└────────────────────────────────┬────────────────────────────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │   Target Classifier     │
                    │   Auto-Dispatch Router  │
                    └────────────┬────────────┘
                                 │
        ┌────────────────────────┼────────────────────────┐
        │                        │                        │
   ┌────▼────┐              ┌────▼────┐              ┌────▼────┐
   │  Web    │              │  File   │              │  Host   │
   │ Targets │              │ Targets │              │ Targets │
   └────┬────┘              └────┬────┘              └────┬────┘
        │                        │                        │
        └────────────────────────┼────────────────────────┘
                                 │
                    ┌────────────▼────────────┐
                    │   Module  Registry      │
                    │   (46 Pillars A → AT)   │
                    └────────────┬────────────┘
                                 │
        ┌────────────────────────┼────────────────────────┐
        │                        │                        │
   ┌────▼────┐              ┌────▼────┐              ┌────▼────┐
   │ Engine  │              │ Findngs │              │ Report  │
   │  Core   │─────────────▶│  Store  │─────────────▶│ Adapter │
   └─────────┘              └─────────┘              └─────────┘
                                                          │
                                              ┌───────────┼───────────┐
                                              │           │           │
                                           JSON        STIX        MISP
                                           CSV         XML         Partial
```

Runtime pipeline

```
Input → Classify → Route → Execute → Collect → Aggregate → Export
```

---

Pillar Reference

MetaPWN organizes its capabilities into 46 pillars, each handling a distinct domain of the offensive security and forensic lifecycle.

Pillar Name Domain Modules
A EXTRACTOR Universal metadata from structured formats 45
B WEB/PROTO Web and protocol metadata 19
C SNATCHER Active retrieval 33
D CRACKER Hash, archive, and password recovery 27
E INTEL Cross-cutting intelligence 10
F ENGINE Plugins, rules, and output adapters 14
G CREDS Credential attacks 14
H EXPLOIT Exploitation primitives 18
I PRIVESC Privilege escalation 12
J PERSIST Persistence mechanisms 13
K LATERAL Lateral movement 13
L EXFIL Exfiltration channels 15
M PAYLOADS Payload generation 15
N C2 Command and control 12
O ANTI-FOR Anti-forensics 7
P CLOUD/CTR Cloud and container abuse 8
Q DOWNLOAD Universal retrieval 38
R RECOVERY Deleted-file and disk recovery 15
S CARVE Stream carving 13
T MEDIA-META Video and audio container extraction 22
U SOCIAL Social media metadata 16
V REMAINDER Remaining platforms and formats 20
W ARCHIVE Web archives and crawl indexes 16
X PEOPLE/PAY People intelligence and payment fingerprinting 17
Y GEO/CRED Geolocation and web credential extraction 19
Z OFFICE-DEEP Office and PDF deep analysis 20
AA MEDIA-DEEP Media container deep analysis 20
AB MOBILE Mobile app analysis 19
AC CONTAINERS Containers and Kubernetes 20
AD AD/KERB Kerberos, NTLM, and Active Directory 19
AE CLOUD-DEEP Deep cloud provider enumeration 25
AF CI/CD CI/CD pipeline metadata 25
AG DATABASES Database configuration and metadata 25
AH MSG-QUEUES Message queues and brokers 20
AI SECRETS Secret and token validation 20
AJ SYSTEMD systemd and journald forensics 15
AK BROWSER-ART Browser artifacts deep 20
AL FORENSICS Windows, macOS, and Linux forensics 30
AM ICS/VOIP ICS, telecom, and VoIP 20
AN HARDWARE Printers and hardware inventory 25
AO WIRELESS Bluetooth and nearby radio 15
AP OS-LINUX Linux system enumeration 20
AQ WEB-DEEP Web application deep analysis 20
AR WEB-INTEL Web intelligence and scraping 25
AS INFRA Infrastructure service configs 25
AT PICTURE Image metadata and forensic analysis 96

Detailed Pillar Capabilities

<details>
<summary><b>A — EXTRACTOR</b> · Universal metadata from structured formats</summary>

· OpenDocument (odt/ods/odp) meta.xml
· RTF info group, EPUB OPF, MOBI/AZW3 Kindle blocks
· Apple iWork (Pages/Numbers/Keynote), OneNote .one
· Visio, MS Project .mpp, Publisher .pub, Access .mdb/.accdb
· AutoCAD .dwg/.dxf, Photoshop .psd, Illustrator .ai, InDesign .indd
· Sketch/Figma exports, Blender .blend, Unity .unity3d
· Subtitles .srt/.ass, iCalendar .ics, vCard .vcf, Torrent .torrent
· Apple plists, Windows .lnk, Prefetch, Registry hives, .evtx, .DS_Store
· SQLite schema + PII scan, MongoDB BSON, LDIF, .eml/.msg/.pst/.ost
· SBOM (SPDX / CycloneDX), JAR/APK/IPA/WAR manifests
· .NET assembly, Go/Rust/GCC build info, PE/ELF/Mach-O headers
· Firmware blobs, QR + barcode + OCR, PDF Info + XMP + JS
· DOCX/XLSX/PPTX docProps, ID3v2 frames, native XMP sidecars

</details>

<details>
<summary><b>B — WEB/PROTO</b> · Web and protocol metadata</summary>

· HTTP response header fingerprinting, meta-tag mining
· <link rel=author|me>, RSS/Atom, OpenGraph + Twitter Card
· JSON-LD structured data, GraphQL introspection
· Swagger / OpenAPI discovery, WSDL/SOAP, GraphQL SDL
· favicon mmh3 (Shodan), TLS certificate metadata (SANs, PEM save)
· DNS records (A/AAAA/MX/NS/TXT/CNAME/SOA/CAA/SRV/DMARC)
· WHOIS / RDAP registrant, HTTP/2 + HTTP/3 push headers
· Cookie metadata, CORS misconfig, JWT payload decode, secret regex sweep

</details>

<details>
<summary><b>C — SNATCHER</b> · Active retrieval</summary>

· Browser cache/history/cookie DB discovery, session token snatch
· OS credential manager enumeration, SSH key metadata
· Git repo scraping (.git/.svn/.hg), .env recursive parse
· Docker registry metadata, Kubernetes manifest leaks
· Cloud IMDS (AWS/GCP/Azure/DO/Alibaba/Oracle), SSRF → IMDS
· Cloud storage enumeration (S3/GCS/Azure), open bucket discovery
· Slack/Discord/Teams webhooks, Postman/Insomnia, Jupyter notebooks
· Elasticsearch/Kibana, MongoDB/Redis/Memcached/CouchDB
· RabbitMQ/Kafka/MQTT, Jenkins/GitLab/Gitea
· SonarQube/Nexus/Artifactory, WordPress/Drupal/Joomla
· Paste site monitor, Wayback diffing, AXFR, NSEC walking
· Reverse IP pivot, ASN enum, subdomain brute force

</details>

<details>
<summary><b>D — CRACKER</b> · Hash, archive, and password recovery</summary>

· Hash identification (MD5/SHA/NTLM/bcrypt/argon2/yescrypt/SSHA)
· Dictionary attacks with hashcat fallback hints
· ZIP/RAR/7z/PDF/Office password recovery
· JWT secret brute force, Basic-auth, form-login brute force
· Steganography detection + recovery (steghide)
· EXIF hidden-data carve, polyglot detection, embedded file carving
· Base64/hex/URL/ROT13 auto-decode, multi-layer recursive decode
· XOR single-byte brute, Vigenère auto-crack, Caesar, rail fence
· QR/barcode decode, OCR, wire fuzz, SSRF, XXE, path traversal

</details>

<details>
<summary><b>E — INTEL</b> · Cross-cutting intelligence</summary>

· Unified timeline (HTTP + filesystem + findings)
· Entity graph (emails → domains → IPs → URLs)
· Dedup SHA256 + fuzzy hash (ssdeep, tlsh)
· Language detection, named entity recognition
· Secret scanning ruleset, PII detection
· YARA-style signature scan, IOC extraction, MITRE ATT&CK mapping

</details>

<details>
<summary><b>F — ENGINE</b> · Plugins, rules, and output adapters</summary>

· Plugin loader (data/plugins/*.py)
· Rule engine (data/rules.json)
· Output adapters (JSON / CSV / XML / STIX 2.1 / MISP)
· Resume/checkpoint, distributed mode (worker + coordinator)
· Docker image + compose generator, REST API mode
· TUI/Web UI helpers, live streaming output
· Phase skipping, scope file, kill switch, encrypted output vault

</details>

<details>
<summary><b>G — CREDS</b> · Credential attacks</summary>

· Password spraying, credential stuffing
· Username permutation engine, email → username mapping
· Default-credential testing, SSH key harvesting
· Kerberos username enum, AS-REP roast, Kerberoast
· NTLM relay prep, JWT forgery (alg:none + HS256 guesses)
· API key replay, OAuth token replay, session cookie hijack

</details>

<details>
<summary><b>H — EXPLOIT</b> · Exploitation primitives</summary>

· Version → CVE mapping, searchsploit lookup
· SSRF chains, XXE delivery, path traversal chains
· Log4Shell / Spring4Shell probes, deserialization gadget detection
· Web shell drop, SQLi autopwn, Cmdi autopwn, SSTI autopwn
· File upload bypass, GraphQL mutation abuse
· Mass assignment, prototype pollution, race-condition, subdomain takeover
· DNS rebinding, S3 bucket hijack

</details>

<details>
<summary><b>I — PRIVESC</b> · Privilege escalation</summary>

· Linux SUID/sudo/cron checks, Windows service checks
· Container escape (/.dockerenv, docker.sock, cgroups)
· Kubernetes privesc, cloud IAM privesc, IMDS privesc
· SSH agent forwarding abuse, Kerberos delegation abuse
· ADCS abuse, GPO abuse, Sudo CVE, Polkit PwnKit

</details>

<details>
<summary><b>J — PERSIST</b> · Persistence mechanisms</summary>

· authorized_keys injection, cron / systemd timers
· Windows scheduled task, registry Run key, WMI subscription
· Web shell persistence, reverse-shell beacon (bash + PS)
· Service install, cloud backdoor, container sidecar injection
· Backdoor in build pipeline, DNS-based persistence, LDAP persistence

</details>

<details>
<summary><b>K — LATERAL</b> · Lateral movement</summary>

· Pass-the-hash, pass-the-ticket, overpass-the-hash
· PSExec / SMBExec / WMIExec / ATExec / DCOMExec
· WinRM / RDP spray, SSH pivot, SOCKS proxy over host
· Cloud lateral, VPN lateral, Kubernetes lateral
· Internal DNS poisoning, network share enum, DB hop

</details>

<details>
<summary><b>L — EXFIL</b> · Exfiltration channels</summary>

· DNS tunneling, ICMP covert channel, HTTPS exfil
· Cloud storage exfil, paste site exfil, stego exfil
· Encrypted archive exfil, chunked exfil with timing jitter
· Exfil via chat webhooks, backup service, print jobs, email
· Exfil via GitHub, DNS zone, monitored-API blending

</details>

<details>
<summary><b>M — PAYLOADS</b> · Payload generation</summary>

· Reverse shell generator (bash/nc/python/perl/powershell/socat)
· Shellcode encoder (XOR + Base64)
· PE / ELF payload builder, cross-compile support
· Macro (VBA), LNK, HTA, JScript, VBScript generators
· One-liner obfuscator, PowerShell AMSI bypass
· AV evasion stub, signed binary proxy list
· DLL sideloading payload, container image backdoor
· K8s job template, CloudFormation / Terraform backdoor

</details>

<details>
<summary><b>N — C2</b> · Command and control</summary>

· Reverse shell listener, HTTP/HTTPS C2 server
· DNS C2, Slack/Discord/Telegram C2
· GitHub-based C2, dead-drop C2, session management
· Post-exploitation modules, screen/webcam capture
· Keylogger module, credential dumper, screenshot/clipboard

</details>

<details>
<summary><b>O — ANTI-FOR</b> · Anti-forensics</summary>

· Log wiping, timestamp manipulation, shell history clearing
· Process name masquerading, traffic shaping
· Certificate pinning bypass (Frida), AV/EDR evasion hints

</details>

<details>
<summary><b>P — CLOUD/CTR</b> · Cloud and container abuse</summary>

· AWS/Azure/GCP abuse scripts + live identity probes
· Kubernetes abuse, Docker abuse, CI/CD pipeline injection
· Serverless hijack, IaC state file leak

</details>

<details>
<summary><b>Q — DOWNLOAD</b> · Universal retrieval</summary>

· HTTP/HTTPS streaming, segmented multi-connection, resume
· Checksum verification, bandwidth throttling, size cap
· Cookie jar (Netscape), FTP/FTPS, SFTP, SCP, TFTP, WebDAV
· SMB / CIFS, NFS, S3, GCS, Azure Blob
· BitTorrent / magnet, HLS (m3u8), DASH (mpd)
· RTSP live capture, RTMP live capture, Git clone
· Recursive website crawler, sitemap-driven bulk download
· Link extractor, download queue with concurrency
· aria2c, wget, curl, yt-dlp, gallery-dl, rclone, lftp wrappers

</details>

<details>
<summary><b>R — RECOVERY</b> · Deleted-file and disk recovery</summary>

· NTFS deleted-file recovery (MFT), ext2/3/4 recovery, FAT/exFAT
· PhotoRec-style carving, SQLite WAL/journal recovery
· Windows $Recycle.Bin recovery, shellbag parsing, jump lists
· macOS quarantine events, Linux log recovery
· Memory dump (Volatility), registry hive recovery
· Volume shadow copy access, trash recovery
· Browser closed-session recovery

</details>

<details>
<summary><b>S — CARVE</b> · Stream carving</summary>

· Carve socket traffic, command output (pipe), PCAP streams
· Printable strings + UTF-16 strings
· DNS-tunneled exfil data, raw disk images
· HTTP responses from proxy logs, credentials from memory dumps
· Encryption keys, URLs and endpoints
· Base64 blobs (auto-decode to known magic)
· XOR-encoded payloads (256-key brute with magic match)

</details>

<details>
<summary><b>T — MEDIA-META</b> · Video and audio container extraction</summary>

· ExifTool universal extraction, ffprobe, MediaInfo, mkvinfo
· 7z + unrar listings
· Native MP4/MOV, MKV/WebM, AVI, WAV/BWF, MP3 ID3, FLAC, OGG/Opus, WebP
· Native HEIC/AVIF, SVG, XMP, NFO, GPX, KML, TIFF IFD
· Universal metadata auto-dispatch

</details>

<details>
<summary><b>U — SOCIAL</b> · Social media metadata</summary>

· oEmbed autodiscovery, YouTube, Vimeo, TikTok, Instagram, Twitter/X, Facebook
· Reddit, Schema.org VideoObject, OG video tags
· Plex/Jellyfin/Kodi NFO, HLS/DASH manifest metadata
· Streaming player metadata, embedded video extraction
· Media catalogue API (Plex/Jellyfin), download-and-inspect video

</details>

<details>
<summary><b>V — REMAINDER</b> · Remaining platforms and formats</summary>

· LinkedIn, Pinterest, Tumblr post metadata
· Mastodon status, Bluesky AT Protocol, Mastodon instance info
· ActivityPub actor lookup, RAW camera (CR2/NEF/ARW/DNG/ORF/RW2)
· CHM, DjVu, FB2, CBZ/CBR, mind maps (.mm/.xmind/.mindnode)
· Native RAR / 7z / TAR (PAX/GNU) header parsers
· ISO 9660 / UDF / El Torito, NTFS MFT, ext superblock, Shellbag

</details>

<details>
<summary><b>W — ARCHIVE</b> · Web archives and crawl indexes</summary>

· Wayback CDX URL enumeration, subdomain enum, historical robots.txt
· Wayback availability + snapshot retrieval
· Internet Archive item metadata / advanced search / collection search
· Common Crawl URL index, digest lookup, WARC byte-range retrieval
· Memento TimeMap, Memento aggregator discovery
· archive.today lookup, search engine cache lookup

</details>

<details>
<summary><b>X — PEOPLE/PAY</b> · People intelligence and payment fingerprinting</summary>

· Employee name enumeration, email naming convention inference
· Candidate email generation, GitHub commit email extraction
· GitHub org member enum, SMTP RCPT verification
· Cross-platform username correlation (18 services)
· Breach database correlation (HIBP), people search site links
· Payment gateway frontend fingerprint, e-commerce platform detection
· Payment orchestration layer detection, leaked payment credential search
· PSP API key pattern matching, checkout flow analysis
· Merchant risk signals, payment SDK version detection

</details>

<details>
<summary><b>Y — GEO/CRED</b> · Geolocation and web credential extraction</summary>

· Forward/reverse geocoding (Nominatim), IP geolocation
· WiFi BSSID geolocation (WiGLE), cell tower geolocation (OpenCellID)
· EXIF GPS extraction + enrichment
· Satellite imagery metadata, Street View capture, elevation lookup
· Timezone resolution, Overpass radius search
· Location history / trajectory reconstruction
· Web username/password extractor, login form detection
· Basic-auth header extractor, hidden input + comment extraction
· HTML metadata credential sweep, form login brute force

</details>

<details>
<summary><b>Z — OFFICE-DEEP</b> · Office and PDF deep analysis</summary>

· DOCX full XML tree dump, XLSX all sheets, PPTX slide metadata
· DOCX embedded fonts, tracked changes
· XLSX defined names, external links, hidden sheets, VBA macros
· PDF embedded objects, annotations, forms, incremental updates
· PDF encryption and permissions
· ODT styles, iWork preview, OneNote sections
· Visio stencils, MS Project tasks, Publisher pages

</details>

<details>
<summary><b>AA — MEDIA-DEEP</b> · Media container deep analysis</summary>

· MP4 subtitle/audio/video tracks, chapters, fragmented files, reference movies
· MKV chapters + attachments, AVI stream headers
· WAV cue points, BWF broadcast metadata
· FLAC cue sheet + PICTURE block, Ogg stream info
· WebP ICC profile, HEIC/AVIF item info
· SVG CSS + scripts, XMP full dump
· Photoshop layers, TIFF EXIF IFD, RAW camera metadata

</details>

<details>
<summary><b>AB — MOBILE</b> · Mobile app analysis</summary>

· APK permissions, activities/services, resources, signing certs
· APK assets/native libs, DEX classes, base64 strings
· IPA Info.plist, provisioning, frameworks, entitlements
· Xamarin / React Native, Flutter libapp.so, Unity assets
· Cordova/PhoneGap config, native library list
· APK version/target SDK, permissions risk scoring

</details>

<details>
<summary><b>AC — CONTAINERS</b> · Containers and Kubernetes</summary>

· Docker image config, layer commands, labels and env
· Compose file parser, K8s deployment YAML, K8s secrets decoder
· K8s service account tokens, Helm chart, Terraform state
· CloudFormation, Ansible, Vagrant, Packer, Serverless framework
· Nomad, Kustomize, Dockerfile, container env dump, cgroup limits
· OCI image manifest

</details>

<details>
<summary><b>AD — AD/KERB</b> · Kerberos, NTLM, and Active Directory</summary>

· ccache, kirbi ticket parsing, krb5.conf, krb5.keytab
· NTLM hash extraction from SAM, Kerberoast, AS-REP roast
· KDC probe, LDAP anonymous bind, LDAP root DSE dump
· AD domain info, AD users, PAC parsing
· NTLM challenge extraction from PCAP
· Kerberos realm discovery, AD CS templates, AD trusts
· gMSA password read, NTLM relay targets

</details>

<details>
<summary><b>AE — CLOUD-DEEP</b> · Deep cloud provider enumeration</summary>

· AWS IAM users, S3 buckets, EC2 instances, Secrets Manager, SSM, Lambda
· GCP projects, service accounts, storage buckets
· Azure tenants/subscriptions, storage accounts, Key Vault
· Kubernetes pods, services, cluster roles, configmaps
· Cloud instance identity, cloud-init user data
· IMDSv1 (AWS), GCP metadata server, Azure IMDS
· DigitalOcean / Alibaba / Oracle metadata, cloud storage signed URLs

</details>

<details>
<summary><b>AF — CI/CD</b> · CI/CD pipeline metadata</summary>

· GitHub Actions, GitLab CI, Jenkins, CircleCI, Travis, Drone
· Tekton, Argo Workflows, Buildkite, Woodpecker, Bamboo
· AppVeyor, Azure Pipelines, Dependabot, Renovate
· GitLab CI secrets, GitHub Actions secrets in logs
· Artifactory build info, Nexus repositories, CI runner tokens
· Build artifact signatures, pipeline env vars, SBOM in CI
· CI badge metadata, release asset metadata

</details>

<details>
<summary><b>AG — DATABASES</b> · Database configuration and metadata</summary>

· MySQL / Postgres pg_hba / Redis / Elasticsearch / Cassandra / RabbitMQ / Kafka
· SQL Server config, SQLite discovery, pg_hba.conf
· DB connection string sweep, live Redis INFO
· MongoDB isMaster, Memcached stats, Cassandra cqlshrc
· InfluxDB / CouchDB / Neo4j config
· DB error page detection, MSSQL xp_cmdshell, MySQL UDF
· Postgres extensions, Redis keys dump, Elasticsearch index dump

</details>

<details>
<summary><b>AH — MSG-QUEUES</b> · Message queues and brokers</summary>

· RabbitMQ management API, Kafka topics, MQTT broker probe
· NATS monitoring, ZeroMQ, ActiveMQ, Solace PubSub+
· Google PubSub emulator, Pulsar admin, Celery broker, RocketMQ
· AWS SQS / SNS / Kinesis, Azure Service Bus / Event Hubs, GCP PubSub
· RabbitMQ shovel/federation, Kafka topic config, MQ credentials sweep

</details>

<details>
<summary><b>AI — SECRETS</b> · Secret and token validation</summary>

· GitHub, AWS (AKIA pair), Google API, Slack, Stripe, SendGrid
· Twilio, JWT full parse, TOTP secret extraction
· GitLab, NPM, PyPI, Docker registry, DigitalOcean, Heroku
· Cloudflare, OpenAI, HuggingFace, Discord bot, Telegram bot

</details>

<details>
<summary><b>AJ — SYSTEMD</b> · systemd and journald forensics</summary>

· Unit files, journal dump, journal JSON fields
· systemd-networkd, resolved, timesyncd configs
· coredumpctl, tmpfiles rules, timers, failed services
· Service env files, coredump pattern, socket units, path units, drop-ins

</details>

<details>
<summary><b>AK — BROWSER-ART</b> · Browser artifacts deep</summary>

· Chrome extensions, Local Storage, IndexedDB, Service Worker cache
· Firefox addons, places.sqlite, logins.json, cookies.sqlite
· Chrome Login Data cookies, Web Data autofill, Shortcuts, Top Sites
· Safari history + cache, Edge profile, Brave rewards
· Search engines, sync accounts, download history
· Chrome extension cookies, Firefox formhistory

</details>

<details>
<summary><b>AL — FORENSICS</b> · Windows, macOS, and Linux forensics</summary>

· Prefetch, Amcache, ShimCache, USB history, RecentDocs
· MUICache, UserAssist (ROT13), Windows Search, thumbcache
· Windows event log parsing, $MFT, USN Journal, $LogFile
· Recycle bin $I metadata, Windows Timeline activitiescache.db
· Windows notifications, Defender scan history
· PowerShell + Bash history, RDP bitmap cache, WiFi profiles
· Clipboard history, LSA secrets, WMI repo, startup items, services
· macOS unified log, LaunchAgents/Daemons, TCC db, knowledgeC.db

</details>

<details>
<summary><b>AM — ICS/VOIP</b> · ICS, telecom, and VoIP</summary>

· Modbus, DNP3, BACnet, Siemens S7comm, EtherNet/IP CIP
· OPC-UA, PROFINET DCP, Zigbee sniff, Z-Wave
· LoRaWAN, SIP, RTP, H.323, MGCP, SS7/SIGTRAN
· Diameter, GTP-C/GTP-U, SCTP assoc, RADIUS, Diameter CER

</details>

<details>
<summary><b>AN — HARDWARE</b> · Printers and hardware inventory</summary>

· IPP printer attributes, PJL printer info, LPD queue info
· HP / Brother / Canon / Xerox printer MIBs, config page
· Print job spool, CUPS config, USB / PCI trees
· Block devices, DMI/SMBIOS, UEFI vars, memory modules
· CPU, GPU, battery, sensors

</details>

<details>
<summary><b>AO — WIRELESS</b> · Bluetooth and nearby radio</summary>

· Bluetooth device scan, paired devices, adapter info
· Nearby WiFi networks, saved WiFi credentials
· GPS device discovery, NFC tag reading, RFID reader probe
· SDR device info, WiFi monitor mode, airodump-ng survey
· WPS APs, Bluetooth LE scan, GATT services, Zigbee coordinator

</details>

<details>
<summary><b>AP — OS-LINUX</b> · Linux system enumeration</summary>

· /etc/passwd, /etc/group, sudoers, capabilities
· systemd services, kernel modules, sysctl
· iptables / nftables, resolved, mounts, env vars
· Process tree, open files, kernel params
· SELinux/AppArmor, /etc/shadow (root), interfaces
· /etc/hosts, logind sessions

</details>

<details>
<summary><b>AQ — WEB-DEEP</b> · Web application deep analysis</summary>

· robots.txt, sitemap.xml, security.txt, humans.txt, ads.txt
· HTTP security headers score, CSP parse
· Open redirect test, HTTP method enum, directory listing detection
· Backup file discovery, source map discovery
· WAF detection, reverse proxy detection, load balancer detection
· Cookie SameSite / Secure analysis, content-type handling
· HTTP caching headers, compression and encoding

</details>

<details>
<summary><b>AR — WEB-INTEL</b> · Web intelligence and scraping</summary>

· Cloudflare email protection decode, base64 email obfuscation
· Comment email scraping, JavaScript email scraping
· Contact form fields, social media links, BTC/ETH addresses
· Phone / address scraping, employee names from team pages
· RSS feed discovery, Google Analytics IDs
· Facebook Pixel, Adsense, Disqus, reCAPTCHA site keys
· Stripe publishable keys, Google Maps key, Slack workspace
· GitHub org profile, LinkedIn slug, Twitter handle guess
· Reddit subreddit, Wikipedia page scrape, Common Crawl backlinks

</details>

<details>
<summary><b>AS — INFRA</b> · Infrastructure service configs</summary>

· Docker Compose port mapping, Nginx sites, Apache vhosts
· HAProxy, Envoy, Traefik, Caddy
· WireGuard, OpenVPN, IPsec
· Keepalived, Consul, Nomad, Vault, etcd, Zookeeper
· Hadoop, Spark, NFS exports, Samba, iSCSI targets
· ZFS, Btrfs, LVM, RAID

</details>

<details>
<summary><b>AT — PICTURE</b> · Image metadata and forensic analysis</summary>

The deepest pillar in MetaPWN, covering the complete image forensics lifecycle.

Core metadata — Basic info, format detection, ICC color profile, thumbnail extraction, dominant color / palette, full EXIF dump, camera make/model/lens/serial, EXIF dates, GPS, altitude/direction, shooting settings, orientation, white balance, UserComment, Software/Firmware.

Geo enrichment — GPS reverse geocoding, elevation lookup, timezone resolution, Street View URL, satellite tile, trajectory from multiple images, geotag clustering.

Ownership — Artist / Creator / Copyright, XMP owner, dc:creator + dc:rights, IPTC creator/contact, Photoshop owner metadata, Lightroom settings, Google/Apple Photos metadata.

Timeline — Full timestamp history, Photoshop history / edit trail, filesystem timestamps, XMP edit history, software edit chain.

Steganography — Appended data detection, steganography detection (LSB/steghide), palette steganography, EXIF thumbnail mismatch, double JPEG compression detection.

Content — QR code, face detection, barcode/QR, OCR, screenshot metadata + URL leak, sensitive text in image (SSN/CC/IBAN).

Container analysis — JPEG segments, PNG chunks, GIF logical screen + frames, BMP header, ICO/CUR, JPEG2000, JPEG XL, QOI, FLIF, DDS, TGA, PSD layers, ICO frames deep, SVG element census / embedded raster / external refs.

Modern formats — C2PA / Content Credentials manifest, IPTC IIM fields, maker notes, GPS deep, HEIC auxiliary images, JPEG XT / HDR metadata, APNG info, animated WebP, AVIF sequence.

Analysis — Perceptual hash (pHash/aHash/dHash/whash), custom dHash64, reverse image search link generation, SSIM similarity, burst/sequence detection, EXIF completeness score, EXIF anomalies, metadata stripping verification, GIF frame timestamps.

Reporting — JPEG APP marker deep scan, bounding box / crop detection, histogram statistics, color histogram, sharpness/blur estimate, screenshot vs camera classification, embedded preview extraction, MIME/magic verification, comprehensive report, HEIC/AVIF thumbnails, PSD resources, xattr/ADS scan, image URL/host leak, metadata diff, final image intelligence rollup.

</details>

---

Installation

Prerequisites

· Python 3.9+
· Linux, macOS, or Windows (Linux recommended)
· Optional root for automatic bootstrap

Clone

```bash
git clone https://github.com/THE-ERROR808/MetaPWN.git
cd MetaPWN
```

Bootstrap (recommended)

Run once as root to install all optional system packages and Python libraries:

```bash
sudo python3 1.py
```

The bootstrap installer provisions:

· apt packages — exiftool, ffmpeg, mediainfo, mkvtoolnix, 7z, unrar, tesseract, steghide, binwalk, foremost, sleuthkit, testdisk, hashcat, john, hydra, sqlmap, nmap, dig, whois, curl, wget, git, aria2, rclone, smbclient, snmpwalk, and more
· pip packages — aiohttp, beautifulsoup4, lxml, PyPDF2, openpyxl, python-docx, python-pptx, olefile, Pillow, pyzbar, timezonefinder, pysmb, smbprotocol, ssdeep, tlsh, msoffcrypto-tool, python-magic, pefile, dnspython, pyOpenSSL, cryptography, yara-python, ipwhois, pytesseract, svglib, reportlab, icalendar, vobject, exifread, hachoir, pyasn1, pyasn1-modules, pyyaml, piexif, imagehash, psd-tools

Manual install

```bash
pip install -r requirements.txt    # or install individually
```

MetaPWN degrades gracefully — modules automatically skip when a dependency is missing.

---

Quick Start

```bash
python3 1.py
```

Example session

```
MetaPWN› target https://example.com
MetaPWN› B
MetaPWN› findings 100
MetaPWN› save
```

Target types

Target Example
URL target https://example.com
Domain target example.com
IP / port target 10.0.0.1:443
Local file target ./evidence/photo.jpg
Hash target 5d41402abc4b2a76b9719d911017c592
JWT target eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
Coordinates target 40.7128,-74.0060

MetaPWN auto-classifies and routes the target to the relevant pillars.

---

Command Reference

Target management

Command Description
target <value> Set target (auto-classified + auto-copied)
target Show current target
clear Clear target
info Show target type and routing
autocopy Copy target into pillar input trees

Module execution

Command Description
<number> Run module by numeric ID
<LETTER> Run all modules in a pillar (e.g. A)
<LETTER>-all Run every pillar from A to AT
chain A B C Run pillars in sequence
run <pattern> Run every module matching pattern
all Run every registered module

Listing

Command Description
show List all modules grouped by pillar
show <LETTER> List modules for a single pillar
show <pattern> Filter modules by keyword
pillars List all pillars with descriptions
count Total registered modules

Findings & reports

Command Description
findings [N] Show last N findings
save Write JSON / CSV / XML / STIX / MISP reports
artifacts List generated artifacts
clearfindings Wipe in-memory findings

System

Command Description
help / ? Command reference
banner Reprint banner
deps Optional dependency status
tools External tool availability
env Environment variables
cols <N> Set terminal width
shell <cmd> Run a shell command
python <expr> Evaluate a Python expression
history Command history
about Credits and version info
exit / quit / q Leave MetaPWN

Prefix any command with ! to force raw shell execution, ? for quick help.

---

Reports & Artifacts

Reports are written to data/reports/:

Format File Purpose
JSON report.json Full structured output
CSV report.csv Spreadsheet-friendly tabular export
XML report.xml Legacy integration
STIX 2.1 report.stix.json Threat intelligence sharing
MISP report.misp.json MISP event import
Partial partial_<session>.json Written on Ctrl+C

Every finding is also appended to data/metapwn.log as newline-delimited JSON.

---

Data Layout

```
data/
├── input_files/              # Auto-sorted by detected type
│   ├── documents/  media/    images/     archives/
│   ├── mobile/     binaries/ tokens/     strings/
│   ├── ip/         disk_images/  pcaps/  forensic/
│   ├── metadata/   office/   social/     web/
│   ├── geo/        emails/   misc/
├── pillars/
│   ├── A_EXTRACTOR/
│   │   ├── input/            # Drop files here
│   │   ├── output/           # Results land here
│   │   └── README.txt
│   ├── B_WEB-PROTO/
│   └── ... (through AT_PICTURE)
├── reports/                  # JSON / CSV / XML / STIX / MISP
├── logs/                     # session_<timestamp>.log
├── assets/                   # Generated payloads, C2, cloud, shells
├── payloads/                 # Reverse shells, encoders, stubs
├── wordlists/                # Built-in + drop your own
├── templates/
├── plugins/                  # Drop .py plugins here
├── test_samples/
├── cookies.txt               # Netscape cookie jar
├── scope.txt                 # allow / deny directives
├── rules.json                # Rule engine
├── checkpoint.json           # Resume state
├── metapwn.log               # JSONL findings log
└── KILL                      # Kill switch
```

---

Extending MetaPWN

Plugin API

Drop a .py file into data/plugins/:

```python
def register(reg):
    @reg("Z", "My custom module")
    def my_module(target, ctx):
        # your logic here
        print(f"target = {target}")
        return None
```

Load plugins with:

```
MetaPWN› F1               # runs the plugin loader
```

Rule engine

Edit data/rules.json:

```json
{
  "rules": [
    {
      "if": "content contains 'password'",
      "then": "alert possible secret leak"
    },
    {
      "if": "header Server contains 'Apache/2.4.49'",
      "then": "CVE-2021-41773"
    }
  ]
}
```

Scope control

Edit data/scope.txt:

```
allow: *.example.com, 10.0.0.0/8
deny: *.gov, 169.254.0.0/16
```

Kill switch

```
MetaPWN› F13              # toggle data/KILL
```

When data/KILL exists, modules stop executing.

---

Optional Dependencies

Check availability from inside MetaPWN:

```
MetaPWN› deps
MetaPWN› tools
```

Python libraries

```
aiohttp aiofiles beautifulsoup4 lxml requests PyPDF2 openpyxl
python-docx python-pptx olefile Pillow pyzbar timezonefinder pysmb
smbprotocol ssdeep tlsh msoffcrypto-tool python-magic pefile dnspython
pyOpenSSL cryptography yara-python ipwhois pytesseract svglib reportlab
icalendar vobject exifread hachoir pyasn1 pyasn1-modules pyyaml piexif
imagehash psd-tools
```

External tools

```
exiftool ffprobe ffmpeg mediainfo mkvinfo 7z unrar unzip zip tesseract
steghide binwalk foremost sleuthkit testdisk hashcat john hydra sqlmap
nmap dig whois curl wget git aria2c rclone smbclient snmpwalk lsusb
lspci dmidecode lsblk journalctl systemctl loginctl getcap lsof iw nmcli
bluetoothctl lpstat klist ldapsearch kubectl aws az gcloud
```

---

Safety Features

· Graceful shutdown — Ctrl+C writes a partial report before exit
· Rate limiting — global token delay, per-request
· HTTP cache — bounded LRU, avoids repeat requests
· Cookie jar — Netscape format, auto-populated from responses
· Scope file — allow / deny directives for safe-targeting
· Kill switch — data/KILL file halts all module execution
· Checkpointing — data/checkpoint.json for resumable runs
· Session logging — data/logs/session_<ts>.log + data/metapwn.log
· Artifact attribution — every generated file is recorded as a finding
· Dependency-aware — modules detect missing libraries and degrade gracefully

---

Legal Notice

```
╔══════════════════════════════════════════════════════════════════════╗
║  AUTHORIZED USE ONLY                                                 ║
║                                                                      ║
║  MetaPWN is intended exclusively for:                                ║
║                                                                      ║
║    • Authorized red-team engagements with signed scope               ║
║    • Penetration tests with written client permission                ║
║    • Digital forensics & incident response on owned systems          ║
║    • OSINT investigations on publicly available information          ║
║    • Security research & education in isolated labs                  ║
║                                                                      ║
║  Unauthorized use against systems, networks, or data you do not      ║
║  own or have explicit written permission to test is ILLEGAL and      ║
║  may violate computer fraud, privacy, and telecommunication laws     ║
║  in your jurisdiction.                                               ║
║                                                                      ║
║  The author assumes NO liability for misuse, damages, or legal       ║
║  consequences arising from use of this software.                     ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

Credits

 
Tool MetaPWN
Tagline Adversary Emulation & Metadata Intelligence Platform
Author SYLHETYHACKVENGER
Handle THE-ERROR808
Language Pure Python 3.9+
Pillars 46 (A → AT)
Modules 600+

---

<p align="center">
  <b>MetaPWN</b> — <i>Adversary Emulation & Metadata Intelligence Platform</i>
</p>

<p align="center">
  <sub>Built for operators who need everything in one REPL.</sub>
</p>

<p align="center">
  <a href="#metapwn">↑ back to top</a>
</p>
