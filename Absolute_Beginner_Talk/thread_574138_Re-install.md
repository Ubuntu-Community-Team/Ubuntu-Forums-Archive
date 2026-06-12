---
title: "Re-install"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by ces1939 on 2007-10-12
:popcorn: Hi,
I now have a new motherboard, one 80Gb SATA HDD, one 250Gb SATA HDD.
I have Win XP on the 80 after having to use the 'fixmbr' with XP disk.
Now I want to put Ubuntu CE on the 250 using half, and PCLOS on the second half. 
Can I do that so everything works the way it should?
Simple, easy to understand step by step instructions will be so appreciated.
I have learned a lot, trial and error method, but still consider mysel a newbee.
I really am thankful for this forum, and even if I get frustrated and start from scratch, it just teaches me two lessons: patience, and persistence. 
You may not even believe in God, but I do and I thank Him He has held me in check when I feel like throwing up my hands and just quitting.
68 is probably not the best age to begin learning, but you can teach an old dog new tricks.
So, Thanks!!!! for your help.

---

### Post by az on 2007-10-12
You are not describing a re-install, but a dual (or triple) boot.

I cannot speak for PCLOS, but Ubuntu will detect your windows installation (and any other OS installed - including other linux distros) and allow you to install UBuntu alongside it.  Once it's done, it will create and install a bootloader that will allow you to pick what OS you want when you boot up your computer.

I know the Ubuntu installer will properly set up your bootloader.  Probably, the easiest way to proceed is to install PCLOS and use half of the 250 GB hard disk.  Leave the rest as Free Space.  When you then boot the Ubuntu installer, it will see that free space and you will have the option of installing Ubuntu there.  The bootloader (as I mentioned) will be installed and all three OSes will be on it.

---

### Post by ces1939 on 2007-10-12
:confused: I did everything as suggested: 
Had XP already on 80Gb
Re-installed PCLOS to 1/2 250Gb
Installed Ubuntu to seciond 1/2.
Ubuntu did set the bootloader.
I get a splash with Linux (PCLOS) and Windows only.
No Ubuntu!
Any suggestions?

---

### Post by ces1939 on 2007-10-13
Sadly, I had to abandon the efforts to put Ubuntu CE on with PCLOS and Win XP. 
I tried PCLOS on one HD and XP on a second HD, then Ubuntu on the larger PCLOS drive.  
It set the bootloader which left me with nothing available but Ubuntu. 
I removed Ubuntu, re-set the MBR on XP and re-installed PCLOS. 
They worked fine together. 
I tried to re-install Ubuntu, following the advice to choose Advance and choose which should be bootloader. 
I chose the XP drive, that caused error 17, and nothing booted. 
I put PCLOS disk in and deleted the entire disk, re-partitioned and let PCLOS take over the entire drive. 
It asked which drive to make bootloader. 
I again chose XP drive and they both work fine.
I really like the Ubuntu CE, but I guess I just don't know enough to get it to work, and I can't get any help I can understand as a newbee from this forum.
So, until I learn enough to do it by myself, I will keep what I have and let someone else have the headaches.
Bye!

---

### Post by ryanVickers on 2007-10-13
I have 2 Ubuntu's on 1 drive along with windows, and on another drive Mac OS X, and they all triple boot fine - super easy, no problems!  I just installed windows, then Ubuntu, then Mac and added a grub entry for mac ;)

---

