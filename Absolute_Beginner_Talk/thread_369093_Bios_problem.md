---
title: "Bios problem"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by al1b1 on 2007-02-24
Hi i got a new hdd for my 160GB for my bday and im tryin to install ubuntu on it. 
The installation goes fine however when i boot into my 160gb drive it comes up with error message Disk boot failure, please insert system disk and hit enter. i have put the hard drive in another computer and ubuntu worked fine. Any help thanks 

Nick

---

### Post by arochester on 2007-02-24
Does your BIOS tell the computer to boot from the CD first? It should now tell the computer to boot from Hard Drive first. The error message could be because it finds no disk in the CD-ROM.

---

### Post by al1b1 on 2007-02-24
Tried that

---

### Post by al1b1 on 2007-02-24
Can anybody help please

---

### Post by alienexplorers on 2007-02-24
Does the BIOS recognize the HD correctly?

---

### Post by al1b1 on 2007-02-24
It recoginzes the name and its size so i presume so. However the bios says the size is 149GB whilst its supposed to be 160GB u think my bios cant handle the capacity?

---

### Post by al1b1 on 2007-02-24
anybody out there have any ideas??

---

### Post by igknighted on 2007-02-24
Dude, its (a) a weekend and (b) the middle of the night in the US where a large number of the forum member are... just be patient.  A 160GB disk will be recognized as 149 GB, that's the size you actually get after the file system takes up all its space.

As for your specific problem, It sounds as if there is no bootloader installed on that HD.  Did you already install Ubuntu on that disk?  Did you make sure you installed the bootloader to that disk?  If you have already done these things, can you boot the live CD and tell me the output of "fdisk -l"?

---

### Post by funchords on 2007-02-24
> **al1b1 said:**
> Hi i got a new hdd for my 160GB for my bday and im tryin to install ubuntu on it. 
The installation goes fine however when i boot into my 160gb drive it comes up with error message Disk boot failure, please insert system disk and hit enter. i have put the hard drive in another computer and ubuntu worked fine. 

That's fishy -- did you install Ubuntu while _this_ HDD was in _this_ computer?  Or was it in another computer when you performed the install?  If it was in another computer when you performed the installation, this is likely related to your problem.

Equally likely are jumper settings.  Most new drives use "Cable Select" as the default out-of-the-box jumper setting, but not all systems behave well using CS.  You might fare better by making the drive an explicit Master.  Some BIOS lets you swap Master and Slave in the BIOS.  Look for that setting.

---

### Post by klein de usa on 2007-02-24
hi 
are you trying to do? boot xp and ubuntu on the same hard drive ? 
sounds like maybe a grub problem ?
what ver. of ubuntu are you useing? 
 it is my experance that switching hdd with installed operating systems between two computers in less they are exacly the same won't work , the only os that i ever saw that would rebuild it's self was win98se and that was when i switched hdd in two dell optiplex

---

### Post by al1b1 on 2007-03-10
Its resolved the hard drive had a couple of pins broken that were giving me an interminet signal. So i could detect but thats as far as i can go. Sent it to Samsung and im hoping for a replacement

---

