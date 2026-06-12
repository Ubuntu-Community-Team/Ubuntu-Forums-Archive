---
title: "i have some questions"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by simion314 on 2007-06-27
i want to install the latest version of monodevelop but i can't because i need to install first mono.  I use the installer from mono web site(they have an installer that works for all linux disributions) but the ubuntu packege manager do not sees those libreries and i musy install them, I have tried to install  the packeges manualy but are too many.. i wan t to compile mono but i belive that i will have the same problem with the packege manager, i have ubuntu 6.10.
 I belive i must copy some libreries in ubuntu GAC but i do not  where to put them (or to make a link for them), the moono installer does not put his libraries in the /lib or other locations, it makes a folder in my home directory. Please help me , i wan tto enderstend how ubuntu works and how to fix this.
Thanks

---

### Post by zanglang on 2007-06-27
Why not just install from Synaptic? There's a full package along with a bunch plugins available, and will automatically grab any dependencies for monodevelop. Or if you prefer the commandline:
> sudo aptitude install monodevelop

---

### Post by simion314 on 2007-06-27
in synaaptic monodevelop is only version 0.12 and the curent stable version is 0.14.  I have ubuntu version 6.10 , there are diffrent repositories for difrent versions of ubuntu?
I have problems upgrading, i do not have the options to upgrade and neither from terminal i can't it sais thar are 0 packeges to upgrade. Maybe i should reinstall ubuntu or upgrade from the cd

---

### Post by zanglang on 2007-06-27
Ah no, 7.04 here has version 0.12 packaged as well. Their webpage offers RPMs for download, maybe you could try converting them to .deb and install? Download the RPM from 2nd link here:
[http://www.monodevelop.com/Download](http://www.monodevelop.com/Download)

Now, you'll need a separate tool, Alien, for converting to .deb first There's a good guide here:
[http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)

When you're done just install the Monodevelop .deb the usual way.

Edit: Just realized that the new .deb doesn't record dependencies... So you'll probably have to manually install them from Synaptic.

---

