---
title: "Dual Boot Ubuntu/XP with Two Hard Drives"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by aarondesk on 2007-02-26
Hello all,

  I'm a linux/Ubuntu newbie. I have a Windows XP Media Edition PC that I want to dual-boot with Ubuntu and a second hard-drive. I really, really don't want to lose my XP data/programs (I have them backed up, but restoring is a pain). 
  
  I've done some research and present what I've found below. Please let me know if I'm dead-wrong on anything, and if you have any tips, suggestions, or ideas.
  
  1) Dual boot with Bios Control
  
  First I would remove the windows HD, then put in my new HD as master. I'd install Ubuntu on this HD, then put back the windows HD as master and the Ubuntu HD as slave.
 
 I can press F8 during boot-up to choose boot device, and could choose my OS this way.
 
 This method may not be as elegant as other methods, but I belive it would keep the windows HD and linux HD separate, so would have the least possibility of losing data. It also seems the simplest/easiest solution. 
 
 2) Set Ubuntu HD as master, Windows HD as slave
 
  In this method I would put the new HD into my computer, switch the HD cable around, and any jumper settings, and any bios settings. I would then drop in the LiveOS CD, install to the first HD (the new one). 
  
  I've read differing accounts on Grub and XP HDs. From what I've seen the install should auto-detect the second HD with XP, and after installation allow me to boot to this HD during bootup using Grub. I've also read that XP doesn't like to be slave, so this setup might not work. Any ideas? Is this feasible?
  
 3) Set Windows HD as master, Ubuntu HD as slave.
 
 Install new HD as slave. Insert CD. Choose second HD as HD to install to. I think that somewhere during the process I can choose to install a new boot loader to the Windows (master) HD. 
 
 This is the least favorable option. Basically from what I've gathered, I'd have to replace the NTLDR file on my windows HD to be able to boot to Ubuntu using the Windows MBR. It also looks tricky. I don't want to touch my windows HD if I can help it.
 
 
 Again, comments are welcome.
 
 Aaron

---

### Post by netkid91 on 2007-02-26
Yeah, you are doing more than you need.  if you tell Ubuntu to install on the second drive it will happily cooperate with XP.  It will just pop up a box asking you what to boot on every startup.
Edit: Didn't read your post.  No, it will not erase NTLDR!  NTLDR is located on your windows partition, the Windows MBR only transfers execution to NTLDR, like GRUB does when you select Windows.  You won't have to touch a thing on your Windows partition.

---

### Post by wireddad on 2007-02-26
I would think #3 would be the option.  Will have to try this and see.  Keep posting and let us know which one you tried.

---

### Post by punx45 on 2007-02-26
i have a dual boot setup.   Windows is on master, Ubuntu is on slave.   I can select primary boot up with BIOS. If Ubuntu is the primary boot device, and if it detected windows during the install, then grub will give you the option of which OS to boot, so then you really don't need to choose with BIOS anymore.  (windows partiton was never touched.)

i used [this guide]("http://psychocats.net/ubuntu/installing") for the install process.

---

### Post by aarondesk on 2007-02-26
> **netkid91 said:**
> Edit: Didn't read your post.  No, it will not erase NTLDR!  NTLDR is located on your windows partition, the Windows MBR only transfers execution to NTLDR, like GRUB does when you select Windows.  You won't have to touch a thing on your Windows partition.

Hmmm... so the NTLDR starts after the MBR tells it to, and GRUB starts also after the MBR tells it to. Is this right? 

Does the MBR automatically detect Ubuntu on the second drive, or does the install have to overwrite the MBR to update it that there are two OS's present?

Thanks,
Aaron

---

### Post by netkid91 on 2007-02-26
GRUB runs in the MBR.  It handles everything, it loads Ubuntu right off, or hands control over to NTLDR.  Simple enough.

---

### Post by aarondesk on 2007-02-26
> **netkid91 said:**
> GRUB runs in the MBR.  It handles everything, it loads Ubuntu right off, or hands control over to NTLDR.  Simple enough.

Ok, so GRUB is written to the MBR during install, but the install doesn't actually touch the windows partition, right? 

