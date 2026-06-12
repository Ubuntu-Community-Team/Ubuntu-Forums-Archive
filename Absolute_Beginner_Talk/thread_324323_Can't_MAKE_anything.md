---
title: "Can't MAKE anything"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by mastergamer on 2006-12-23
Hi, I've used linux a bit before (at school), and I liked it there. I ordered a 6.06 CD a while ago, and never got around to installing it. I finally did so today, and I found out that I can't use make.

I'm trying to compile ndiswrapper, so I can use my usb wireless adapter, so surrently I have no internet on my ubuntu box. I downloaded and extracted ndiswrapper-1.32.tar.gz

I then proceeded to run "make uninstall" in the ndiswrapper directory, as instructed by the INSTALL file. I got the error message "bash: make: command not found". I get the feeling that something is terribly wrong if make dosen't exist...

---

### Post by Adramelech on 2006-12-23
i think u need automake from repos to get make.

---

### Post by fdoving on 2006-12-23
Hi. You need to install the build-essential package.

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

- Frode

---

### Post by mastergamer on 2006-12-23
Thanks, I have installed build-essential from my ubuntu CD and make works now :D

---

