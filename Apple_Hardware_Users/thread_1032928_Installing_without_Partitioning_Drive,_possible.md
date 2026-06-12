---
title: "Installing without Partitioning Drive, possible?"
date: 2009-01-06
forum: Apple Hardware Users
---

### Post by ladydeathstrike on 2009-01-06
Hello.

Alright, I have ubuntu 8.04LTS image burned correctly, on a cd.

I've got a powerbook g4 (powerpc) with osX.  

I've been trying to install ubuntu, but once it gets to a loading screen, the screen on my mac turns grey, then bright grey,then even brighter grey.  Nothing really happens.

i have not been able to partition my drive because I don't have the software or the money to obtain the software.  I don't even want to run any part of OSX anymore either.

Can anyone help me out?

---

### Post by Zeroberry on 2009-01-06
Wubi might be your best option for installing without partitioning drive. I'm not really sure about your problem though. Maybe Mac HQ registered that you were trying to switch from OS X and interferred!

Seriously though, the install cd will partition for you. Try burning the alternate install or another version.

---

### Post by ladydeathstrike on 2009-01-06
Wubi appears to only work for windows, not Mac.

---

### Post by mkvnmtr on 2009-01-06
If I am understanding correctly you have not been able to boot the disk. Is that correct? You have burned the powerpc live disk and burned it in Disk Utility on your mac? First we need to know how much ram you have on your machine.My G4 came with 256MB of ram and that is not enough to install from the live disk. Before I installed I added 1Gb and that is more than enough. It wasn't very expensive even here in Mexico. If you are short of ram you should still be able to get an install with the alt disk but it will be better if you can boot the live disk and play around with it before you try to install.

---

### Post by Zeroberry on 2009-01-06
The alternate install doesn't get half as much love as it should. It's true you should try an OS out before you switch to it but if you've already got your heart set that doesn't matter =)

---

### Post by ladydeathstrike on 2009-01-06
Alright.

1GB ram, 1GHZ.

Unfortunetly, did not burn on my laptop, I burned it on a pc, because I did not have any more cd-r, this laptop only has a cd-r.  the pc had a dvd-r, and i had an excess of dvd-rs.  

I will re-try this install when I get more cd-r.


I've already installed ubuntu on an extremely old toshiba laptop for my mom.  I wanted to put ubuntu on this powerbook because I prefer the ubuntu operating system, and I don't want to take my mom's toshiba.

---

### Post by pxwpxw on 2009-01-07
> **ladydeathstrike said:**
> Alright.

1GB ram, 1GHZ.

Unfortunetly, did not burn on my laptop, I burned it on a pc, because I did not have any more cd-r, this laptop only has a cd-r.  the pc had a dvd-r, and i had an excess of dvd-rs.  

I will re-try this install when I get more cd-r.


I've already installed ubuntu on an extremely old toshiba laptop for my mom.  I wanted to put ubuntu on this powerbook because I prefer the ubuntu operating system, and I don't want to take my mom's toshiba.

Booting Ubuntu 804 desktop on an Ibook G4, I find it needs selecting the

<TAB> option
 
boot: live-nospalsh

then about 2 minutes to get to the desktop.

Otherwise it just hangs.

---

### Post by ladydeathstrike on 2009-01-07
> **pxwpxw said:**
> Booting Ubuntu 804 desktop on an Ibook G4, I find it needs selecting the

<TAB> option
 
boot: live-nospalsh

then about 2 minutes to get to the desktop.

Otherwise it just hangs.

Thank you, it worked!  :) Now I just gotta set up the wireless. Thank you.

---

### Post by joka. on 2009-01-07
Wait... unless I'm missing a part... you want to install Ubuntu but don't have anything to partition the drive with? You're using OS X... so doesn't it come with Bootcamp or DiskUtility [or can download for free off the Apple website]?

From what I remembered, I was able to install Ubuntu 8.04 without partitioning my drive, but I was running Windows Vista and when I rebooted it only ran Ubuntu... I kinda messed up my drive a little and had to use the backup disc to wipe it clean so I can use Windows again. I don't remember 8.04 having anything that helps you partition hard drives [if I'm not mistaken].

I'm really a newb at Ubuntu, so if I didn't get what you were trying to say, wrong in some part, or messed up somewhere don't blame me.

---

### Post by sanil on 2009-01-07
thanks for the information and post. many many thanks. Windows Vista and when I rebooted it only ran Ubuntu... I kinda messed up my drive a little and had to use the backup disc to wipe it clean so I can use Windows again. I don't remember 8.04 having anything that helps you partition hard drives [if I'm not mistaken].

---

### Post by mkvnmtr on 2009-01-07
If yuou have booted the disk then you are set to go. You can resize the Mac partition with Disk Utility on the mac install disk. Just leave the part of the disk you want for Ubuntu as free space. If you don't have the mac disk you can use the partition editor on the live disk before you install. Then when you install and get to the partition part choose to install in the largest free space. The installer will form your Ubuntu, swap and boot partitions with no more input from you. This will be the easiest way for a first time install. After that it is just waiting for the install to finish and rebooting and downloading the updates.

---

