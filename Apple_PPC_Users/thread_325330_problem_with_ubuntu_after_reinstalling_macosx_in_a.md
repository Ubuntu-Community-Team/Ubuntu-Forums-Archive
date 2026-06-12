---
title: "problem with ubuntu after reinstalling macosx in a dualboot PB G4"
date: 2006-12-25
forum: Apple PPC Users
---

### Post by Marco Renoldi on 2006-12-25
Hello
I had to reinstall MacOsx on my Powerbook G4 and now I dont know how to regain access to my ubuntu partition.... How do I reinstall yaboot without having to reinstall Edgy?
Many thanks
Marco

---

### Post by calum on 2006-12-25
First boot into Edgy by holding down Command (Apple key) while the PowerBook is rebooting, and selecting your Linux partition when you get the choice.  Once you're there, log in and run 'sudo ybin' to get your boot menu back (but be sure your yaboot.conf is correct first, if you changed any partitions when you reinstalled OSX).

---

### Post by Marco Renoldi on 2006-12-25
I tried to hold down the apple key but nothing happened, so I tried with the alt key. I got a blu window with only the mac partition.... It seems it cannot see the linux partition...

---

### Post by Marco Renoldi on 2006-12-26
I managed to have edgy back following this guide
[http://www.gentoo.org/doc/it/handbook/2004.3/handbook-ppc.xml?part=1&chap=10](http://www.gentoo.org/doc/it/handbook/2004.3/handbook-ppc.xml?part=1&chap=10)

---

### Post by handylinux on 2006-12-26
You might find [this thread]("http://www.ubuntuforums.org/showthread.php?t=318682") of interest.

---

