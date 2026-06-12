---
title: "Update errors"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by poloman2 on 2006-01-20
this is what i get afeter i type 

sudo apt-get update
it says not in gzip format, what should i do?

[HTML]Get:1 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://archive.ubuntu.com hoary-updates Release.gpg [189B]
Get:3 http://archive.ubuntu.com hoary-backports Release.gpg [189B]
Hit http://archive.ubuntu.com hoary Release
Get:4 http://archive.ubuntu.com hoary-updates Release [16.8kB]
Get:5 http://archive.ubuntu.com hoary-backports Release [11.3kB]
Hit http://archive.ubuntu.com hoary/main Packages
Hit http://archive.ubuntu.com hoary/restricted Packages
Hit http://archive.ubuntu.com hoary/main Sources
Hit http://archive.ubuntu.com hoary/restricted Sources
Ign http://archive.ubuntu.com hoary/universe Packages
Ign http://archive.ubuntu.com hoary/universe Sources
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://archive.ubuntu.com hoary-updates/main Packages
Hit http://archive.ubuntu.com hoary-updates/restricted Packages
Hit http://archive.ubuntu.com hoary-updates/main Sources
Hit http://archive.ubuntu.com hoary-updates/restricted Sources
Hit http://archive.ubuntu.com hoary-backports/main Packages
Hit http://archive.ubuntu.com hoary-backports/restricted Packages
Hit http://archive.ubuntu.com hoary-backports/universe Packages
Hit http://archive.ubuntu.com hoary-backports/multiverse Packages
Get:6 http://archive.ubuntu.com hoary/universe Packages [2853kB]
99% [6 Packages gzip 0] [Waiting for headers] [Connecting to security.ubuntu.co
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com hoary/universe Packages
  Sub-process gzip returned an error code (1)
Get:7 http://archive.ubuntu.com hoary/universe Sources [1142kB]
99% [7 Sources gzip 0] [Connecting to security.ubuntu.com (82.211.81.138)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com hoary/universe Sources
  Sub-process gzip returned an error code (1)
99% [Connecting to security.ubuntu.com (82.211.81.138)]
[/HTML]

---

### Post by bulldogzerofive on 2006-01-20
Have you tried using the graphical front end synaptic to do this?

---

