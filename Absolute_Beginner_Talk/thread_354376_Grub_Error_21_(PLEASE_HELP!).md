---
title: "Grub Error 21 (PLEASE HELP!)"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Ub_newb on 2007-02-05
I am a total newb at anything Linux, but I decided to finally take the plunge and install Ubuntu (perhaps not the smartest thing I've ever done)!

After going through the install process for Ubuntu 6.06 using the live CD, I got the message "Grub is loading please wait ... Error 21."  

I have been going through these forums and many others.  Most suggest editing a file in the /boot/grub.  However, in my /boot there is no grub!  There is just a few files named abi, config, system.map, etc... Do I need to install Grub somehow?  Wasn't this supposed to already be done at the end of the install process?

My setup is this.  I am attempting to dual boot with WinXP Home (Dell BIOS).  I have an 80 gig hd that is my main XP drive.  I recently added a 200 Gig drive, 145 of which is NTFS, 5 is FAT32, 2 was supposed to be swap, and 45 was supposed to be root.  So I have seen many people ask for a fdisk -l, and mine looks like this:

Disk /dev/hda: 80.0 GB

Device          Boot      Start          End             Blocks             Id             System
/dev/hda1                    1              4                 32098+          de             Dell Utility
/dev/hda2        *          5              9725        78083939+        7               HPFS/NTFS

Disk /dev/hdb: 203.9 GB

Device          Boot      Start          End             Blocks             Id             System
/dev/hdb1                      1          18098        145372153+        7              HPFS/NTFS
/dev/hdb2                 18099        18751            5245222+       b               W95 FAT32
/dev/hdb3                 18752        19012            2096482+      82      Linux swap/Solaris
/dev/hdb4                 19013        24792           46427850+     83               Linux


Oh and also I think that I have hda as master and hdb as a slave.  If you have any advice, please try to dumb it down as much as possible, as I am very new at Linux.  

Any help would be GREATLY appreciated.  I was really excited to try Ubuntu, but I am getting really discouraged after spending the last several hours trying to figure this out.


Thanks in advance!
Dave

---

### Post by Maestro23 on 2007-02-05
You should have a menu.lst file under /boot/grub.  Open a terminal and type the following command and paste the results here so someone can begin to help you.

#cat /boot/grub/menu.lst

---

### Post by Ub_newb on 2007-02-05
After much frustration, I solved the problem.  I had to go into the BIOS settings and change my hard drive to auto.  

... so simple, and I feel silly.

Sorry for the wasted space, but maybe this will help somebody else!

---

### Post by Maestro23 on 2007-02-05
> **Ub_newb said:**
> After much frustration, I solved the problem.  I had to go into the BIOS settings and change my hard drive to auto.  

... so simple, and I feel silly.

Sorry for the wasted space, but maybe this will help somebody else!

Don't feel silly, you corrected the problem on your own...and you learned something.:)

---

