---
title: "install can't create directory"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by lostndazed on 2008-01-12
Recently purchased an eee pc with linux installed and have been enjoying playing with it.  I decided that I'd try to install Ubuntu 7.10 as a dual boot on an older Hp desktop running windows 98.  My grandaughter mostly uses this computer to play games on ( shes 6 yrs old).  

Anyways all seemed to be going well during the install except there was one directory that didn't install.  I can't get all the info but the first part of it says something like unable to create directory sys/device/sys/cpu/cpu0  and there is one or two directories that came after that in the same line.

Once that has completed I get an orange screen and that just stays.  Anyone have any ideas what would cause this and how I might fix it?

---

### Post by tgalati4 on 2008-01-13
Sounds like a RAM issue.  How much memory in the laptop?  You need a minimum of 128 MB RAM with a 128 MB swap disk to install Ubuntu.  It's really slow this way.  A better situation is 256 MB of RAM and 256 MB or more swap disk.  If your specs are less than this, then try burning the "alternate" disk.  It's designed for older machines with troublesome installation.  What kind of processor?

---

### Post by lostndazed on 2008-01-13
Thanks so much for the help.  It has 128 Mb of ram and it's an intel pentium III E processor at 533 Mhz.

Where can I find the alternate disk?  I had a look but can only see earlier versions of Ubuntu.

When I got thinking about it. I wondered if it was because I hadn't partitioned my hard drive.  I was assuming that the install process would do that, so that has me wondering if that could be the problem or is it as you suggested lack of ram?

---

### Post by tgalati4 on 2008-01-13
You have to manually partition your disk to give yourself a swap partition.  It is not automatic.  The standard Ubuntu installer will create a swap partition, but only if you allow it the entire disk.  If you simply squish the existing windows partition, I don't think the swap partition is created.  That is why you have to manually partition it.

This is why some folks loose all their existing data on their existing Windows partition.  If you don't know what you are doing, it's quite easy to wipe your existing Windows installation (and all of its data).

If you go to [http://www.ubuntu.com](http://www.ubuntu.com)  you will find a small check box that says:

*Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.*

This will download the "Alternate" version of the installer disk.  It is NOT a Live CD, strickly a text-based installer.  This will generally work on 128 MB RAM machines.  

Do yourself a favor, back up your critical data before manually partitioning the disk drive.

Don't expect speedy performance with 128 MB.  With 256 MB or more, a PIII, 533 MB machine is quite usable.  

I also like Linux Mint 4 XFCE.  XFCE is a light-weight window manager and Linux Mint contains all of the multimedia stuff already configured and working.

---

### Post by lostndazed on 2008-01-14
Ok, thanks, I think I'll upgrade the ram on this old machine, the max it can handle is 256 but if I can squeeze a little more life out of it for my grandaughter then all the better.

I need to do some reading up on partitioning the hard drive or could I just add another drive and leave the c drive for windows?  Would ubuntu install to that new drive without it being partitioned in any way?
 	
I had a look at the alternate cd and it says you should have some linux experience to install it and as I have practically nil I think I'll try the upgrade route with the ram.

If the worse happens and I trash windows and the data it won't be any big deal...not for me anyways..lol I'm sure my grandaughter won't be too happy but hey she's 6 and an ice cream cone will make it better..lol

Really appreciate the help.  thanks.

---

