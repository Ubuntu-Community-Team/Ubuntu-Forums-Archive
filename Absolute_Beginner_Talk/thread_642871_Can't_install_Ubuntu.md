---
title: "Can't install Ubuntu"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by chopsuwe on 2007-12-17
I am not having any luck with Ubuntu at all. I installed Ubuntu 5.10 and it seemed to work. I then turned my pc off popped in v7.04, turned on and started the install process. After the initial splash screen it came up with the error "can't access tty; job control turned off". 

Thinking it maybe a problem with the old installation on the drive I stuck in the Win98 boot cd and deleted all partitions using fdisk. Then created a new partition usuing the maximum available space. Here's where it gets interesting. The maximum free space fdisk sees is 8GB but it is a 20GB drive, and is recognised in bios as 20GB. 

I used fdisk to delete all the partitions again, formatted it in dos and rebooted. The computer tries to boot off the hard disk but instead of coming up with an error saying operating system not found it comes up with a message about a problem in grub. 

This system used to work perfectly in Win98, Win2k, WinXP.

What has linux done to my drive and how do I fix it?

Specs:
Duron750
MS-6390 VIA KM266
Integrated ProSavage8 AGP 4x
Seagate 20GB

---

### Post by 720iD on 2007-12-17
> **chopsuwe said:**
> 

I used fdisk to delete all the partitions again, formatted it in dos and rebooted. The computer tries to boot off the hard disk but instead of coming up with an error saying operating system not found it comes up with a message about a problem in grub. 

This system used to work perfectly in Win98, Win2k, WinXP.

What has linux done to my drive and how do I fix it?


you get an error message about grub so it might be a problem with grub.
perhaps grub has been formatted with the rest of your hdd!

---

### Post by chopsuwe on 2007-12-17
The idea was to scrub everyting clean and start out again since I now can't install Linux or Windows and have lost over half the capacity of the drive.

---

### Post by 720iD on 2007-12-17
stick with it you will work it out. what is happening now when you try to boot from a cd?

---

### Post by chopsuwe on 2007-12-17
If I put in 5.10 it comes up to the normal install options screen. But I want to install 7.04 which goes as far as the original "can't access tty; job control turned off" error. 

In the WinXP installation it gives the option of removing all the old partitions. Surely Ubuntu has something similar?

---

### Post by 720iD on 2007-12-17
could be your iso has corrupt during burning or download. can you check the integrity of your CD some way?

---

### Post by lgambett on 2007-12-17
Try also using the Ubuntu alternate CD (not the desktop one) to install. It performs a textual installation, making easier to spot errors and problems.

---

### Post by discoade on 2007-12-17
the problem your having with fdisk is you are working with dos drives if you go back into fdisk and check your drive again you should find a partition that's a non dos partition, the linux partition there's an option in there to delete non dos partitions that's what you need to regain your disk space!  once you have it back and if your not installing windows let linux set the drive up for you on install!

on boot up if your getting a message from grub then you obviously haven't deleted all your partitions as the grub is still present!

---

### Post by geirha on 2007-12-17
If the fdisk in win98 can't see all 20GB then don't use it, it's ancient and unreliable.

With the 7.04 cd, when do you get that error, when you boot the CD, or after installing it?

---

### Post by chopsuwe on 2007-12-17
discoade:
There was a extended partition of about 800MB and a non-dos partition of about 18GB. I deleted both using fdisk and rebooted. Fdisk then reported no partitions at all. I created a primary dos partition using all available space, rebooted and formated it in dos. During the partitioning fdisk reports only 8GB available on the drive total. I am missing 12GB.

If all the partitions were deleted why was grub still there?

> **geirha said:**
> If the fdisk in win98 can't see all 20GB then don't use it, it's ancient and unreliable.

With the 7.04 cd, when do you get that error, when you boot the CD, or after installing it?

Put in cd, turn on power, boot from CD. Ubuntu menu asking what sort of install (normal, safe graphics, etc). Select the top option (normal install). Splash screen showing the ubuntu graphic and a progress bar. After 7 min or so there is a black screen with white writing and the error message.

---

### Post by vt100 on 2007-12-17
Two parts:

1) Grub.... Don't worry about it. (Quick and simple) It has two pieces, one resides on the Linux partition which holds the configurations and the other on the MBR (Master Boot Record) of the disk if you wiped the partitions the MBR portion can't find the configurations and will error out (nothing to boot).

2) Check the disk make sure its not corrupt. Does Linux see all 20G when you get to where you can partition the disk? if not you may need to enable large disk support in the BIOS too.   after you download a new copy of the install disk and burn it see if you get the same error.

---

### Post by geirha on 2007-12-17
> **chopsuwe said:**
> 
If all the partitions were deleted why was grub still there?

GRUB is usually not installed on a partition, but rather at the MBR (first 512 bytes) of the harddrive.

> **chopsuwe said:**
> 
Put in cd, turn on power, boot from CD. Ubuntu menu asking what sort of install (normal, safe graphics, etc). Select the top option (normal install). Splash screen showing the ubuntu graphic and a progress bar. After 7 min or so there is a black screen with white writing and the error message.

In that case, choose the option to check the CD in that boot menu. If that check fails, try burning a new one at a lower speed. And if you have the internet connection for a 700MiB download, download ubuntu 7.10 instead.

---

### Post by chopsuwe on 2007-12-17
I'll check the cd tomorrow. Downloading it again really isn't an option on dialup.

---

### Post by 720iD on 2007-12-17
have you tried safe graphic option on install. if your computer is older and if the graphics chips are not great, then that could be why you get a blank screen. if you choose safe graphics or if you can choose vga options then set your vga to a lower resolution like 800x600.

---

### Post by meindian523 on 2007-12-17
> **geirha said:**
> GRUB is usually not installed on a partition, but rather at the MBR (first 512 bytes) of the harddrive..
Not necessarily,depends on where the user decides Grub should be put....


In that case, choose the option to check the CD in that boot menu. If that check fails, try burning a new one at a lower speed. And if you have the internet connection for a 700MiB download, download ubuntu 7.10 instead.[/QUOTE]
lower speed ==preferably 4x

---

### Post by chopsuwe on 2007-12-19
I get the error when using option 1 - Normal install, 2 - safe graphics, and 3 - check CD. I guess that means the CD is no good. 

Is there any way to check to see which files are no good and just download them? 700mb takes a long time on dialup.

---

### Post by geirha on 2007-12-19
If you still have the CD-image (iso-file), check if the md5sum is correct. Type ```
md5sum the-image.iso
```
The md5sums you'll find at any ubuntu mirror here [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

From what I understand you have one of the desktop CDs of feisty, so the md5sum should match one of these:

```

a2b159599b69cea51371eee1ec5feda6 *ubuntu-7.04-desktop-amd64.iso
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso

```

If they match, then it simply must be a bad burn, try again at lower speed. If they don't match, I'm afraid you will have to download it again, or request one to be sent to you [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

