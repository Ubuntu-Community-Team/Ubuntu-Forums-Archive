---
title: "[SOLVED] Gutsy or Feisty will not install"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2007-11-04
I tried using a gutsy alt CD but when xserver packages get installed, the screen scrambles and is unreadable. After a while the install hangs. This disk worked fine on my old laptop.

I then used my old feisty desktop cd, and I got the 'can't access tty: job control turned off.' I fixed this problem, but then I got the xserver failed blue screen. No matter what I tried, I alwyas got the message 'xserver failed.'

laptop specs:

[novatech rasor pro](http://www.novatech.co.uk/novatech/specpage.html?NNB-560)
Intel Core 2 Duo Mobile T7100 2Mb Cache Dual Core Processor
2GB DDR2 667MHz Memory
160GB SATA Hard Drive
**Intel GMA X3100 Graphics**

Does anyone know a work around so I can install gutsy?

Cheers

---

### Post by alienexplorers on 2007-11-04
have you done a 
> sudo dpkg-reconfigure xserver-xorg

---

### Post by spamzilla on 2007-11-04
yep I tried several graphics drivers and all resulted in the 'xserver failed' scren :(

---

### Post by Malta paul on 2007-11-04
When you boot your alt disk and get the menu screen try F4 and set the screen resolution you have used before.
Hope this works for you
There is a good video on:[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)
That may also help

---

### Post by spamzilla on 2007-11-04
> **Malta paul said:**
> When you boot your alt disk and get the menu screen try F4 and set the screen resolution you have used before.
Hope this works for you

I think this option is set to VGA, so I'll change it and see what happens.

Thanks so far guys :KS

---

### Post by spamzilla on 2007-11-04
Changing my screen resolution worked, but now the install is hanging when installing/configuring Tomboy. Is there anyway I can skip this package so the install can resume? Or is there anything else I can do to resume the install?

Thanks

---

### Post by ByteJuggler on 2007-11-04
Can you please check the CD (using the "Check CD" option on the initial boot menu) for both CD's **on the laptop you're trying to install to**  (Just trying to ensure we're not also dealing with a CD-reader/disc incompatibility as well here.)

---

### Post by spamzilla on 2007-11-04
> **ByteJuggler said:**
> Can you please check the CD (using the "Check CD" option on the initial boot menu) for both CD's **on the laptop you're trying to install to**  (Just trying to ensure we're not also dealing with a CD-reader/disc incompatibility as well here.)

I hit alt + ctrl + f4 and saw that for some reason tomboy couldn't be installed via the cd, so it was trying to download the package from the repos. So I plugged my laptop in to my Ethernet connection (wireless wasn't working :/) and it fixed my problem :D

Thanks all :guitar:

---

