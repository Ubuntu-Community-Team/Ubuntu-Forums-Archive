---
title: "Automatic xconfig failover?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by gnomic on 2007-05-29
I'm running 6.10 because of nvidia/7.04 issues that I'm not yet up to fixing. I set 6.10 up with a bench monitor, then hooked it to my LCD. For some reason it is picking some settings WAY outside the range fo the monitor. I'm assuming from what I've read here that the command

sudo dpkg-reconfigure xserver-xorg

will fix this problem. 

However, I'm wondering why there isn't a automatic failover to a default setting, or at lease a boot option to run this automatically? Or is there and I'm just missing it?

---

### Post by Sparkster185 on 2007-05-29
Before I touch my xorg.conf file, I always copy it to a backup.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK

```

If you're having issues with nVidia stuff, try using Envy.  It's a script that downloads/configures all the nvidia tolls/drivers/etc.  Worked great for me in Feisty.

---

### Post by ikonia on 2007-05-29
if you have automatix installed, I suggest you visit their site and forum and request support. 

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by gnomic on 2007-05-29
> **ikonia said:**
> if you have automatix installed, I suggest you visit their site and forum and request support. 

[http://www.getautomatix.com/](http://www.getautomatix.com/)

I've nto installed automatix - until I know more, I'm sticking to conservitive (supoprted) options.

---

### Post by gnomic on 2007-05-29
> **Sparkster185 said:**
> 
If you're having issues with nVidia stuff, try using Envy.  It's a script that downloads/configures all the nvidia tolls/drivers/etc.  Worked great for me in Feisty.

I would, but I couldn't get the system to boot with a GeForce 8500, so I'm using a Geforce 7300 which was working fine until I switched monitors - now I can't see anything. :mad: Its one of my pet useability peeves - leaving the user (me) in a possition that is difficult to recover from. No matter what the reason, a level of service less than what XP provides isn't a good thing for linux. Not everyone is a geek (like us).

---

