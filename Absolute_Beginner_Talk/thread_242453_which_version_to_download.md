---
title: "which version to download ?"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by hkgonra on 2006-08-23
I have an system running dual athlon xp 2400's, I plan to use it as a server for mail and web maybe FTP. 

Which version do I need to download ? 

The motherboard is an ABIT KD-7 with 4 80gb sata hd's in raid 5.

---

### Post by Turgon on 2006-08-23
You got to options. 

The ubuntu 6.06 desktop i386 or the ubuntu 6.06 server i386.

I don't know to much about server stuff, but I beleve that you will be fine with both.

Hope someone here can give some better tips than I can, but generaly you can just apt-get everything you need.

---

### Post by hkgonra on 2006-08-23
Will both of those have smp support ?

---

### Post by Turgon on 2006-08-23
I don't think Ubuntu commes with SMP turned on by default, but you can install the linux-k7 smp kernel in synaptic, so you can have it in both.

---

### Post by Shortgeek on 2006-08-23
Do you want a GUI? If you install the server edition, it isn't installed out of the box. But you can install a GUI later, and since you wanted a server, I would do server. Just be warned: you'll be put into a command line until you run

```
sudo apt-get install (k,x,ed)ubuntu-desktop
```

---

### Post by David Corrales on 2006-08-23
The server and desktop version both use the same base packages. The server edition has a server optimized kernel (duh) which is SMP enabled.
I'd go with a server install and then add whatever GUI components you want along the way, like webmin for example or a full desktop if you need it.

---

### Post by hkgonra on 2006-08-23
I do want a GUI installed. 
I am a COMPLETE linux NOOB!!! 
I can make my way around any windows distro blindfolded but not linux... yet :p

---

### Post by David Corrales on 2006-08-24
Install the server then a meta package with your desktop of choice :)

---

### Post by Metacarpal on 2006-08-24
I agree with the general consensus above.  Do a server installation. (Download your ISO [from this page]("http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/") - you'll want to scroll down about half-way and click "64-bit PC (AMD64) server install CD".) Then once the installation is completed and you reboot, you'll arrive at a command prompt (no gui).  Then you can just type:
```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```
It'll prompt you for your password; just give it your regular login password.  Once the installation completes, you can type "startx" or simply reboot to get into the graphical environment.

The default environment for Ubuntu is called Gnome.  There are two other main desktop environments called KDE and XFCE.  Those are bundled under kubuntu-desktop and xubuntu-desktop, respectively.  KDE is heavier on eye-candy and has a more Windows-like setup and feel.  XFCE is much lighter-weight and takes up less resources, but it also has fewer customization options.  Gnome is somewhere in-between.

Which is better?  For the love of whatever you deem holy, don't ask.  Everybody's got a favorite, and there are SO many threads beating that dead horse on here already... just do a search with the word "better" and KDE, Gnome, or XFCE and you'll see what I mean.  In the end, it's a matter of personal preference.

---

### Post by hkgonra on 2006-08-24
I don't have 64-bit processors.

---

### Post by Metacarpal on 2006-08-24
> **hkgonra said:**
> I don't have 64-bit processors.

Sorry about that - the i386 one is the way to go, then.

---

