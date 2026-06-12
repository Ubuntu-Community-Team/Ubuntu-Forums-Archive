---
title: "How to find Windows partitions"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by balasatya on 2005-10-15
Hi,
I am new to linux and ubuntu. I have installed windows 2000 on first hard disk and redhat-9 on (p-3 650MHZ PC's) second disk's 4th partition. Today I installed ubuntu on second disk's partition where i installed redhat-9.
When ubuntu asked to install which base system(kernal) I selected 1st option.(should i select 3rd one?)After installation is completed when i logged in to windows all my second drive's partitions have gone. I can't access them.
Only drive "D:\" is there! ( drive E,F have gone?)How can i retrieve my data on these drives? What wrong i have done? My bios only supports 33 GB hard disk space but my second hard disk is 40GB. Is this bois problem? How can i get my data? I hope you understand my problem.Sorry for my english.
Waiting for our reply....
yours,
abuntu

---

### Post by aysiu on 2005-10-15
Why were you asked which kernel to install? Did you do an expert install? A regular install does not ask you this question. You can mount Windows partitions using the instructions here:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

If you want a recovery CD, Knoppix is good for that.

---

### Post by balasatya on 2005-10-16
Yes, you are right I selected expert mode.
But I solved my problem by log in Rescue mode! May be until I complete my installation Ubuntu locked all Drives? I can't install Grub and still need to configure desktop. This is how I got into trouble 
1) My System configuration is:
System Information
------------------
Time of this report: 10/16/2005, 17:19:22
       Machine name: HP-BRIO
   Operating System: Windows 2000 Professional (5.0, Build 2195) Service Pack 4
           Language: English (Regional Setting: English)
System Manufacturer: Hewlett-Packard
       System Model: HP Brio
               BIOS: Default System BIOS
          Processor: Intel Pentium III, ~650MHz
             Memory: 192MB RAM
          Page File: 79MB used, 379MB available
        Windows Dir: C:\WINNT

I have Two Hard disks. On Fist one I installed win-2000 and on second 40GB, which was partitioned as four parts D(6GB), E(6GB), F(6GB), and G (22GB). I have installed RedHat-9 (now it is Ubuntu 5.4) on G drive. My Bios can read only unto 33GB. That is why Red Hat leave 8GB space as not-usable and installed the Base system on usable(I mean BIOS readable) space.
If you are thinking why I am saying all this? When I installed Ubuntu It took all space!
Is it possible to access all the space? When I try to install grub on hdd3 ( which is root partition) it says hdd3 is not recognized.  Which is the right way to install grub? I  installed redhat on hdd3. And with the command # 
dd if=/dev/hdd3 of=/bootsect.lnx bs=512 count=1
created bootsect.lnx . Then copy bootsect.lnx file to C:\  for start up screen to change OS.
I am learning web development with PHP-MySQL and want to switch to Linux OS so I can learn Linux networking concepts. Please suggest me which is the best way to install Ubuntu for my context(server or desktop). Should I wait for Ubuntu 5.10 ?       
Yours aBuntu!:)

---

### Post by aysiu on 2005-10-16
```
sudo fdisk -l
``` will tell you what partitions you have and what types they are. My guess is that Ubuntu will be the ext3 partition. The best way to do a dual-boot is to put Ubuntu's Grub on the MBR, not do that crazy dd and boot.ini stuff.

To do that, follow these instructions:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by balasatya on 2005-10-16
Hi, All my win partitions are fat-32. The problem with installing grub in MBR is if I reinstall windows, as it always happend bcz it is buggy, I would lost the Grub that is why a friend told me this method. If you recomend this is the best way then i will go on.

---

