---
title: "[SOLVED] Repository Problem"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Gwasanaethau on 2008-02-01
Hi all.

I updated my sources.list and started getting this error. Assuming it was me messing something up, I reverted to the backup that I'd saved, but the error still appears. I tried going into the repository manually with firefox, and file-roller complains of an unexpected end-of-file in the relevant 'Packages.gz' file. Does anyone know that truly is the problem, or am I missing something?

> Get:1 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/main Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/restricted Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/universe Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/multiverse Translation-en_IE
Get:2 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty-updates/main Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty-updates/restricted Translation-en_IE
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_IE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_IE
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_IE
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/restricted Sources
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty-updates/restricted Sources
Get:4 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [4 Packages gzip 0]            
[COLOR="Teal"]gzip: stdin: not in gzip format
Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 4B in 1s (3B/s)
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.[/COLOR]

---

### Post by taurus on 2008-02-01
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and pick another location or use the main server.

---

### Post by Gwasanaethau on 2008-02-01
Thanks a million! I didn't realise there was more than one server here in Ireland!

Is there any way to let the admin of that particular server know about the problem so they can sort it out?

---

