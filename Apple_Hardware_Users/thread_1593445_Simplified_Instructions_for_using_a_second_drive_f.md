---
title: "Simplified Instructions for using a second drive for Ubuntu?"
date: 2010-10-11
forum: Apple Hardware Users
---

### Post by obast on 2010-10-11
Drives are much cheaper than my time. 

So I want to just install Ubuntu on a second drive. Unfortunately, most of the docs seems focused on installing Ubuntu on a partition of the main drive, or using refit which can't deal with a second drive. 

I tried just booting the Maverick Live CD (after getting the port version, sigh), but the "reformat the drive and install Ubuntu" option doesn't seem to build the right partitions on the mac. 

Does anyone have any simplified instructions for installing Ubuntu on a second  drive? Ideally I just want to be able to hold down the option key and switch between MacOSX and Linux.

---

### Post by zeroti on 2010-10-11
Try this:

[https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks](https://help.ubuntu.com/community/Installation#Installing%20on%20external%20or%20RAID%20hard%20disks)

---

### Post by MiXor on 2010-10-11
Hey,

it seems that booting from an external drive with a mac isn't guaranteed to work:
[http://support.apple.com/kb/HT1948?viewlocale=en_US](http://support.apple.com/kb/HT1948?viewlocale=en_US)
I hope you do get it to work, but if it doesn't there's always the option of running a virtual machine like virtualbox.
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Best of luck!

---

### Post by obast on 2010-10-11
Actually, I'm installing on a second internal drive because its a MacPro so those aren't quite right. 

I found these directions:

[http://www.kapsi.de/blog/2008/09/21/installing-ubuntu-804-on-a-mac-pro/](http://www.kapsi.de/blog/2008/09/21/installing-ubuntu-804-on-a-mac-pro/)

And I'm modifying them as follows because things seem slightly simpler with Maverick. 

[SIZE="3"]Things you need:
[/SIZE]

1. An Ubuntu Live CD. If you want 10.10, be sure to download the "port" version. 
2. A rEFIt CD. refit.sf.net  You don't have to install it, I didn't, but you need to boot from it once after installing so it can do some magic stuff. 

[SIZE="3"]Prep the drive by building two partitions in **GUID Partition Table format**:
[/SIZE]
a.    Launch Disk Utility in MacOSX
b.    Choose the drive you're installing to.
c.    Choose the partition tab.
d.    Choose options and select "GUID Partition Table"
e.    Choose 2 partitions and make one of them big named linux, and the other approximately 3 times your RAM named Swap.

Why: Having the disk in MBR format was the big gotcha for me, the Mac wouldn't boot Ubuntu from it and I couldn't figure out why. You also need to do this on the MacOSX side so that there's an EFI partition. 

[SIZE="3"]Install Ubuntu:
[/SIZE]
1. Boot the LiveCD by restarting and holding down C. Select "Try Ubuntu"

  NOTE: At the moment I write this, 10.10 was just released which had an issue with macs, and so you need to download a mac-specific version of the Ubuntu live CD by going do cdimage.ubuntu.com and navigating through the ports. 

2. Select the Advanced installation where you get to select partitions. 
3. Look for the drive where you want to install. /dev/sd_ where _ is the correct letter.  In my case it was easy to tell  because my Ubuntu drive was a different size than all the others. 
4. Click on the partition you made for Linux, in my case it was /dev/sdb2. Click "change". Change the type to ext3, tell it to format, and make the mount point /. 
5. Click on the swap partition, click change, make it type swap. 
6. **Specify the big ext3 partition as the location for the boot loader. **
7. Install. 

[SIZE="3"]Let rEFIt do its magic:[/SIZE]

When the install tells you to restart, do that, but after it ejects the Ubuntu Live CD, put the rEFIt cd in and restart. Hold down C so it reboots into rEFIt.

At this point, you should see macosx, rEFIt and linux icons. For some reason I ended up with 2 Linux icons "boot into Linux HD" and "boot into Linux". The first one didn't work for me, so I chose the second one. That worked, and Ubuntu booted. (Actually GRUB boots first, but whatever)

Now here's the cool part. rEFIt did some kind of magic when it booted linux. You can now switch between MacOSX and Ubuntu by using the option key at startup. It will think that "Ubuntu" is Windows, but I can live with that. So you no longer need the rEFIt CD.

---

### Post by ThoFre97 on 2011-01-05
I, too, have an internal hard drive dedicated to ubuntu. The live CD I'm using is from caelinux.com, which is based on the recent Ubuntu 10.04 LTS 64bit distribution.

I've been able to follow all of the above until we get to this part:

[SIZE=3]"Let rEFIt do its magic:[/SIZE]
When the install tells you to restart, do that, but after it ejects the Ubuntu Live CD, put the rEFIt cd in and restart. Hold down C so it reboots into rEFIt."

I didn't find a bootable rEFIt disk. I had previously installed rEFIt so that is what came up. As above, 
"I ended up with 2 Linux icons "boot into Linux HD" and "boot into Linux". "
but neither one works. I get a black screen with a blinking underscore.

Thanks in advance for help.

Configuration:
MacPro4,1
3 internal sata drives, one exclusively for linux.
Nvidia GeForce GTX285 with dual monitors

---

### Post by ThoFre97 on 2011-01-05
HO HO HO! Merry Christmas!

Upon further shutdowns/rebootings, I started up holding down the option key and LO & BEHOLD, there is now a "Windows" option that is actually the dedicated linux drive. Selecting that leads to a 
"GNU GRUB Version 1.98-1ubuntu7"
screen with options to boot from all the various disks/partitions on the system. Once booted, everything looks just like it does when booted from the live CD. 

Amazingly, even the Wacom tablet/mouse works!

THANK YOU OBAST and all other supporting cast.

---

### Post by macyf on 2011-01-07
"Why: Having the disk in MBR format was the big gotcha for me, the Mac wouldn't boot Ubuntu from it and I couldn't fiqure out why. You also need to do this on the MacOSX side so that here's an EFI partition."

Could you elaborate on this a little more.
Do I make a partition in MacintoshHD and if I do, what next?

---

### Post by GeoffRoynon on 2011-01-08
> **macyf said:**
> "Why: Having the disk in MBR format was the big gotcha for me, the Mac wouldn't boot Ubuntu from it and I couldn't fiqure out why. You also need to do this on the MacOSX side so that here's an EFI partition."

Could you elaborate on this a little more.
Do I make a partition in MacintoshHD and if I do, what next?

I'm also interested in the answer to this question. I have a MacPro and will be getting a second internal disk (30GB) next week which I want to use for Ubuntu.

Thanks for the instructions - I've been searching the web for this!

---

### Post by ThoFre97 on 2011-01-08
> **macyf said:**
> "Why: Having the disk in MBR format was the big gotcha for me, the Mac wouldn't boot Ubuntu from it and I couldn't fiqure out why. You also need to do this on the MacOSX side so that here's an EFI partition."

Could you elaborate on this a little more.
Do I make a partition in MacintoshHD and if I do, what next?

I'm not an expert on this but I did get it working. I just followed the steps as outlined by obast.

Macyf, I'm very confused by "Do I make a partition in MacintoshHD." Normally that is your OSX boot drive. In step b you would be partitioning the second internal drive that you are dedicating to linux; it would almost certainly have a different name than "MacintoshHD."

All of the "Why...EFI partition" is just some brief sort of explanation of why steps a through e need to be performed; no action is required in response to it.

As a PS: to my experience, my OS X boot drive has a BootCamp partition. I can get that to boot by selecting the linux disk in rEFIt, which leads to the GRUB screen, where I can select the BootCamp partition and proceed to boot XP. The only problem - I can't get it to boot from within VMware Fusion... darn...

---

### Post by macyf on 2011-01-08
> **ThoFre97 said:**
> I'm not an expert on this but I did get it working. I just followed the steps as outlined by obast.
 
Macyf, I'm very confused by "Do I make a partition in MacintoshHD." Normally that is your OSX boot drive. In step b you would be partitioning the second internal drive that you are dedicating to linux; it would almost certainly have a different name than "MacintoshHD."
 
All of the "Why...EFI partition" is just some brief sort of explanation of why steps a through e need to be performed; no action is required in response to it.
 
As a PS: to my experience, my OS X boot drive has a BootCamp partition. I can get that to boot by selecting the linux disk in rEFIt, which leads to the GRUB screen, where I can select the BootCamp partition and proceed to boot XP. The only problem - I can't get it to boot from within VMware Fusion... darn...
 
Thanks ThoFre97
I just read it the wrong way

---

