---
title: "Need help... most basics of all basic things"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by sunnymw on 2008-03-17
Hi, I'm Sunny, and this is my first post.... I am a DIYer by nature, so I tried fixing this problem myself, but I've probably just messed things up even more, so I need your help...


Background: My friend and I built my PC together. Admittedly, I brought the cash and he brought the brains. I can probably look up exact information if needed (it's so messed up that it would take me a long time just to pull up information), but from what I remember, it's an AMD 64 3200+ processor (Athalon I believe), 1GB RAM, ATI 128 something :confused: video card, soltek motherboard, ... to begin with I had an HP CD-only drive (no DVD reading even) and a cheapo DVD reader/burner, on which the burning feature didn't work but the reader did. I also had 2 120GB SATA hard drives, which we tried to set up as RAID 0 but it didn't work... so we just partitioned one of the drives for XP and left the other blank for the time being, as I eventually wanted something else on it.

Everything worked fine... then I got another friend to come over and load SuSE on the other drive with dual-boot. The dual-boot set up was fine, but there seemed to be a problem with my graphics drivers for suse, because once I selected that option, it scrolled through a list of what was loading and then just... stopped... or the screen went blank. We tried a few things (I did not have graphics drivers on a floppy disc, only on a USB drive, which is what we used when we set up XP), but due to time and life constraints we gave up and I just used XP and pretended not to be bothered that half of my hard drive space was now useless :(

Okay, now in recent times (2 years later). My DH bought me a new DVD burner (Lite-ON) this past Christmas. I installed it fine, but when I went to install the software, it had to uninstall a bunch of things (DirectX was one, and now I can't watch any videos :mad: ). And then the CD had a fatal error. All of a sudden I have TWO completely non-working drives. They have power, and when they open and close my computer lags, but there is nothing on my PC that recognizes their existence. I have even tried pulling up driver software for the Lite-ON but was told that yes, indeed, the HP drive still existed... but no Lite-on drive was installed and therefore I could not load the application. (On an unrelated note, I have also been having other problems with the computer recently... probably due to a virus... as I shamefully have had no virus protection since Norton expired in 2006 and my PC stayed at a friend's house for awhile who is not computer-savvy and does not exactly go to the most innocent of internet sites).

Anyway, I burned ubuntu onto a DVD first, hoping that the Lite-ON would read it when I just hard booted. It didn't. So I went and bought regular blank CD's and put it in the HP drive. It got to the point in loading where it stopped and said: "Boot from CD: HP bla bla, ISOLINUX something something, 3.3something, Debian something" and just a flashing cursor. I waited several minutes for something to happen, but nothing did. Pressed Enter, nothing happened. Waited about 20 more minutes (walked away), came back, no change... rebooted, and now it stops at "Boot from CD:" but says nothing and does nothing more.

Where do I go from here, other than burning my desktop PC? You know, literally...

Ideally I'd like XP and Ubuntu on it, but personally I'd be fine not having XP on it at all (I have an XP upgrade disc but I lost my "previous full version" that it needs, so I can't load it anyway). I'd like SuSE gone because it's useless... how about 240GB of just ubuntu? Or hey, I'd be happy just with a working OS on that computer right now!!! :lolflag:

I read the "Complete guide to installing" but its step 1 seems to be 30 minutes away from where I am now, KWIM?

Any help is VERY much appreciated. I am not a computer genius by any means at all... I took Basic, VB, and C++ in high school, but it's been a few years... these days I'm thrilled if my cheapo router works and I can get online.



If you got through my novel... wow!! And, thank you so much in advance.

---

### Post by jken146 on 2008-03-17
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) has lots of methods for installing Ubuntu.  Installation Without a CD might be the way to go for you.

---

### Post by Victormd on 2008-03-17
> **sunnymw said:**
> Okay, now in recent times (2 years later). My DH bought me a new DVD burner (Lite-ON) this past Christmas. I installed it fine, but when I went to install the software, it had to uninstall a bunch of things (DirectX was one, and now I can't watch any videos :mad: ). And then the CD had a fatal error. All of a sudden I have TWO completely non-working drives. They have power, and when they open and close my computer lags, but there is nothing on my PC that recognizes their existence. I have even tried pulling up driver software for the Lite-ON but was told that yes, indeed, the HP drive still existed... but no Lite-on drive was installed and therefore I could not load the application. (On an unrelated note, I have also been having other problems with the computer recently... probably due to a virus... as I shamefully have had no virus protection since Norton expired in 2006 and my PC stayed at a friend's house for awhile who is not computer-savvy and does not exactly go to the most innocent of internet sites).

Well, looks like you overlooked the jumpers in your drives. Seems like they're not set properly. Both should be set to "Cable Select" if they're connected through the same ribbon cable, or one needs to be set as "Master" and the other as "Slave" (I prefer this last alternative). These are set on the back of the drive so you'll need to pull them out and check a small jumper (located usually between the power and the ribbon cable)... Do this, then try the install...

---

### Post by JoshuaRL on 2008-03-17
Sounds like the CD may be corrupted.  Could you try burning the ISO to another disk, and this time with the lowest speed possible?  That might just fix your problem.

---

### Post by sunnymw on 2008-03-17
Thank you so much for your quick replies! I will try re-burning it in the morning, and if that does not work will try the non-CD versions...

As far as the drives go... there are only 2 sets of cables attached to the back of each one... and when I try to go into setup mode it has the HP set as master, but the 2nd one says that nothing is there at all, period... Maybe the entire drive itself is just a piece? It has power, though... and FWIW, both the HP and the old drive had issues playing CDs, games would play just fine, CDs would burn just fine, but listening to audio directly from CD sounded like it was skipping the entire way through... so maybe it's that entire cable...

Anyway, thanks so much and I will come back tomorrow and let you guys know how it went... or didn't ;)

---

### Post by Victormd on 2008-03-17
Try unpluging the second drive and see what happens... If they're not setup right (this is a hardware setup) then they'll still be recognized but you will have problems using them...

---

