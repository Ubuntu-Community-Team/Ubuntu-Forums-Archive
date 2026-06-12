---
title: "Display brightness can't be changed"
date: 2010-03-25
forum: Apple Hardware Users
---

### Post by cyberco on 2010-03-25
I am running Karmic (9.10) on my macbook air (2,1) and although many things work fine (I wrote about it here: [https://help.ubuntu.com/community/MacBookAir2-1/Karmic](https://help.ubuntu.com/community/MacBookAir2-1/Karmic)) one of the last things that doesn't work is setting the screen brightness. The FN-F11/F12 combo does bring up the brightness adjustment notification window (top right) and I can change the setting, but it has no effect UNTILL I reboot or suspend to RAM and reboot.

A related issue is that the brightness doesn't automatically adjust to the surrounding brightness.

Thanks!
Berco

---

### Post by linuxopjemac on 2010-03-25
maybe you can ask the pommed guys for a feature request (MacBook Air 2,1).
[http://alioth.debian.org/projects/pommed/](http://alioth.debian.org/projects/pommed/)

It seems that there is a new version 1.32 out. It might work for MacBook Air 2,1...

---

### Post by cyberco on 2010-03-25
Pommed 1.32 seems like it might solve the problem. Do you know if there is some 'software source' (repos) where I can get it from for Karmic? Make, build and copying files by hand is always possible but I'd rather take the short route. :)

Groet!

---

### Post by linuxopjemac on 2010-03-26
Dear cyberco, you have pommed in your repository. I don't know at which version it is currently, but to install you simply:
```
sudo apt-get install pommed
```

Restart and you will have pommed running.

Edit: Apparently very old ( v 1.26)
[http://packages.ubuntu.com/karmic/pommed](http://packages.ubuntu.com/karmic/pommed)

---

### Post by linuxopjemac on 2010-03-26
You can add the Mactel PPA repository and install a more recent pommed (v 1.30)

[https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)

---

### Post by cyberco on 2010-03-26
Great, pommed 1.30 indeed solved the problem. Thanks!

---

### Post by linuxopjemac on 2010-03-26
fantastic !!

---

