---
title: "synaptic package manger help"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Jason_howard on 2007-07-17
when I open it up I get this

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
 
 is this bad?

---

### Post by useResa on 2007-07-17
Could you post the content of your sources.list file?
You can get the content by opening a terminal (Applications --> Accessories --> Terminal) and issue the command ```
cat /etc/apt/sources.list
```

---

### Post by AlexenderReez on 2007-07-17
don't need to post...you have duplicate sources list....

just

> gksudo /etc/apt/sources.list

search that error list...it will give to lists for each search remove one....
:)

---

