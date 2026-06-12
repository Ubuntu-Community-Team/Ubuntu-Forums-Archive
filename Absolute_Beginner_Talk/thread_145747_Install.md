---
title: "Install"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by EX0S on 2006-03-16
Well, I let my friend talk me into Dual-Booting with Linux. Right now I have Windows XP : Home Edition. Anyways, I booted up the disk and pressed enter (BTW : I have 2 hard drives ones 82.0 GB (Windows is installed on this) and a 40.0 GB they are both NFTS). Anyways.. I read up on the Dual-Boot guid (both of them) and i'm still kinda confused! I mean... I just want to make windows use 42.0 GB and Ubuntu 40.0 GB. I'm really confused! Can you please clear this up for me? Also, i'm getting The Elderscrolls IV : Oblivion will linux or windows screw it up? Thanks! \\:D/

EDIT : What programs can I program with? Can I use Visual Basic, or C++? Am I able to also use Photoshop, or 3D modeling programs like LightWave 3D, Maya, 3DS Max?

---

### Post by aysiu on 2006-03-16
Your friend talked you into dual-booting and didn't help you set up the dual boot?

Which two dual boot guides did you use?

---

### Post by EX0S on 2006-03-16
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm), [https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28DualBoot%29](https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28DualBoot%29)

Those two.

EDIT : For some reason when I try to change my partions to 42.0 GB it stays the same to 82.0 GB nothing even happened!

---

### Post by IYY on 2006-03-17
> What programs can I program with? Can I use Visual Basic, or C++? Am I able to also use Photoshop, or 3D modeling programs like LightWave 3D, Maya, 3DS Max?

These programs are not natively supported in Linux, so you can only run them using Wine, but there's really little point of doing that if you are dual booting and can just use XP. However, there are alternatives to all (except for VB, which you should unlearn as soon as possible)

For example, GIMP is what you'd use instead of Photoshop. Instead of Microsoft's Visual C++ which is usually only used to make Windows apps, you could make programs for GTK or QT using one of the many enviorments avaliable (still coding in C or C++, of course). Some 3D modelling software can also be downloaded, though it's not quite as good as Maya or Max.

---

### Post by aysiu on 2006-03-17
If the Ubuntu installer's partitioning tool doesn't work and/or seem easy to use, you can try one of these (I recommend the last option):

[GParted](http://gparted.sourceforge.net/screenshots.php) on the Ubuntu live CD
[QTParted](http://qtparted.sourceforge.net/screenshots.en.html) on Knoppix
[DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142) on PCLinuxOS

Once you've resized, the *hermanzone* tutorial can help you select which partitions to install to and how to handle Grub.

---

### Post by xubuntux on 2006-03-17
This might work but you might need to reinstall windows if you want to use the space its currently in,

1.) remove all the partitions in the hdd (you can use fdisk on steps 1 and 2, xp installation can also do it for you).
2.) partition the hdd to how much youd want each os to use.
3.) format the partition initially to what format you will install windows(windows 98 installation requires you to do this not sure about the others)
4.) install windows on the partition for windows.
5.) after completing the windows installation install ubuntu with expert install then choose the partition you set aside for it during the install.

good luck!

---

