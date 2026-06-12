---
title: "Installing another operating system"
date: 2005-08-06
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-08-06
I am very new to linux, so far i have tried ubuntu warty, at first i seemed to have a heap of trouble getting it runnng, but thanks to some patient help on these forums it's now up and running pretty well. I had lots of hassle especially with getting the internet running properly, but even thats fine now.

My question is i have a p4 system  with 160 gig hardive, it's divided into several partions, i have windows on c drive, then ubuntu, and the other partions are all empty.I have a couple of other distros i would like to try(mandravia, and xandros), but i don't want to stuff it all up as things are running pretty well.Is it just a case of installing them on the other partitions and grub will sort it all out for me, or is there more to it than that?. I did upgrade something(which took 24 hrs of downloading on my dial up) and now on boot up i get an extra choice i have ubuntu ver 1.5, , 1.3 and windows, so i'm presuming i upgraded to a newer version.

---

### Post by GavinX on 2005-08-06
If you install any of the distros which you mentioned, Grub will pretty much do the configuration for you. You don't have much to worry about.

---

### Post by aysiu on 2005-08-06
I don't believe Grub will sort it all out for you unless you re-install Grub, let one of the new distros take over the MBR, or edit /boot/grub/menu.lst manually to add the other distros.

---

### Post by GavinX on 2005-08-06
[QUOTE=aysiu]I don't believe Grub will sort it all out for you unless you re-install Grub, let one of the new distros take over the MBR, or edit /boot/grub/menu.lst manually to add the other distros.[/QUOTE]
Actually, I should have explained myself in this way. What I actually meant is that one of the new distros would ask whether or not to overwrite the MBR and by allowing it to, all would be sorted out automatically. Thanks much,aysiu.

---