Maybe I'm being loose with my terminology about windows HD or partition. Doesn't the MBR reside at the beginning of my windows HD? So the install (option #3) would technically write on the windows HD?

---

### Post by nickdolan on 2007-02-26
the MBR is teh master boot Record it boot-staps the machine to read the disk. GRUB replaces the MBR and gives you a menu to choose what to boot. if you need to recover the windows MBR boot off your XP disk into recover / console mode and tyep 'mbr' & 'fix boot' (or something like that - can't remember the exact syntax)

you've worked out the options above - so choose one - cos it sounds like you already know the one you want.

(P.S> I always install Xp first then re-patition and install Linux on the same drive)

---

### Post by netkid91 on 2007-02-26
No, it doesn't touch your windows partition.  The MBR is the 512-byte block at the start of the DISK (not partition, which is where NTLDR is), that contains partition info (and bootloader, GRUB).

---

### Post by aarondesk on 2007-02-26
> **netkid91 said:**
> No, it doesn't touch your windows partition.  The MBR is the 512-byte block at the start of the DISK (not partition, which is where NTLDR is), that contains partition info (and bootloader, GRUB).

Thanks! That clears up my confusion.

---

### Post by confused57 on 2007-02-26
Here's another option:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Pelham123 on 2007-02-26
I have tried two methods, ie - 1) choosing via BIOS, 2)XP master Ubuntu slave.

I had always used 2) but I had a sticky moment with XP once (which forced me to perform a recovery install), this stuffed up GRUB/MBR which meant I couldn't access Ubuntu. So from then on I have always used BIOS to select my OS. I now prefer keeping them separate and I use small partitions on each to back up data from the other, as well as a FAT partition on one to share files.

Just my 0.2p from another newb

---

### Post by punx45 on 2007-02-27
Reading some of the newer replies it seems like there may be some confusion in details with Master Boot Records and GRUB etc.

On a dual drive install, grub is going to install on the MBR of whichever drive you are installing Ubuntu on.   Nothing is done with the Windows drive ever, aside from possibly stating its presence during the install for mounting purposes later (grub can also detect the presence of a windows partition on another disk during install).   

So with my system, If I choose the Windows drive (HDD0/master) in BIOS it boots directly to Windows.   If I choose the Ubuntu drive (HDD1/slave) in BIOS, it boots to GRUB, where I then have the choice between Linux and Windows.   

So, when doing a multi-drive install, even if you install GRUB, it will not write to or interfere with the MBR on the Windows drive.   Every disk has potential for an MBR.  You are not required to use the MBR on the Windows drive if you don't want to.

---

### Post by aarondesk on 2007-03-01
> **Pelham123 said:**
>  I use small partitions on each to back up data from the other, as well as a FAT partition on one to share files.

Just my 0.2p from another newb

A shared FAT partition to share files between XP and Ubuntu seems like  a great idea. Can you create a FAT partition during Ubuntu installation? If not, how could I create a FAT partition and Ubuntu partition on one HD? I imagine I could use windows to fdisk the partitions and format the HD, but could I use this HD/partitions for Ubuntu installation?

Honestly, I'm not even sure what format the partition/HD will be for the linux files (FAT32, NTFS, something else?).

Thanks,
Aaron

---

### Post by aarondesk on 2007-03-01
> **punx45 said:**
> Reading some of the newer replies it seems like there may be some confusion in details with Master Boot Records and GRUB etc.

On a dual drive install, grub is going to install on the MBR of whichever drive you are installing Ubuntu on.   Nothing is done with the Windows drive ever, aside from possibly stating its presence during the install for mounting purposes later (grub can also detect the presence of a windows partition on another disk during install).   

So with my system, If I choose the Windows drive (HDD0/master) in BIOS it boots directly to Windows.   If I choose the Ubuntu drive (HDD1/slave) in BIOS, it boots to GRUB, where I then have the choice between Linux and Windows.   

So, when doing a multi-drive install, even if you install GRUB, it will not write to or interfere with the MBR on the Windows drive.   Every disk has potential for an MBR.  You are not required to use the MBR on the Windows drive if you don't want to.

Let me know if I have this right. 

I put in new HD as slave. Pop in Ubuntu CD. I choose to install to HDD1/slave. It writes over MBR of HDD1- doesn't touch MBR of HDD0. It installs correctly.

