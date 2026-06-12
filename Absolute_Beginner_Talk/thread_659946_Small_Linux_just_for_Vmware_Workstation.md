---
title: "Small Linux just for Vmware Workstation"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by goodhope on 2008-01-06
hi all,

first of all, i have never worked with any linux. now i need a test environment with 1 or 2 xp clients and 1 to 3 win 2003 server. i want to use vmware workstation 6 therefore.
i have an old notebook (fsc amilo pentium m 1.7 and 1gb ram) that i want to use for this projekt.
i thought it would be lightweight to use linux than windows as host für vmware but i don't know which distribution.

since i don't want to work with the linux installation a lightweight windowmanager or comand line installation or ubuntu server installation would be the best. do you agree or are there better ways to realize my virtual environment?

---

### Post by Dr Small on 2008-01-06
Install Ubuntu from the alternate cd and choose a command line system only. That's what I did for about the same thing (VirtualBox).

Then you can just launch your VMware (once you install Xorg and maybe a window manager like IceWM or Fluxbox) and it will be fullscreen and lightweight :)

Dr Small

---

### Post by goodhope on 2008-01-06
> **Dr Small said:**
> Install Ubuntu from the alternate cd and choose a command line system only. That's what I did for about the same thing (VirtualBox).

Then you can just launch your VMware (once you install Xorg and maybe a window manager like IceWM or Fluxbox) and it will be fullscreen and lightweight :)

Dr Small

should i download ubuntu kubuntu or xubunto as alternate version or doesn't it matter?

and there al different ubuntu versions on the download page: [http://wiki.ubuntuusers.de/Downloads#Downloads](http://wiki.ubuntuusers.de/Downloads#Downloads)
which should i use, gutsy gibbon?

---

### Post by snickers295 on 2008-01-06
If you use a command-line system, Ubuntu, Kubuntu and Xubuntu the same because the only difference is the window manager.
also you could use Serbuntu (my name for Ubuntu Server)

---

### Post by eazi.it on 2008-03-21
has anyone been so kind as to do a step by step guide for this small as possible ubunto text only running vmware?

---

### Post by Paqman on 2008-03-21
Is a text-only system really very practical for someone who's not used Linux before though?

A simple way to achieve what you want would be just to install Xubuntu, then trim anything you don't need afterwards. That would give you the window manager you need as well as all the GUI tools that a new user would want (eg: Synaptic for installing VMWare)

---

### Post by bodhi.zazen on 2008-03-21
You might want to tyr JeOS, it was designed for exactly this tank :

[http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos](http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos)

---

### Post by eazi.it on 2008-03-21
I think you are right Paqman.

I have installed linux several times but my familiarity with windows always draws me back :(

What I actuall want to acheive is to host both my IPcop firewall and Win 2K3 domain controller on the same physical box.

Obviously the IPCOP requires very little resource and the domain controller is never touched so to put both on one piece of hardware in the server room makes perfect sense.

---

### Post by bodhi.zazen on 2008-03-21
Well JeOS is optimized for virtualization, if you want a minimal install you can look at the minimal CD :

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Or installing via chroot/debootstrap

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

---

### Post by eazi.it on 2008-03-21
> **bodhi.zazen said:**
> Well JeOS is optimized for virtualization, if you want a minimal install you can look at the minimal CD :

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Or installing via chroot/debootstrap

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

lol, note to self if you don't understand the instructions then don't try 

lol

---

