---
title: "Properly hardening ubuntu?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by damatta on 2007-08-19
Hello,
 I have been reading about hardening linux and i'm aware ubuntu is fairly secure by default, especially to the average desktop user. However, in order to improve it I was thinking of thoroughly deactivating services that are of no use for me, such as bluetooth, samba, wine etc. I started by deinstalling softwares but there was still some leftovers like  bluetooth, wine config flies. Feisty Fawn ships with BIND, but isnt it for servers?
How can I get rid of all of these unwanted stuff easily? I also appreciated if you could enlighten me as to how to improve security, taking into account my limited software needs...
Cheers :)

---

### Post by Golyadkin on 2007-08-20
You can enable SELinux. Read up on it here: [https://wiki.ubuntu.com/SELinux](https://wiki.ubuntu.com/SELinux)

---

### Post by Felix-the-Cat on 2008-02-24
Enabling SeLinux can help increase the security of ubuntu (ik ubuntu is secure out of the box but you can have too  much security unless your talking about unhooking your computer from the internet, unplugging the keyboard and mouse toot), however if you are using a FS such as reiserfs it can cause more headache than it is worth. Anyway, it appears that Ubuntu may be working on implementing Apparmor especially since it was released into the GPL in September 2007 (I would like to know if this is definitely true). Personally, I'm just waiting on Apparmor because it overcomes many of the problems in SELinux. I have been reading on hardening Linux and found this article: . Some of the suggestions looked as though they would be beneficial to implement but I'm not sure of the implications of doing these things on Ubuntu. I'm running Ubuntu Server 6.06.

---