I have BIOS set to boot from HDD0/master (XP) first. My system will always boot to XP, because the MBR on HDD0 doesn't know anything about the Ubuntu install. If I change the BIOS to boot to HDD1/slave, then GRUB will let me choose XP or Ubuntu.

Correct?

---

### Post by netkid91 on 2007-03-01
Yes, that is correct.

---

### Post by confused57 on 2007-03-01
> **aarondesk said:**
> Let me know if I have this right. 

I put in new HD as slave. Pop in Ubuntu CD. I choose to install to HDD1/slave. It writes over MBR of HDD1- doesn't touch MBR of HDD0. It installs correctly.

I have BIOS set to boot from HDD0/master (XP) first. My system will always boot to XP, because the MBR on HDD0 doesn't know anything about the Ubuntu install. If I change the BIOS to boot to HDD1/slave, then GRUB will let me choose XP or Ubuntu.

Correct?

Grub doesn't always install to the mbr of the drive that you're installing Ubuntu on...before you boot up your install cd, go into bios and change your slave drive as your first hard booted(before the Windows drive)...this "should" make make grub recognize your slave as the first hard drive(hd0)...or disconnect your Windows drive before installing, but still select your slave drive to boot as the first hard drive.

---

### Post by aarondesk on 2007-03-01
> **confused57 said:**
> ...or disconnect your Windows drive before installing, but still select your slave drive to boot as the first hard drive.

Thanks... if I install Ubuntu with only my new drive inside the computer (remove original XP drive), and then later put my XP drive back in after installation, will GRUB recognize the XP HD and allow me to boot to it?

---

### Post by confused57 on 2007-03-01
> **aarondesk said:**
> Thanks... if I install Ubuntu with only my new drive inside the computer (remove original XP drive), and then later put my XP drive back in after installation, will GRUB recognize the XP HD and allow me to boot to it?
Yes, but you should probably still select the slave drive to be the first booted hard drive in bios(may not need to do this, but won't hurt anything), before booting up the live cd to install Ubuntu...see my earlier link I gave you for an entry to boot Windows:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

You're probably aware of this, but you would just need to disconnect the Windows hard drive rather than removing...if this is what you intended to do...be sure your jumper settings are correct on the slave drive.

---

### Post by aarondesk on 2007-03-03
Ok, this has gotten more complicated than I thought. It turns out I have a Sata drive for XP, and my new drive is an IDE drive, set as slave to a CD-ROM. I unplugged the XP SATA drive, then added the IDE drive and installed Ubuntu fine. Now, the way I can dual-boot is to use the BIOS to select the boot method.

I have looked at some of the links listed in this topic, but I can't get them to work so that I can just use GRUB.

For example, adding the following to my menu.1st doesn't work. It turns out I have a partition on my Sata drive that holds the "Recovery" files for my computer. I guess that's how some factory configured computers come these days. The following tried to boot me into Recovery mode (from the recovery partition), which somehow failed. 

[INDENT]title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1[/INDENT]

I played around with the root section to change hd1 around, but couldn't get it to work. Does anyone know what I should set the 'root hd' line to ? hd1? hd2? 

In summary, I have the following. 

[INDENT]Sata HD with 2 partitions. 1st has recovery Partition and 2nd has Windows XP. 
IDE CD-ROM
IDE HD set as Slave. Has 3 partitions. 18 MB as EXT3 for linux, 1 MB for SWAP, and 9 MB for FAT32 partition to share files. [/INDENT]


Here's the output from 'fdisk -l' if it helps.


[INDENT]Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1046     8401963+   c  W95 FAT32 (LBA)
/dev/sda2   *        1047       24321   186956437+   7  HPFS/NTFS

Disk /dev/hdd: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2295    18434556   83  Linux
/dev/hdd2            3555        3649      763087+   5  Extended
/dev/hdd3            2296        2422     1020127+  83  Linux
/dev/hdd4            2423        3554     9092790    b  W95 FAT32
/dev/hdd5            3555        3649      763056   82  Linux swap / Solaris

Partition table entries are not in disk order[/INDENT]

---

### Post by aarondesk on 2007-03-03
Doh!

Buried in one post I read mentioned that you can change 'root (hd1,1)' in menu.lst to specify the second partition. That worked!

Hurray! I'm off and running! 

Thanks for all your help. 
:)

---

