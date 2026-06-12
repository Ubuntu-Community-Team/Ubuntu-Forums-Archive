---
title: "[SOLVED] Dual HDD question."
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by jso2897 on 2007-09-02
I am getting ready to install Ubuntu as a dual boot on a WinXP box. I am going to install it on a second hard drive, rather than a partition. The main hard drive is SATA, but the seciond one I installed is IDE, and I installed it a the single drive on the spare IDE bridge on the MB.
 Now, when I boot up, two things. First, Windows sees all the USB sockets as disks, until I shut them off. Second, it does does NOT see the hard drive as a drive with a letter addres in My Computer. It shows as a working drive in the hardware manager, and in setup, the BIOS also sees it and identifies it properly. 
Does anybody have any idea what the problem is?

---

### Post by jso2897 on 2007-09-02
I have switched it to the slave coonector on the primary IDE cable, and now it shows up in the second channel in the BIOS setup instead of the first, but nothing else has changed. Anybody got any ideas?:confused:

---

### Post by mikewhatever on 2007-09-02
Windows can't see ext3 filesystem, it's the same with one HDD. You'll need to install fs-driver if you want that kind of access. [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jso2897 on 2007-09-02
Stupidly, i left out an important detail. This is a brand new drive, with nothing on it - not even formatted. Should I just go ahead and boot up Fiesty live, and see if it will install Ubuntu on the second drive and let GRUB figger it out? Or would that be a mistake? According to both the Bios setup and Windows hardware manger, the drive is there and working fine.

---

### Post by Duck2006 on 2007-09-02
> **jso2897 said:**
> Stupidly, i left out an important detail. This is a brand new drive, with nothing on it - not even formatted. Should I just go ahead and boot up Fiesty live, and see if it will install Ubuntu on the second drive and let GRUB figger it out? Or would that be a mistake? According to both the Bios setup and Windows hardware manger, the drive is there and working fine.

Just run the live CD and click the install and let ubuntu installer install on the new drive,
or i would do a manual install
20Gb for /  root partition
1Gb for swap partition
and the rest for home partition

so if you have to reinstall ubuntu you will not lose your files in your home partition

---

### Post by jso2897 on 2007-09-02
Thanks, man. I'll probably just let GRUB do it - I won't have any important data on that drive anyway - this whole PC is for play, not work. I do my important  stuff on an all Ubuntu box. I don't want anything I hav esecurity concerns about on a box with Winodws on it.
Thanks for the help!:KS

---

### Post by pcrussell50 on 2007-09-02
> **jso2897 said:**
> Thanks, man. I'll probably just let GRUB do it - I won't have any important data on that drive anyway - this whole PC is for play, not work. I do my important  stuff on an all Ubuntu box. I don't want anything I hav esecurity concerns about on a box with Winodws on it.
Thanks for the help!:KS

Sooo.  The thread title says "solved".  How was it solved?

I've been debating starting a new thread on this myself.  I have almost the same goal you do.  I have a SATA drive with winXP, and an IDE drive that I would like to install feisty on.  So far, i have:

1]run the feisty live CD and installed it onto the IDE drive.  it goes like a normal install, but when i try to boot, i don't get that boot menu like i do when both drives are IDE...thus...it will only boot into windows.

then i tried:

2]run the feisty live CD and install ubuntu onto the SATA drive, [the one with windows on it].  i get as far as that slider bar that asks you how much disk space to give to ubuntu.  it give it 80Gb.  then it says it has to change the file system and that this may take a long time.  ok.  after about four hours, there is 0% progress.

I will postface this by saying that I have installed many dual boot xp/ubuntu setups on both single and dual IDE systems.  this SATA thing is new to me.  and SATA/RAID is even newer to me. I do NOT want to run a RAID.  i just want windows on the sata drive and ubuntu on the ide drive and to dual boot.

my board is:
ASUS Vintage-AH1 AMD Socket 939 AMD Athlon 64 FX / Athlon 64 

it uses what i THINK is fakeRAID to see the SATA drive.**      IOW, even to get winXP to see it, i need to install a driver that the ASUS gave me for that purpose during windows install.

** i barely know what this means, except that it works flawlessly under windows.  ULi comes up during windows boot as something that may be of interest

thanks and regards,
-peter

---

