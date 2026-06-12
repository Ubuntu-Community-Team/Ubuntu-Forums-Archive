---
title: "removing ubuntu"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by bellzii on 2008-01-07
i wanna remove ubuntu from my brothers laptop , as ive been using it on his laptop a year now, his laptop has windows vista also installeded.
thanks 4 ur time

---

### Post by snickers295 on 2008-01-07
reinstall the vista loader with [this]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD") first.
use [this]("http://gparted.sourceforge.net/") livecd to remove the Ubuntu partition  and the swap partition after you reinstall the vista loader.

---

### Post by bellzii on 2008-01-08
Ive done a silly thing, used a livecd removed the partition that had ubuntu and formated it , before using the vista loader program , and now im stuck with the grub page that says error 22, can some1 help?

---

### Post by Joeb454 on 2008-01-08
Do you have a Vista install disc anywhere at all?

---

### Post by bellzii on 2008-01-08
ya

---

### Post by Joeb454 on 2008-01-08
If you put that in, you should be able to choose the repair option, and then choose to reinstall the MBR (I'm at University currently...so not got my Vista disc on me).

I know Vista lets you reinstall the MBR which means it should be able to boot...there's even an auto-repair function on there, try that and let me know :)

---

### Post by Glugglug on 2008-01-08
I did this only 2 days ago only difference is I couldn't get gparted to work so I  used windows disk manager to try to free up some space because the Ubuntu automatic partitioner was only giving me 11 GB to install Ubuntu and there was about 18 gb  free space so I deleted a partition that wasn't active and left the 1st partition with Windows on and another partition that was active and also left the swap partition in place . 

When I rebooted I got the error 22  so I put the Gparted disk in and  went down the list to where it said boot 1st partition  and it booted up Windows so I was relieved to know I hadn't lost XP  there was still a way of booting  I then reinstalled feisty 7.04 but this time I partitioned it manually after alot of messing around it kept telling me I had not specified a mount point I tried all different ways untill I just put " / "  and it worked and now I have the Grub screen back . 

  But you didn't want Ubuntu installed but maybe if you reinstalled Ubuntu and manualy resize the partition and just use the minimum space I think its 2gb and a swap partition just so you can get the Grub back .  or is there another way.

---

