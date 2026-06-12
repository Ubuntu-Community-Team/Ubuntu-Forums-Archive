---
title: "Tri-Booting Mac OS X Snow Leopard, Windows 7, and Ubuntu 10.10 Netbook"
date: 2010-10-28
forum: Apple Hardware Users
---

### Post by rashhashan on 2010-10-28
Following the title...what is the best way of doing  this...please give me a walk through...im seeking optimal performance from all 3 operating systems

**My Current Machine**
Macbook 5,1
350 Gb 7200 rpm WDScorpio Black HDD
2 Gb Ram
2.4 GHz Core 2 Duo Proc


Thanks,
Rash

---

### Post by itismike on 2010-10-29
Hey Rash,

I just did this on my 6,2 MBP but can't find the guide I followed. Assuming your Mac also uses an EFI filesystem, here's what I remember:

[LIST=1]
[*]In MacOS: install rEFIt. Update the system and firmware if available
[*]In Mac recovery CD: (hold down Option or use the rEFIt menu during reboot to boot from CD/DVD) Launch disk utility and add partitions to your drive as follows:
[LIST]
[*]MacOS (leave alone)
[*]Windows (FAT32)
[*]Linux (FAT32)
[*]Swap (FAT32) - make this about 1.5 times as large as your system RAM (I have 4GiB installed, so I made mine 6GiB. Probably overkill...)
[/LIST]
[*]Boot back into MacOS and test the disk to be sure the partitioning didn't disturb anything. If it did, attempt a repair, either while booted or from the Mac OS recovery DVD.
[*]Install Windows. Choose Advanced > Format the Windows partition.
[*]Install antivirus
[*]Tell Windows to not mess up the system time: [http://ubuntuforums.org/archive/index.php/t-661577.html]("http://ubuntuforums.org/archive/index.php/t-661577.html")
[*]Install updates > reboot > repeat
[*]Install Ubuntu. Choose Manual Partitioning and mount the large partition as "/" and the swap partition as 'swap.' Also, at the last screen of the installer, be sure to set the specific partition to install GRUB on. I believe mine was SDA4. (It should end with a number)
[*]Install updates > reboot > enjoy!
[/LIST]
I think that's most of it. I had to do this about 3-4 times before I got the steps right. Good luck!

---

