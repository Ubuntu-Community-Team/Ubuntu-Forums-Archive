---
title: "Downloading Debian"
date: 2011-11-30
forum: Any Other OS
---

### Post by Spyderkid on 2011-11-30
I'm trying to find a direct link for debian 32bit, however Debian have managed to make there website super complicated and I can't finda direct link...?

Can someone post a link here please :)?

---

### Post by ObsidianCommand on 2011-11-30
Here [http://cdimage.debian.org/debian-cd/6.0.3/i386/iso-cd/debian-6.0.3-i386-netinst.iso](http://cdimage.debian.org/debian-cd/6.0.3/i386/iso-cd/debian-6.0.3-i386-netinst.iso) be adviced that this link leads to the net installation .iso image.

---

### Post by Frogs Hair on 2011-11-30
[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

---

### Post by Spyderkid on 2011-11-30
Found a direct download link :D

[http://cdimage.debian.org/debian-cd/6.0.3/i386/iso-cd/debian-6.0.3-i386-CD-1.iso](http://cdimage.debian.org/debian-cd/6.0.3/i386/iso-cd/debian-6.0.3-i386-CD-1.iso)

---

### Post by k357k9 on 2011-12-01
Here is the LiveCD List -- [http://www.livecdlist.com/debian]("http://www.livecdlist.com/debian")

---

### Post by Spyderkid on 2011-12-01
[edit] post irrelevant

---

### Post by realitykid on 2011-12-01
> **Spyderkid said:**
> Which version should I download for my 64bit computer... when I downloaded the AMD64 one and after installing it just came up with a text console, not a graphical desktop environment.

The options are as folows amd64,armel,kfreebsd-i386kfreebsd-amd64,i386,ia64,mips,mipsel,powerpc,sparc,s390,source,multi-arch

AMD64 is typically what you want for a 64bit installation. That's what I had to use on my 64bit laptop with Ubuntu. So, I'm not sure why you landed in a command line and not a graphical interface. :confused:

---

### Post by lykwydchykyn on 2011-12-01
If you didn't get a GUI, either X is having a hard time with your video card, or your didn't mark "graphical desktop" during the tasksel portion of the install.

Try logging in and running "startx".  If X11 tries to start and gives you errors, probably a driver issue.

If it says "command not found", install xorg and the desktop of your choice, e.g.
```

aptitude install xorg xfce4

```

---

### Post by Spyderkid on 2011-12-01
Lol yeah, clicked install, not graphical install :)

no worries, case closed

---

### Post by VanR on 2011-12-02
Good luck. I've had good luck installing Debian Stable, but I've installed Debian Testing 3 times now. 2 times I had no internet when finished installing, and 1 time it didn't install the linux kernel. Just bad luck on my part I guess. If you have a good internet connection I would suggest you just download the netinstall ISO or the business card ISO.

---

### Post by Spyderkid on 2011-12-03
I'm going stable :), i'm only installing in virtual box though, so no worries XD

---

