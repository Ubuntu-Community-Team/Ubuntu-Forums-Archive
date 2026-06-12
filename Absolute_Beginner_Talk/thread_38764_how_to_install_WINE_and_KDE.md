---
title: "how to install WINE and KDE?"
date: 2005-06-01
forum: Absolute Beginner Talk
---

### Post by reynoldlariza on 2005-06-01
ok, i know i'm already a byte comfortable with Gnomes, but I still like to have KDE and wine installed?

how do I install these?


P.S. 
I have a wine package in .tgz compressed.
I was thinking of installing this copy from my CollegeLinux distribution, also for the KDE too. Which means these are not on .deb (debian packaging).

I'll try to do some trial and errors, but if anybody have done it alraedy, I would appreciate it :)

---

### Post by bored2k on 2005-06-01
[QUOTE=reynoldlariza]ok, i know i'm already a byte comfortable with Gnomes, but I still like to have KDE and wine installed?

how do I install these?


P.S. 
I have a wine package in .tgz compressed.
I was thinking of installing this copy from my CollegeLinux distribution, also for the KDE too. Which means these are not on .deb (debian packaging).

I'll try to do some trial and errors, but if anybody have done it alraedy, I would appreciate it :)[/QUOTE]
 Open up Applications > System Tools > Terminal
0. Prerequisites: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
1. sudo apt-get install wine wine-utils wine-doc msttcorefonts
2. sudo apt-get install kubuntu-desktop

That's what apt is for. And DO NOT install software from other distributions..

---

