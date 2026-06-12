---
title: "Compilation Error"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-03-03
Hi everyone, 

I am new to this.  I need to upgrade ALSA.  I am following the instructions here:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=upgrade+alsa](http://ubuntuforums.org/showthread.php?t=205449&highlight=upgrade+alsa)

```
brandon@brandon-laptop:~/alsa-driver-1.0.14rc2$ sudo ./configuresudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<stac92xx> --with-oss=yes
bash: stac92xx: No such file or directory

```

I put Stac92xx in there, because that is my card.  However, it looks like it is not right.  I looked at the Changelog for 1.0.14rc2 and they say that my sound should work now, so is there something I can put here for driver that would be default or something?

I have Sigmatel Stac92xx on Gateway MX3414

---

### Post by Bachstelze on 2007-03-03
> sudo ./configuresudo ./configure

I think your problem is here ;)

---

### Post by brandoncolorado on 2007-03-03
Sorry that was just a typo, the part I have a question about is the driver part.  Can I just use sudo ./configure by itself?

---

### Post by Maestro23 on 2007-03-03
> **brandoncolorado said:**
> Sorry that was just a typo, the part I have a question about is the driver part.  Can I just use sudo ./configure by itself?

You have the d/l link for the driver?

---

### Post by brandoncolorado on 2007-03-03
> **Maestro23 said:**
> You have the d/l link for the driver?

[http://www.alsa-project.org/download.php](http://www.alsa-project.org/download.php)

---

### Post by brandoncolorado on 2007-03-03
I installed ALSA 1.0.14RC2 by doing this:

sudo ./configure
sudo make
sudo make install

it seemed to work, but I don't think it did.

Synaptic still shows 1.0.11

and 

there is no /proc directory.

How did I screw this up?

---

