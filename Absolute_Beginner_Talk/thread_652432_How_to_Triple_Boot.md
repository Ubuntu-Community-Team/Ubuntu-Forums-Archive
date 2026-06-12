---
title: "How to Triple Boot ?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by p0ker on 2007-12-28
I want to make a triple boot in my PC, WinXP, Vista64 and Ubuntu. I have two 320GB HDs, what i´ve planned was to install WinXP in the first HD, and Ubuntu and Vista64 on the second HD.

So what are steps to accomplish that, what would be the correct sequence to make that work?

I´m totally a linux newbie btw

---

### Post by ade90212 on 2007-12-28
I'm not 100% sure, but I would install XP, Vista and Ubuntu in that order. That way Ubuntu will install the Grub bootloader over the XP Master Boot Record, and Grub is easier to configure than the Windows equivalent.

---

### Post by spydon on 2007-12-28
I would install windows vista and XP first and then install ubuntu so you don't have to reconfigure GRUB. You can download the partion live cd gparted from [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) or you can just use the gparted that comes with the Ubuntu live cd. I've heard that vista is a bit tricky to dual-boot with so you might want to check that up first...

---

### Post by p0ker on 2007-12-28
i´ve already setup all the partitions in order to install linux (the root partition, swap, etc)  i was wondering if a special installation order was needed  :confused:

---

### Post by spydon on 2007-12-28
> **p0ker said:**
> i´ve already setup all the partitions in order to install linux (the root partition, swap, etc)  i was wondering if a special installation order was needed  :confused:

Install ubuntu last in all case...
Maybe vista first then XP and then ubuntu, I don't know if the order of vista and XP matters.

Edit: okay here I found a guide, seems like installing Vista first is best.
[http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php](http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php)

---

### Post by meierfra on 2007-12-28
Installation order should be XP, Vista, Ubuntu.
(Neither XP nor Vista will recognize Ubuntu, XP won't recognize Vista)

---

### Post by meierfra on 2007-12-28
> Edit: okay here I found a guide, seems like installing Vista first is best.
[http://lifehacker.com/software/ubunt...ntu-193474.php](http://lifehacker.com/software/ubunt...ntu-193474.php)

That guide assumes that XP is already installed.

---

### Post by Lostincyberspace on 2007-12-28
Make sure the boot partition for grub is in the first half of a disk (preferably the first) though since most computers wont recognize boot partitions past that point. I have no idea why just one of those thing that haven't been updated as technology advanced.

---

### Post by p0ker on 2007-12-28
> **Lostincyberspace said:**
> Make sure the boot partition for grub is in the first half of a disk (preferably the first) 


what do u mean by "first half of the disk" ?

btw, i intend to install Ubuntu, on the first partition of my second HD, and Vista on the third partition of my second HD

---

### Post by Lostincyberspace on 2007-12-28
I mean that if you hard drive is 100GB then /boot/grub needs to be before the 50GB mark otherwise it might not recognize it. But if you are going to install it at the beginning of the drive it should be fine. I had a problem with it when I first started multi booting.

---

### Post by buntunub on 2007-12-28
Vista.. LOL!!!!!

Well, since you seem to be quite the glutton for punishment, its really quite simple. You must install XP first. Vista seems to be a tad more advanced in the dual/triple boot area, so I expect that it wont be the disk hog that XP is when it comes to MBR. However, Microshaft being what it is, it will expect to come first on the drive, and so long as that is the case, your good to go with your Linux install. Put XP on sda/hda1, Vista on sda/hda2, and Linux however you like, probably extended partitions being the best way to go (so that you can make seperate /home, /var, etc partitions) without worrying about primary partition limits. Then you must ensure that both XP and Vista are detected and configured in GRUB on Ubuntu install (it should be). You will then boot from GRUB, and select XP or Vista from there. Funny thing is that most Linux distro's quite easily autodetect and configure GRUB on install for WIndows, but most have the worst time doing the same for other Linux installs.

---

### Post by p0ker on 2007-12-28
> **buntunub said:**
> Vista.. LOL!!!!!

Well, since you seem to be quite the glutton for punishment, its really quite simple. 

hehe, well i´m only using Vista to play games in DirectX 10 Mode,  

WinXP for life!!!! and then Ubuntu of course

---

