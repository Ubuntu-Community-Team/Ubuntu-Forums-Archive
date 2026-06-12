---
title: "Windows 8 &amp; Ubuntu - Separate Harddrives"
date: 2012-12-18
forum: Any Other OS
---

### Post by snuggs8 on 2012-12-18
Hello friends,

I want to install Windows 8 alongside Ubuntu. I'm using a laptop with 2 hard drives. Ubuntu LTS 12.04 is installed on the primary hard drive and the second hard drive is just a data drive at the moment.

I was wondering what is the safest way to install Windows 8 on the second hard drive? My thoughts were to remove my Ubuntu hard drive entirely, install Windows on the remaining hard drive, and then return the Ubuntu hard drive. How would this method disrupt the boot process? Are there better methods?

Thank you for you time,
snuggs8

---

### Post by erind on 2012-12-18
> **snuggs8 said:**
> [...]

I was wondering what is the safest way to install Windows 8 on the second hard drive? **My thoughts were to remove my Ubuntu hard drive entirely, install Windows on the remaining hard drive, and then return the Ubuntu hard drive.** How would this method disrupt the boot process? Are there better methods?

[...]

I don't know about Win 8 (others can help more), but for Win 7 basically you'd pull out the ubuntu drive (as you're planning to do), install Windows on the second drive, shut it down, reconnect the first ubuntu drive, boot into ubuntu, and update grub ( **sudo update-grub** ). Now windows should show up in grub. 

More info here:

[http://ubuntuforums.org/showthread.php?t=1950071](http://ubuntuforums.org/showthread.php?t=1950071)
[http://ubuntuforums.org/showthread.php?t=1686335](http://ubuntuforums.org/showthread.php?t=1686335)

---

### Post by andrew.46 on 2012-12-20
*Safest *way is to install Windows 8 as guest with VirtualBox. Just make sure you have enough resources to share with a reasonably hungry OS :). See this on my own system:

[http://www.andrews-corner.org/images/screenshot.november.png](http://www.andrews-corner.org/images/screenshot.november.png)

That is Windows 8 in the corner with the Metro interface hidden away by the fabulous [Classic Shell]("http://classicshell.sourceforge.net/").

---

### Post by Dr. C on 2012-12-21
> **andrew.46 said:**
> *Safest *way is to install Windows 8 as guest with VirtualBox. Just make sure you have enough resources to share with a reasonably hungry OS :). See this on my own system:

[http://www.andrews-corner.org/images/screenshot.november.png](http://www.andrews-corner.org/images/screenshot.november.png)

That is Windows 8 in the corner with the Metro interface hidden away by the fabulous [Classic Shell]("http://classicshell.sourceforge.net/").

I run Windows 7 in Virtualbox on top of Ubuntu 12.04 and it works great. One suggestion with multiple drives is to place your virtual machines on a different drive from the one that has your root partition. I have found that this does improve performace. 

Classic Shell on Windows 8 looks great by the way.

---

### Post by andrew.46 on 2012-12-21
> **Dr. C said:**
> Classic Shell on Windows 8 looks great by the way.

A great application that has many, many options. Open Source too which is a bonus :)

---

### Post by 3rdalbum on 2012-12-23
Easy. Don't unplug any hard disks. Install Windows on the hard disk and then run Boot Repair from an Ubuntu live CD (its on Ubuntu Wiki for instructions) to get access back to Ubuntu.

---

### Post by oldfred on 2012-12-23
Windows knows which drive is the boot drive in BIOS. So if you do not disconnect Ubuntu drive, be sure to change boot drive in BIOS to the drive you want to install Windows before installing or it may try to write boot files to the Ubuntu drive.

Windows has to boot from a primary partition with NTFS format and boot flag or active partition in Windows. New Windows install with two partitions a small 100 to 200MB boot/repair (hidden) partition and the main install. It will also install to one preformatted partition, but may also want to reformat again. 

If a new system with UEFI install instructions are all different,  but Ubuntu & Windows have to be either both UEFI or both BIOS.

---

### Post by snuggs8 on 2012-12-26
I've never heard of VirtualBox. Thank you for introducing me to this. It is very cool. I installed Windows 8 on it and it worked great. The only problem is the only reason I want Windows 8 is to play high-end games. I looked around and it seems this just isn't possible yet in VirtualBox. When I have time I am going to try one of the other suggestions.

---

### Post by andrew.46 on 2012-12-26
3d support seems a little better (don't forget to tick that particular box, I think it is unchecked by default) but still has a way to go....

---

### Post by snuggs8 on 2012-12-26
I'm somewhat new to linux and dual-booting and decided I wasn't comfortable leaving my linux harddrive in while trying to install Windows 8.
 
I took my linux harddrive out, installed Windows 8 on the second harddrive, popped the linux harddrive back in, and ran **sudo update-grub**. Everything worked better than I could have imagined.
 
Thanks all for your input.

---

