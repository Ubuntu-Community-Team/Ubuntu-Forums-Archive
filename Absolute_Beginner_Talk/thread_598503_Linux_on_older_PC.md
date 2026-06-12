---
title: "Linux on older PC"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by hlesley on 2007-10-31
I have a older PC that I am trying install 7.10 on. I did not have any luck with 7.04.
This PC has a P3 550 processor with 448mb ram and a 80gb HDD.
Both 7.10 and 7.04 run ok with the cd.
It has been a while since I tried to install 7.04, but i don't think it would even try to load.
7.10 will get to where you tell it a city in your time zone and it won't go any farther.
I don't know whether the PC is too old and slow to load and run 7.10 or what.
Any ideas? I set this PC up to load and learn more about Linux, but no luck so far. PC is slow but runs XP ok.

Thanks in advance

Herman

---

### Post by LowSky on 2007-10-31
use the alternate install cd

---

### Post by overdrank on 2007-10-31
> **hlesley said:**
> I have a older PC that I am trying install 7.10 on. I did not have any luck with 7.04.
This PC has a P3 550 processor with 448mb ram and a 80gb HDD.
Both 7.10 and 7.04 run ok with the cd.
It has been a while since I tried to install 7.04, but i don't think it would even try to load.
7.10 will get to where you tell it a city in your time zone and it won't go any farther.
I don't know whether the PC is too old and slow to load and run 7.10 or what.
Any ideas? I set this PC up to load and learn more about Linux, but no luck so far. PC is slow but runs XP ok.

Thanks in advance

Herman

Hi and welcome, have you check the cd for errors? and you may want to check checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Also if you want to just install then the alternate cd is great for installation found here
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)
Good luck!

---

### Post by kerry_s on 2007-10-31
try debian-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

you should have no problems, your specs are better than mine. i have 450mhz 256ram, i do a debian base install and build up from there so i only install what i want. you can go custom when you learn a bit and then you can build that computer for speed. :)

---

### Post by dward526 on 2007-10-31
I would suggest the alternate install of Xubuntu for an older PC.  It will run a lot nicer.  If you install Ubuntu (using the alternate CD), run the following command to speed stuff up

gconftool -2 -type bool -set /apps/metacity/general/reduced_resources true

(Thanks to The Official Ubuntu Book, 2nd Ed.)

---

