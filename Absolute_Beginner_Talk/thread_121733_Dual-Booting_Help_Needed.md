---
title: "Dual-Booting Help Needed"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by LTU on 2006-01-25
Well, I want to make my computer a dual-booting system. I've tried some stuff before and I ended up having to reinstall everything.

Anyway, my system originally came with Windows XP, and I've installed Ubuntu over it because I didn't know how to partition correctly without messing up the XP partition. So I then reinstalled Ubuntu and created partitions with it, one for Ubuntu, and one for Windows. After that I installed Windows XP again, but I think I overwrote GRUB after saying during the install that I wanted XP to have the active partition. So whenever I turned on my computer again, it came to a screen that let me choose between Windows XP and an "Unknown Operating System", that of course wouldn't boot. After that I downloaded the Ultimate Boot CD and burned it to a blank CD-R and attempted to fix the set-up, hopefully so it would let me choose between Linux and Windows again. In doing that, I think I messed up my computer because it wouldn't let me boot any operating system.

So, now I have installed Ubuntu again, having made the partitions again for both it and Windows(although Ubuntu is the only OS currently installed). Is there something different I should do during the Windows installation, like not setting it to the active partition when it asks me to? 

And also, say if I wanted to get rid of either one of the operating systems for whatever reason and clear up it's partition to be available to use for the other, could I do that with either operating system(or the Ultimate Boot CD, but I'm a bit wary about using it again) and not have to reinstall either one of them all over again? If anybody could help me with those it would save me from more unneeded headaches in the near-future and would greatly be appreciated. I'm not sure if this really falls under the category of "absolute beginner" but it seemed like the best place to put it since it doesn't have to do with installing Ubuntu itself.

---

### Post by tim15856 on 2006-01-25
Try [https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28dual%29%7C%28boot%29](https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28dual%29%7C%28boot%29)

---

### Post by LTU on 2006-01-25
[QUOTE=tim15856]Try [https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28dual%29%7C%28boot%29](https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28dual%29%7C%28boot%29)[/QUOTE]
Well, right now, I have Ubuntu installed only. Should I install Windows into the other partition(FAT32 formatted, by the way), and then reinstall Ubuntu again? Sorry if I didn't make that clear enough.
EDIT: I think I tried that the last time and Ubuntu's partitioner didn't show any partitions at all. I might have installed something wrong  then, but I'm not sure what I did.

---

### Post by aysiu on 2006-01-25
Ideally, you want to install Windows first on one partition, then install Ubuntu on to the second partition and install Grub to the MBR.

Since you already have Ubuntu installed, Windows' boot loader will overwrite Grub on the MBR. So go ahead and do that. Then, [restore Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113).

Grub should automatically add Windows to the boot menu.

---

### Post by storm76 on 2006-01-25
When installing the windows OS, don't make it the active partition. Upon installing the OS, reboot. When Linux loads enter the terminal and edit the grub to reflect the new OS.

---

### Post by jaseywasey on 2006-01-26
Hello,
I had real trouble getting Grub to be the boot loader and gave up and let the windows boot loader do it for me. It's not ideal but at least I can now get into both Windows and Ubuntu. I've managed to dual boot windows XP and 2000 before (work image and home image) and this was easy.

I found:
[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)
Dual Booting Ubuntu Linux and Windows XP on a Toshiba Laptop
to be useful. I don't have a toshiba laptop but the partitioning (I didn't have FAT32) was similar. If you don't have the FAT32 partition then you can mount a floppy disk instead for the bit about copying to boot.ini.

Also I'm not sure if VMware has an evaluation version but if it does then you could experiment to your heart's content (or 30 days) on getting dual booting to work without affecting you main desktop. You'll need a big hard disk for that. VMware is a virtual PC tool and I used it recently to compare a few linux distributions.

Not very specific advice sorry but the above URL got me to the point where I could dual boot. I do have the windows boot loader working and then Grub kicking in after with Ubuntu choices again.

Jason

---

