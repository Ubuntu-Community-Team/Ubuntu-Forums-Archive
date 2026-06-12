---
title: "Need help with dual boot"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by f4llin on 2007-03-07
Hi there. First off, I'm new to Ubuntu and Linux in general. Here is my scenario:

my specs:

Intel E6600 core 2 duo
2Gb ram
Gigabyte GA-945P-S3 mobo
Gigabyte GeForce 8800 gts 320 Mb <- (had a bit of trouble with this)
320 Gb sata hdd (one 320 gb NTFS partition)
40 Gb external sata hdd - connected by usb (18 gb NTFS, 1 gb linux swap, 17 gb for ubuntu)

I installed Windows XP pro SP2 on the 320gb hdd and Ubuntu on the external (17gb part.)

This is how I installed Ubuntu: I physically unplugged my 320 gb hdd (Windows xp) and installed Ubuntu on my external - because I was scared that I would screw up my Windows installation/partition somehow. Windows still works, but Ubuntu freezes up on the loading screen if the 320gb hdd (with Windows) is plugged in.

I haven't really done anything in Ubuntu yet so it wouldn't be the end of the world if I have to reinstall Ubuntu... Please just tell me how!! (without creating some sort of dependancy between the two hard disks).

Thanks in advance.

---

### Post by edwardLS on 2007-03-07
I am not exactly sure of this, but I suspect that your configuration files used to boot ubuntu were set up during installation, and the device id was marked numerically based upon it being the only drive.  When you re-attach the Windows drive, the numerical numbering "may" change and those configuration files point to the wrong place now.

---

### Post by f4llin on 2007-03-07
Okay, can someone help me change the config file so it reconises the second disk, or should I reinstall Ubuntu with both disks plugged in

---

### Post by mahiyar on 2007-03-07
w/o the 320 gb hard drive does ubuntu work?

---

### Post by f4llin on 2007-03-07
yes. When the 320 gb is unplugged, ubuntu works.

---

### Post by Addison on 2007-03-07
I have a set up similar to yours (my two drives are internal) and I installed ubuntu 6.06 on the second drive (both connected) with no problems. A utility was installed on the first (Win XP) drive that gives me a choice as to which operating system will start. You will be given a clear choice to pick which hard drive to install ubuntu on, just pay close attn to the screen during install. Your hard drives will be labeled onscreen with the same numbers that you will see in your bios so, to be absolutely sure, go into your bios and write down the number of the drive you want to install ubuntu on.
  I would suggest first using the ubuntu cd without installing to test how well it works with your sys, ie if it recognizes your internet connection, printer, etc. If you don't already have it I would suggest 6.10 since it is more likely to recognize your new setup. 
 Of course back up your Win XP drive, but you were doing that anyway, right?
Addison

---

### Post by confused57 on 2007-03-07
You'd need to change your boot order in bios, whenever you're using your external hd with Ubuntu...the external hd will need to be selected to boot before your internal hd.  You can also add an entry to grub on your external drive to boot Windows, see the example in this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Ok, I think I know what the problem might be...boot first to your external Ubuntu drive, at the grub menu at bootup, highlight your Ubuntu entry, press "e" to edit, then change the root entry in your kernel line to root=/dev/sdb1, if root is on the first partition of the drive(or sdb2,sdb3...if it's on partitions 2 or 3)...then press "b" to boot.

I'm just guessing that your external drive is sdb...you can determine what it actually is by booting up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by mahiyar on 2007-03-07
I'am not sure I understand, you installed Ubuntu on an external drive (with the internal drive disconnected), so grub must be installed on the external drive, then this means that you can select from bios from which drive to boot? am i correct?

---

### Post by f4llin on 2007-03-07
yes that is correct... but when i choose the ubuntu drive (with the internal drive connected) then ubuntu hangs at the loading screen

---

### Post by confused57 on 2007-03-07
I've edited my first reply...see if the suggestion works.

---

