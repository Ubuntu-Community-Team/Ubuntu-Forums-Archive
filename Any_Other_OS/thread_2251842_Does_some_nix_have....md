---
title: "Does some *nix have...?"
date: 2014-11-07
forum: Any Other OS
---

### Post by i12 on 2014-11-07
Does some *nix have software install center as Ubuntu have? Which one?

---

### Post by TheFu on 2014-11-07
Oops - wrong thread.

So .... Software Center is just a GUI over the package manager that limits the packages presented to keep it simple for end users.  There are other front-ends, like synaptic, apt-get, aptitude .... 

Which *NIX are you interested in?  These are tied to hardware, so asking without having that hardware isn't often useful.
I've never seen any real package manager on UNIX ... most work at the dpkg or rpm level.  Solaris, AIX, HP-UX, Irix, DigitalUNIX .... which ?

---

### Post by Lars Noodén on 2014-11-07
The Software Center is a little special so you will not find exactly that elsewhere.  However, you will find huge software repositories in Debian and other Debian-based distributions like Mint.  Those will be accessible via Synaptic or in the shell via APT.  

Elsewhere, PC-BSD has the same [s]pkg[/s] ports system that FreeBSD has, since it is based on FreeBSD.  OpenBSD also has a pkg system but it is different than FreeBSD's.  If I remember correctly Illumos is using NetBSD's pkg system.  And Minix has it's own, even though it mostly uses NetBSD's userspace utilities.

Edit: pkg -> ports

---

### Post by mips on 2014-11-07
[http://wiki.pcbsd.org/index.php/AppCafe%C2%AE/9.2](http://wiki.pcbsd.org/index.php/AppCafe%C2%AE/9.2)

---

### Post by Lars Noodén on 2014-11-07
> **mips said:**
> [http://wiki.pcbsd.org/index.php/AppCafe%C2%AE/9.2](http://wiki.pcbsd.org/index.php/AppCafe%C2%AE/9.2)

Cool.  I'm going to have to try the new way as soon as I can set up a spare machine.

---

### Post by vasa1 on 2014-11-07
In other words, PC-BSD has "Click" packages already. Nice read!

---

### Post by slickymaster on 2014-11-07
> **mips said:**
> [http://wiki.pcbsd.org/index.php/AppCafe%C2%AE/9.2](http://wiki.pcbsd.org/index.php/AppCafe%C2%AE/9.2)

Thanks for this mips. Very interesting indeed.

---

### Post by mips on 2014-11-08
> **slickymaster said:**
> Thanks for this mips. Very interesting indeed.

Thing is I reckon you will be disappointed using a bsd based os for the desktop, boot time is really slow, flash only works via linux emulation. I downloaded dragonfly bsd the other day but I have not tried it yet, maybe this week on new hdd. Software centre based gui interfaces don't really do it for me.

PBIs don't interest me, reminds me of leaving Sabayon when they started with their binary packages. I'm just old school I suppose.

---

