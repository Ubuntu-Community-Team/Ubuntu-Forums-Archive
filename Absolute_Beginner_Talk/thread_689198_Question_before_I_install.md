---
title: "Question before I install"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by nothingspecial on 2008-02-06
Hi, I have Ubuntu up and running on my pc and love it. I`d like to install it on my laptop as well.
I had quite a hard time getting everything going on my pc and needed a friend to come round a few times and sort it out and I don`t want to bother him too much more. So my question is - if my laptop`s hardware works with the live cd, specifically the wireless lan, sound and graphics, will they definitely work when I wipe windows and do a full Ubuntu install.
 Thankyou in advance.

---

### Post by jken146 on 2008-02-06
Yes

---

### Post by imT on 2008-02-06
it should, but you never know... :)

---

### Post by nothingspecial on 2008-02-06
Thankyou guys. I`ll go for it then.

---

### Post by fourscore on 2008-02-06
If you are not pressed for space on the hard disk, instead of wiping out XP,  you can dual boot and once satisfied that  Ubuntu  runs well  you can  delete the xp partition.

---

### Post by aeiah on 2008-02-06
some people have reported the odd glitch when its actually installed, but it is unusual. also, if it works on the livecd, then even if it doesnt when installed, it certainly will with a bit of tinkering

---

### Post by nothingspecial on 2008-02-06
Chickened out and did a dual boot install. Ubuntu working perfectly. Is there an easy way to remove windows or should I just install again using entire disk. There`s nothing in windows I want, all my files are on my pc.

---

### Post by jan quark on 2008-02-06
the easiest way is to install ubuntu and during the partitioning select guided entire disk

this will not allow you to create a additional /home partition but linux will wipe your whole drive and you have the full capacity used

you can also download the gparted live CD
and make a cd, boot from it and format the windows partition to ext3

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

ask for more help...

---

### Post by imT on 2008-02-06
> **jan quark said:**
> the easiest way is to install ubuntu and during the partitioning select guided entire disk

this will not allow you to create a additional /home partition but linux will wipe your whole drive and you have the full capacity used

you can also download the gparted live CD
and make a cd, boot from it and format the windows partition to ext3

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

ask for more help...
no :( select manual, be careful to allocate swap (somewhere said double of the ram), / (root)(at top 10Gb-min.4), and /home (home)(rest of space)

---

### Post by nothingspecial on 2008-02-06
thanks again guys

---

