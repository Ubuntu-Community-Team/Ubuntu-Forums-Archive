---
title: "apt-get build-dep reports problem with sources.list"
date: 2014-05-26
forum: Any Other OS
---

### Post by MickSulley on 2014-05-26
I am trying to resolve some problems instaiing DigiKam.  But when I run

sudo apt-get build-dep digikam 

It returns

E: You must put some 'source' URIs in your sources.list

When I looked at sources.list it was empty (except for a commented line), the repo definition was in /etc/apt/sources.list.d/official-package-repositories.list.  I have tried moving the definition to /etc/apt/sources.list but I still get the error.

How do I fix this?

---

### Post by steeldriver on 2014-05-26
I've not come across that setup before - what flavor and version of Ubuntu is this?

However, afaik it shouldn't actually matter whether your sources are defined via /etc/apt/sources.list or via other .list files in the /etc/apt/sources.list.d directory - it should just be a question of having the appropriate deb-src lines SOMEWHERE

---

### Post by MickSulley on 2014-05-26
It is on Mint, I have tried Mint 16 (based upon Ubuntu 13.10) and Mint 17 (Ubuntu 14.04) with the same results.  Any idea how I can fix it or find a workaround?

---

### Post by howefield on 2014-05-26
Thread moved to the "*Other OS/Distro Support* forum.

---

