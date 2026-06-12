---
title: "Unable to Boot Ubuntu due to Grub Error 18"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by malicentre on 2006-03-05
Hoping for some help from a kind soul as so far I haven't been able to figure this out ...

I have an older 733Mz PIII running W2K that I added a 160Gb drive to after the original drive died, and now I'm trying to install Linux on it.  (Disclaimer: This is my very first foray into the Linux world.)

I've tried installing a couple of times with slightly different partition configurations, and each time I end up dead in the water due to the Grub error 18.  I know that is due to boot partition for the Linux install not being able to be seen by the bios, but I can't figure out how to partition the drive using the Ubuntu installer to fix this issue.

Here's what I've done so far.  Any suggestions on what I should do differently would be greatly appreciated. :D 
- Chose the manual partitioning option
- Default view shows two partitions:  The existing W2k one is ~137Gb, and the remaining part of the drive shows up as free space
- Created 32 Mb /boot partion
- Created 10 Gb root partition, and marked it as bootable
- Created 1 Gb swap partition
- Created /home partition with the remaining space (~15.4 Gb)

The initial install then seems to start ok, but then error 18 crops up during Stage 1.5.

From reviewing posts and Googling I've done so far, I know that this error is caused by the fact that there's an issue with my Bios not being able to see the part of the drive that has the boot partition. And the suggested workaround was to create a /boot partition where the Bios can see it.  I've found out how to create a /boot partition, but here are my questions:

1) What needs to go into the /boot partition, and how do I get it there?  (Or is this automatically handled by the installer?)

2) How do I get this partition to a location on the drive where the Brios can actually see the information on it?  (The free space is all at the end of my drive, and I don't see any option how to move/change my Windows partition except for deleting it ... and I don't want to do that.)

---

### Post by Sutekh on 2006-03-05
[QUOTE=malicentre]

1) What needs to go into the /boot partition, and how do I get it there?  (Or is this automatically handled by the installer?)[/QUOTE]Well the [GRUB (GRand Unified Bootloader)](http://www.gnu.org/software/grub/) and the kernels go in /boot.  GRUB can be used to boot both Windows and Ubuntu.

I know how you can put GRUB in that /boot partition, but I don't know how your BIOS would choose to boot from there though.  As far as I know, the BIOS can only choose the *hard drive* to boot from not the *partition*. 

[QUOTE=malicentre]
2) How do I get this partition to a location on the drive where the Brios can actually see the information on it?  (The free space is all at the end of my drive, and I don't see any option how to move/change my Windows partition except for deleting it ... and I don't want to do that.)[/QUOTE]
No I wouldn't remove the Windows partition.  

If you install the GRUB into the MBR (Master Boot Record) of your hard disc then when your PC boots GRUB will load up, allowing you the choice of OS to use.  

During the installation you will get to this screen 
[ATTACH]6773[/ATTACH]

(thanks to [Herman](http://www.ubuntuforums.org/member.php?u=31861) for the guide)

The GRUB should detect that Windows is also installed and offer to install on the MBR, if Windows is detected then let it do so.

When your PC is booted up, you will have the option of booting Windows or Ubuntu from a menu like this
[ATTACH]6774[/ATTACH]

---

### Post by malicentre on 2006-03-06
Unfortunately I've tried this already - i.e., I installed GRUB into the MBR (following Herman's detailed instructions), and this doesn't work. :(

From what I've read since the MBR is limited in space (512 MB if I recall correctly), GRUB isn't actually installed here.  The MBR only contains instructions to the actual location where GRUB can be found.

Then the problem is that with older computers, the BIOS can't see entire disk.  So during startup, this leads to the GRUB error 18 since the actual files for GRUB are on a part of the disk that's not seen by the BIOS.

Any other ideas?  I'm really stuck.

---

### Post by lha on 2006-03-06
[QUOTE=malicentre]1) What needs to go into the /boot partition, and how do I get it there?  (Or is this automatically handled by the installer?)

2) How do I get this partition to a location on the drive where the Brios can actually see the information on it?  (The free space is all at the end of my drive, and I don't see any option how to move/change my Windows partition except for deleting it ... and I don't want to do that.)[/QUOTE]

1) If you make a /boot partition, installer takes care of putting the right this there. Just tell installer to mount the partition at /boot. I prefer not to have a separate /boot, I keep it on root partition.

2) If you want to use grub, you have to get /boot in the beginning of your drive. (Or if you don't make a partition for /boot, you have to put root in the beginning.) So you'd have to resize/move your win2k partition to make room for Ubuntu's partition. You might find a program that is able to move your Windows partition. (I'm assuming it's ntfs. Fat would be easier.)

Or, use ntldr, Windows' own boot loader. (This is the first time I recommend it to someone.) Install the way you see fit, but make root (or /boot if it is on a partition of its own) primary and install grub on that partition's boot sector. (Not to mbr.) Then use [bootpart]("http://www.winimage.com/bootpart.htm") in Windows to add Ubuntu to ntldr's menu. Disclaimer: I haven't tested method described above, but I think it's worth trying if you can't make room in the beginning of you drive.

---

### Post by DerekInGermany on 2006-03-07
Hi malicentre,

I had the same problem and what I had to do was update the BIOS on the motherbaord, then it worked fine.

Something to do about reading large Harddrives.

Hope that helps

Derek

---

