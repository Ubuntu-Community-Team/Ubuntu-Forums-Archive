---
title: "Installing on external hard drive- it is stuck at 15% at &quot;detecting flie systems...&quot;"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Tallegio on 2007-12-01
I'm trying to install Ubuntu on my passport, it seemed to be working, but it has been stuck here for a long time now. Probably two hours. My system is pretty fast, so I don't think it should be taking this long. Or should it?

BTW, the passport is 60GB, currently with two partitions, both in FAT32, or vfat. I am using the live disc.

---

### Post by rosetown on 2007-12-01
> **Tallegio said:**
> I'm trying to install Ubuntu on my passport, it seemed to be working, but it has been stuck here for a long time now. Probably two hours. My system is pretty fast, so I don't think it should be taking this long. Or should it?

BTW, the passport is 60GB, currently with two partitions, both in FAT32, or vfat. I am using the live disc.

I'm also running Ubuntu from an external USB drive - you must right click the external drive icon on the desktop and select unmount before installing Ubuntu otherwise it sticks at 15 percent. Wow, 2 hours, I love your patience:)

If it's a dual boot with Windows, I've been led to believe that you must make sure that you safely remove the drive from the windows side before running the live CD. Anyhow that's what I did - being paranoid:)  Take my advice with a grain of salt, I'm a noob!!

Regards Duane

---

### Post by Tallegio on 2007-12-01
Thanks, it worked. 

Another quesiton... how do you boot into it once it is installed? And could i save files in Linux and have them accessible in windows or mac?

---

### Post by rosetown on 2007-12-01
You know - it would be wise if you:
1/ described your hardware
2/describe in detail ( as best as you can) what you want to accomplish

Once installed:
I cold boot into it by:
1/turning on the external USB drive
2/turning on the laptop and then pressing F12 which selects the boot menu in the bios. (your bios might behave differently than mine!!
3/select the USB drive in the boot menu
4/press enter

The above aside I had some problems:
Before you install see:
[http://ubuntuforums.org/showthread.php?t=603095]("http://ubuntuforums.org/showthread.php?t=603095")
There are also many other threads that deal with installation on an external drive and it would be wise to search for them.  I am, as I said just a noob, and I can't help you beyond this because it's beyond me:)

---

### Post by jaybombalous on 2007-12-01
grub can be installed on partitions, because sometimes old bioses can't boot the MBR on newer devices, like USB.

You have to flag partition as bootable and make sure its un-hidden. Read up on partition manager software and u will see, its not that hard.

---

### Post by rosetown on 2007-12-01
> **Tallegio said:**
> Another quesiton... how do you boot into it once it is installed? And could i save files in Linux and have them accessible in windows or mac?
You do need to tell us what hardware you have and what you are trying to accomplish and I am no longer the one to advise - are you installing on an external and trying to run it on a mac?

---

### Post by Tallegio on 2007-12-02
Okay, here is what I am doing. I have a 60GB western digital passport. I have a PC I built which doesn't have a working hard drive. So for now I want to boot off of my external until I get a new internal hard drive. It has a pentium d, 2 gigs ram, good mobo, power supply, case, an old radeon 9200se, a usb wifi device, and dvd drive. 

I want to retain use as an external hard drive though. So I can still transport files on it. So is it possible to have a boot partition then a storage partition? I assume I would use gparted and make an fat32 partition. Right now I can't find gparted though. Partition editor doesn't show up in the drop down menu. BTW, I have already installed, and am running off the external, not the live disc. And internet isn't working yet.

---

