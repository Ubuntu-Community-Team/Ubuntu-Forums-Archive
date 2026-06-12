---
title: "First Time User"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by BOZG on 2007-04-23
I've been seriously thinking about switching over to Linux from Windows but I'm worried about problems with hardware and the drivers etc.  I'm just wondering if anyone could let me know if the hardware I have would work ok with Ubuntu or not.  I've used Linux a number of times but I've never had to install it.  I'm also wondering if Ubuntu will come with basic drivers installed for hardware or whether I'll have to download it and how easy it is to set up routers.  My basic hardware config is below.  Thanks.

Sparkle GeForce 8800GTS 640MB PCI-e
AMD AM2 X2-5200 Dual Core Processor
Gigabyte GA-M51GM-S2G Motherboard

---

### Post by dpar on 2007-04-23
Download the live cd and try it. It won't change your system at all and it will give you a chance to see if it will work well on your system.

---

### Post by igknighted on 2007-04-23
> **BOZG said:**
> I've been seriously thinking about switching over to Linux from Windows but I'm worried about problems with hardware and the drivers etc.  I'm just wondering if anyone could let me know if the hardware I have would work ok with Ubuntu or not.  I've used Linux a number of times but I've never had to install it.  I'm also wondering if Ubuntu will come with basic drivers installed for hardware or whether I'll have to download it and how easy it is to set up routers.  My basic hardware config is below.  Thanks.

Sparkle GeForce 8800GTS 640MB PCI-e
AMD AM2 X2-5200 Dual Core Processor
Gigabyte GA-M51GM-S2G Motherboard

Unfortunately you have very new hardware.  That video card is supported only by the very latest nvidia driver, and you must install it the hard way (it hasn't worked its way though yet).  Aside from that, all the drivers you need should be included (unlike windows) with no further update required.

NOTE: You will be able to boot and run that card fine OOTB, but 3d acceleration will require the very latest 100.xx driver from nvidia.com

EDIT: You will probably notice that system will hardly ever be taxed in linux.  I play full screen FPS games in linux with all settings on at my max res (1280x1024 lol) and it runs at well over 100 fps.  This is the unreal and quake engines though, so nothing super new.

---

### Post by BOZG on 2007-04-23
Cool, thanks a lot guys.  I'll give the Live CD a try first.

---

### Post by Skidpad on 2007-04-23
> **BOZG said:**
> Cool, thanks a lot guys.  I'll give the Live CD a try first.
Make sure you check the MD5 sum, burn the cd as an image (not just a data file) at a slow speed - higher burn speeds sometimes result in error-prone disks that won't function properly.

Oh, and welcome!  :)

---

### Post by BOZG on 2007-04-24
I checked the md5sum already.  Had to go onto the irc server to get it because it's not on the site for 7.04 yet.

---

### Post by tgalati4 on 2007-04-24
Post your Bogomips!  We're curious.
less /proc/cpuinfo
Ubuntu will fly on newer hardware.

---

### Post by BOZG on 2007-04-24
I tried running it Live but for some reason, the desktop sometimes starts halfway across the screen then when I restart it, it will work fine and then switch back to halfway again.  Any ideas?  I'm tempted to just install it and see how it goes but I don't want to delete some of the files I have on my hard drive at the moment until I get some blank DVDs.  If I install it on a partition and have it as a dual boot with Windows, will it format my whole hard drive first?  I wouldn't mind installing it on the partition, checking it works ok and then buying DVDs tomorrow and doing a fresh, full install.

Secondly, I installed it on my old PC running a GeForce Ti 4400 but asks me to enable the 3d driver.  When I enable it, it tells me to restart so as to check Desktop Effects but when I restart, it asks me to enable again.  Any idea what that problem is? I tried enabling on my new PC while in Live and it downloaded a file and asked me to restart but I assume that because I'm running Live that it can't actually install the driver.  My old PC is not connected to the internet because I've no ethernet connection on it at the moment.  If I connect to the Internet should it work?

tgalati4,
I'll post anything you want if I can get it to work. =P

---

### Post by BOZG on 2007-04-24
By the way, I'm running XP on my old PC and Vista on the new one.

---

### Post by baosheng on 2007-04-27
> **BOZG said:**
> 

Secondly, I installed it on my old PC running a GeForce Ti 4400 but asks me to enable the 3d driver.  When I enable it, it tells me to restart so as to check Desktop Effects but when I restart, it asks me to enable again.  Any idea what that problem is? I tried enabling on my new PC while in Live and it downloaded a file and asked me to restart but I assume that because I'm running Live that it can't actually install the driver.  My old PC is not connected to the internet because I've no ethernet connection on it at the moment.  If I connect to the Internet should it work?


Sure, of course, a LIVE CD doesn't store any thing. Everything is loaded into the memory where they will lost after reboot. So you actually didn't install the driver.

Can you network card integrated on the GA-M51GM-S2G motherboard work well?
Which Ubuntu version did you use?

---

### Post by baosheng on 2007-04-27
> **BOZG said:**
> I tried running it Live but for some reason, the desktop sometimes starts halfway across the screen then when I restart it, it will work fine and then switch back to halfway again.  Any ideas?  I'm tempted to just install it and see how it goes but I don't want to delete some of the files I have on my hard drive at the moment until I get some blank DVDs.  If I install it on a partition and have it as a dual boot with Windows, will it format my whole hard drive first?  I wouldn't mind installing it on the partition, checking it works ok and then buying DVDs tomorrow and doing a fresh, full install.


You can search on the Internet. There are many articles about how to prepare your partitions for dual boot Linux and Windows. 

To install Linux, you will need at least two new partitions, on is ext3 format and another is swap format.

You don't need to format the entire hard drive. You can let Windows and Linux co-exist on the same hard driver, but in different partitions. Meanwhile, you can put files that need to be accessible by both Linux and Windows on a FAT32 partition. Only make the partition to put Linux system files into ext3.

---

