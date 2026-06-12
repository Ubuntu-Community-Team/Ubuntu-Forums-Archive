---
title: "Help with installation"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by knutsack on 2006-08-29
Okay I am a complete noob when it comes to linux and partitions and things like that...
I am trying to set up a dual boot system with Windows XP and Ubuntu, and I get through all of the steps but when it gets to setting up partitions the first option continually tells me that it Failed to create enough space for installation... No matter how much or how little space I allow for the new partition size.

Again I have no clue how to set up partitions manually, so that is really not an option unless soemone describes to me exactly what to do with it.

Any help would be GREATLY appreciated...

Thankyou

---

### Post by skymt on 2006-08-29
Do you have Windows XP installed currently? Do you want to keep your current Windows install? How much free space do you have on your drive right now?

---

### Post by Jagot on 2006-08-29
Depending on whether you're using the alternate or desktop install disk you may want to have a look at these links:

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by toasted on 2006-08-29
Before you go any farther, do you have all your information backed up from Windows? There is always a chance of losing it.... fyi

---

### Post by knutsack on 2006-08-29
I am already running XP... I have backed up all of my files... and I have about 60GB of room left on my harddrive...

---

### Post by knutsack on 2006-08-29
and i do want to keep xp on my system

---

### Post by confused57 on 2006-08-29
You might try defragging your Windows partition(maybe a couple of times), before trying to resize.
   If you still have problems resizing, you may want to try gparted(30mb download) to resize your ntfs partition:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

I've read the newer versions of gparted are better at resizing ntfs partitions than the Dapper Live CD gparted...?

---

### Post by murkydurky on 2006-08-29
i'm a noob myself on these things..what i did was i have a fairly fresh Windows XP pro (XP2) installed on a 120 GB IDE hard drive. I downloaded the ubuntu live cd iso, burned it, played around with the cd version for a few days, then clicke d on the install button on the desktop. when it asked me about the partitions, i choose the option that said something like "largest contiguous free space", then i adjusted the slider to some where near 50 or 60 GB, and clicked forward. about 20 minutes (maybe 30) it said it needed to restart and eject the cd, i clicked ok and when it rebooted i had the option of windows xp, ubuntu, ubuntu safe mode (or the equivalant). I may have been blessed with a REAL easy install, but i've had no problems with ubuntu at all. I can even watch DVD's (the ones i actually purchased!).

My system specs :

AMD 2200+
MSI motherboard
1.5 GB RAM
NVidia 5600
120GB Seagate IDE
DVD-ROM /Burner
CD-ROM

---

### Post by pranab_cool on 2006-08-29
hi.
what i did was created a free space in my hard disc. actually i had 10 GB of a partition free. but i did not want to use it all for ubuntu. so i created two parts of it one 5 gb and the other left as free.
i used the free space for ubuntu. i used the option "use the largest free space" to install. i had no probs doing this. intitially when i tried to install manually by setting the size for root n swap, i was unsuccessful. but this method worked.
hope this works for you too.
enjoy!!!

---

### Post by knutsack on 2006-08-30
Thank you everyone...

I figured out that there was a set of un-movable files in the way of creating a new partition... It was the set of files windows uses for hibernation, and after I turned off hibernation, that dissapeared. After defragmenting a couple of times Ubuntu installed with no problems...

---

