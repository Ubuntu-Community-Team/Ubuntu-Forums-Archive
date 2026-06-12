---
title: "Problems booting live cd's and dvd's"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by AdamEW on 2007-04-07
Hi there, I recently recieved a new dvd-rw drive (pioneer dvr-112D) for my pc, and I thought I would try some live linux cd's. Now I had Kubuntu 64bit AMD, installed before, but I have formatted recently. Thing is I cant seem to boot any live disks now, Ubuntu 64bit, kubuntu 64 bit give me the error
"/bin/sh: can't access tty; job control turned off"

Ive searched for cures to this but anything said hasnt helped at all, 32 bit versions of ubuntu and kubuntu become corrupted at the loading screen. I thought I would try opensuse live dvd as well, just to make sure it wasnt a ubuntu problem and this is what I got :
[http://img143.imageshack.us/img143/7276/limprd5.jpg](http://img143.imageshack.us/img143/7276/limprd5.jpg)
so, as you can see Im having some trouble, the only thing I can think to be causing the problems is the new dvd-rw drive as all the disks boot on my brothers computer. Any help would be really appreciated, thanks.

My system spec:

AMD Athlon 64 3200+
Asus a8n-e
Sapphire X800gto
1gb corsair value ram
Western Digital Caviar 200gb sata hdd
Pioneer DVR-112D
Creative Audigy 4

Think thats all.

---

### Post by wpshooter on 2007-04-07
Adam:

I have been getting this same error when attempting to install Feisty BETA versions to one of my computers.  In all of my inquiries about this error, I am beginning like you to believe that maybe this is somehow related to the CD-Rom drive.

I am going to check to see if there is possibly a firmware update for my Plextor CD-RW drive and see if this might cure the problem.  Why don't you do the same and write back if you discover that bringing the firmware up to the lastest version might cure your problem.

Thanks.

---

### Post by AdamEW on 2007-04-07
hi there, yeah I already have the latest firmware for my drive, could be an unaddressed issue with the writer though, perhaps.

---

### Post by wpshooter on 2007-04-07
Yes, I just checked mine and it is on the latest version 1.06 also.

I sure wish someone could come up with a solution to this problem. 

According to what I read elsewhere on here maybe it has now be corrected because I think that the last version of Feisty that I downloaded and burned was 03-22-2007 and I think someone said that perhaps it had been fixed on the 03-31-2007 version.

Good luck.

---

### Post by AdamEW on 2007-04-07
I'm pretty sure I have the  latest version of edgy, should this be a problem with my dvd-rw is there any way I can solve it? or is this not related to my new drive

---

### Post by revoltism on 2007-04-07
I think it has with the kernel update to 2.6.20-12 and JMicron. Problably we have to wait till they have worked out a fix.

read about it here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964")

I gonna test the latest release 2007-04-07 witch has the 2.6.20-14 kernel.. it maybe will work.

---

