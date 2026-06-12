---
title: "More DMA problems"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by dylanknightrogers on 2005-11-14
Hi, Ive posted something like this before.

I have a 52x CD-R/RW drive...cannot burn or rip past 7x....I enabled DMA using the hdparm.conf and bootmisc.sh files.

Still, nothing.

This is my only complaint with Ubuntu...please help me!!

Under Slackware I can burn with k3b at 52x...

---

### Post by Samuel on 2005-11-15
adding this to the bottom of /etc/hdparm.conf
```
/dev/cdrom {
       dma = on
}
```
should enable DMA

and to see if its working ```
sudo hdparm /dev/cdrom
```
if DMA is active on your cd drive maybe you should try different CD burning software, i personally like graveman

---

### Post by dylanknightrogers on 2005-11-15
i get the same burning speeds whatsoever.

i have tried /dev/cdrom and /dev/hdd (in my case) and still nothing.

i have also tried graveman...still nothing.  i tried gnomebaker, k3b and graveman on ubuntu and experience problems.

however, slackware had no issues.  why?

---

