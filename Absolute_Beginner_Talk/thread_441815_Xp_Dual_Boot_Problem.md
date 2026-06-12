---
title: "Xp Dual Boot Problem"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by thiernod on 2007-05-12
Hello Team,
I installed ubuntu a couple of months ago. Great OS. When I powered up my PC, I was given a choice of booting up either Ubuntu,or Windows XP.
Lately however, anytime I press the power button XP loads automatically. No option to choose Ubuntu.
I looked evrywhere,I cannot find it. My question to all of you is: Where the heck is Ubuntu in my HDD?
How do I get it back to where I have the option to choose the OS I want to use?????????:(

---

### Post by FuturePast on 2007-05-13
It's possible that Windows has overwritten the Ubuntu bootloader (called Grub).

You should boot up from your Ubuntu install CD and there should be an option to recover your Ubuntu installation.

---

### Post by bobplano on 2007-05-13
first of all (however unlikely this is) check and see if ubuntu is still there. just see if your windows is taking up the whole HDD. if it works out that windows is the size it was when ubuntu could be booted to then you move on to the next step. it sounds like you may have restored the windows mbr so you'll probably need to  install grub again. i'm not sure how to do this but try supergrub (a live cd).

---

### Post by microsoft92sucks on 2007-05-13
i dont know how to make it like it was but what i would do is put Grub on your computer and add windows xp onto grub just look up a how to on google

---

### Post by thiernod on 2007-05-13
Thank you guys for your prompt reply.I have checked,Bobplano is right, my laptop has a total HDD size of 30Gigs. However it is only showing 14 Gigs as "C". I went onto Partition Magic and it is showing:

PARTITION                    TYPE
-Local Disk (C:)             NTFS
-Local Disk (*.)             Linux Ext3
-(*)                               Extended
-SWAPSPACE2 (*.)      Linux Swap

Which tells me that Ubuntu is still in my PC somewhere. But How to get to it?????????

---

### Post by FuturePast on 2007-05-13
> **FuturePast said:**
> You should boot up from your Ubuntu install CD and there should be an option to recover your Ubuntu installation.

??

---

### Post by mikewhatever on 2007-05-13
Have you reinstalled Windows or played with Windows installation CD? Do you see any notion of GRUB at all? It looks like,for some reason, Windows boot loader got back to your MBR instead of GRUB, so try [GRUB recovering.]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

---

