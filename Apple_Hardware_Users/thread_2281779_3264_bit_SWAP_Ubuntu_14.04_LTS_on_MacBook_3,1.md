---
title: "32/64 bit? SWAP? Ubuntu 14.04 LTS on MacBook 3,1"
date: 2015-06-09
forum: Apple Hardware Users
---

### Post by cristina6 on 2015-06-09
Scenario:

I am a Linux newbie and I will be installing Ubuntu for the first time ever this weekend on my white MacBook 3,1 as a part of a triple boot rEFIT setup with Snow Leopard OSX, Windows 7, and Ubuntu.

Partition Goals:
Snow Leopard = bare bones/minimal install 5 - 10 GB, I will never use it
Win 7 = 80 GB, I use this for work: MS Word, excel, email, and skype
Ubuntu = 20 GB, I use this for personal email, web browsing, and to learn how to use Ubuntu!

Questions:
1. Do I choose the 32 bit or 64 bit version of Ubuntu?
2. Do I choose to make an extra SWAP partition for Ubuntu? Or do I choose to use a savefile instead?

Hardware Specs:

MacBook 3,1 (Late 2007)
Intel Core 2 Duo 2.0 GHz
4.0 GB RAM
120 GB Hard Drive, Serial ATA 5400 rpm
Intel GMA X3100 144 MB RAM (Graphics)
DVD+-RW
Integrated Airport Extreme 802.11a/b/g/n (draft-n enabled)
Gigabit Ethernet
Bluetooth 2.0 + EDR
2x USB 2.0
1x Firewire 400
1x Optical digital / analog audio line-in
1x Optical digital / analog audio line-out
iSight Camera
mini DVI

Software Specs:

Snow Leopard 10.6.8 OSx
Windows 7.1, Home Premium Edition, 32-bit
Ubuntu Trusty Tahr 14.04 LTS, 32/64 bit?

I am familiar with using computers, but I am beginner when it comes to hardware, drivers, software, and programming.. Thanks, meow!

---

### Post by QIII on 2015-06-09
Moved to Apple Hardware Users.

I think you're more likely to get specialized help here.

Cheers!

---

### Post by Bucky Ball on 2015-06-09
Welcome. Core 2 Duo is 64bit from what I can find so 64bit. 

> The Core 2 brand refers to a range of Intel's consumer 64-bit dual-core and MCM quad-core CPUs with the x86-64 instruction set, and based on the Intel Core microarchitecture, which derived from the 32-bit dual-core Yonah laptop processor.

From the comprehensive history of these processors in the last answer [here]("https://au.answers.yahoo.com/question/index?qid=20071223112941AA6Ahr4&p=Intel%20Core%202%20Duo%202.0%20GHz"). 

I would think a /swap would be needed for Ubuntu, but a Mac aficionado may know better as to whether a savefile can be used. I have a feeling this is like the Win pagefile, which is like a /swap partition, but not the same and Ubuntu doesn't use one. I'd probably go ahead with a 2Gb /swap (make it 4Gb if you intend to hibernate). Good luck and hope that is of some help.

---

### Post by cristina6 on 2015-06-09
Thanks QIII and Bucky! I will probably try the 64 bit version with a 4 GB swap partition. Fingers and toes crossed that this works! :)

---

### Post by Bucky Ball on 2015-06-09
Good luck with it and let us know.

---

### Post by typo-joe on 2015-06-16
64 bit.  I installed a 32 bit desktop version of Ubuntu on a MacbookPro1,1 last week with a dual boot to Snow Leopard 10.6.8.  I don't know the exacts but I read it has something to do with your ram.  The MBP1,1 maxes out at 2gb.

It was only on there for a few days before I wiped it clean and installed a single boot 32 bit server version of ubuntu.

The dual boot was done with rEFIt and the way I did it was to reduce the size of the mac os partition and left the remaining space as free space. When I installed Ubuntu (via usb) it found and formatted the free space accordingly.  Was it the right way? IDK, but it worked.

Look forward to hearing how yours went.

---

### Post by cristina6 on 2015-06-20
Hi All,

I installed Ubuntu 14.04.2 LTS 64-bit version on the MacBook 3,1 and it works like a charm! Thanks for the support! Update* Also, Ubuntu automatically created a 4GB swap partition for me when I installed it with the easy/standard/typical/automatic installation mode.

---

### Post by Bucky Ball on 2015-06-20
Great news! Please see second link in my signature. Enjoy! :)

---

