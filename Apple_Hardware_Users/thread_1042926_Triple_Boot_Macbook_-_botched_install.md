---
title: "Triple Boot Macbook - botched install"
date: 2009-01-18
forum: Apple Hardware Users
---

### Post by Buce on 2009-01-18
I'm trying to install Ubuntu Hardy on a friend's MacBook. She had it set up to dual-boot OSX and WinXP already, and after searching for a howto or tutorial for a while, I couldn't find anything quite like what I thought I needed. Having installed a WinXP/Hardy dualboot before, I figured it couldn't be that much different, so I just dove in. Stupid and dangerous, I know...and here I am.

After searching google for a good way to resize her mac partition, I settled on using the CLI diskutil program that was already installed. I couldn't find an option for ext2 or ext3, so I formatted the new partition as FAT32.

After that, I just installed from the LiveCD to that partition as normal, reformatting with the built-in partition editor that pops up during the install. I set it up like so:

```
/dev/sda1  EFI     200M   (unchanged)
/dev/sda2  OSX     121.9G (resized down from 127.9G)
/dev/sda3  Ubuntu  5.2G   
/dev/sda5  Swap    953.7M 
/dev/sda4  WinXP   20.8G  (unchanged)
```

After finishing the install, BootCamp didn't show Ubuntu and no longer showed Windows, and after looking around google for a while, I saw a bunch of sites that suggested using rEFIt, so I downloaded and installed that. Now, when I boot, all three OSes show, but only Mac boots correctly. When I try loading the others with rEFIt, I get a blank screen with plain text that read "No bootable device -- insert boot disk and press any key", but if I insert a bootable CD a hit a random key, nothing happens.

After googling a bit more, I found [this tutorial]("http://ubuntuforums.org/showthread.php?t=187465") (wish I had seen it before). It includes instructions for backing up the Windows MBR and restoring it at some point during the installation (oops).

It also doesn't include setting up a swap partition, since you're limited to four partitions. Come to think of it, how did the LiveCD even get that 5th one on there, anyway? I thought that wasn't supposed to be possible without using logical partitions, and when I look at it from the System Rescue CD with gparted, it shows up as being primary.

So, does anyone have any idea as to how I can get things working? Can I fix the Windows MBR normally with the XP install CD, or do I have to worry about it being a Mac? Should I reinstall Ubuntu and/or get rid of the swap partition? Or can I reinstall the whole thing under a logical partition? All the data on the computer was backed up before doing the install, but I don't want to have to reinstall Windows or Mac (*especially* Mac) from scratch if I can help it.

---

### Post by cyberdork33 on 2009-01-18
> **Buce said:**
> After finishing the install, BootCamp didn't show Ubuntu and no longer showed Windows, and after looking around google for a while, I saw a bunch of sites that suggested using rEFIt, so I downloaded and installed that. Now, when I boot, all three OSes show, but only Mac boots correctly. When I try loading the others with rEFIt, I get a blank screen with plain text that read "No bootable device -- insert boot disk and press any key", but if I insert a bootable CD a hit a random key, nothing happens.
I am pretty sure you need to sync the partition tables. Choose the partition tool in the refit menu

> **Buce said:**
> After googling a bit more, I found [this tutorial]("http://ubuntuforums.org/showthread.php?t=187465") (wish I had seen it before). It includes instructions for backing up the Windows MBR and restoring it at some point during the installation (oops).
I think you are OK still

> **Buce said:**
> It also doesn't include setting up a swap partition, since you're limited to four partitions. Come to think of it, how did the LiveCD even get that 5th one on there, anyway? I thought that wasn't supposed to be possible without using logical partitions, and when I look at it from the System Rescue CD with gparted, it shows up as being primary. because there is no such thing as logical / extended partitions on a GPT formatted disk. You can create like 128 partititons, all primary. The issue is that partitions >4 do not get included in the MBR partition table and that is what Windows and GRUB rely on. (Once the Linux kernel loads, it has support for GPT, so it can see the other partitions.

> **Buce said:**
> So, does anyone have any idea as to how I can get things working? Can I fix the Windows MBR normally with the XP install CD, or do I have to worry about it being a Mac?
I would make sure that you actually need to do something to the MBR first. Did you install GRUB to the Ubuntu partition? 

> **Buce said:**
> Should I reinstall Ubuntu and/or get rid of the swap partition? Or can I reinstall the whole thing under a logical partition? All the data on the computer was backed up before doing the install, but I don't want to have to reinstall Windows or Mac (*especially* Mac) from scratch if I can help it.Answered with above posts.

Please see

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by Buce on 2009-01-18
So, I've now reinstalled Ubuntu without a swap partition on sda3. More below.

> **cyberdork33 said:**
> I am pretty sure you need to sync the partition tables. Choose the partition tool in the refit menu

After doing this, Ubuntu works (thanks!), but not Windows. An error screen comes up with the options to start windows normally, use the last known good configuration, boot in safe mode, etc. I'm guessing that's because I didn't install GRUB to sda3 the first time around. After the second install, I get the same problem...but see below.

>  because there is no such thing as logical / extended partitions on a GPT formatted disk. You can create like 128 partititons, all primary. The issue is that partitions >4 do not get included in the MBR partition table and that is what Windows and GRUB rely on. (Once the Linux kernel loads, it has support for GPT, so it can see the other partitions.

So I could still have swap on a separate partition?

> I would make sure that you actually need to do something to the MBR first. Did you install GRUB to the Ubuntu partition? 

No, I used whatever the default is the first time around. On the second install, I used sda3.

> [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Thanks for the link! After poking around on that site for awhile, I found a suggestion to change boot.ini to use partition 4 instead of 3...and editing that file from Ubuntu worked! All I had to do was choose "Use the last known good configuration" on the error screen that came up after booting. I've only had a cursory look at each of the OSes, but they all seem to boot fine. I'm guessing there'll be hardware issues with Ubuntu, but that's nothing I can't handle...the only thing I'm really worried about is the fact that I didn't install GRUB to sda3 the first time around. Will that cause problems, or did using the last known good configuration fix everything?

Thanks for all the help! I really appreciate it.

---

### Post by cyberdork33 on 2009-01-18
> **Buce said:**
> So I could still have swap on a separate partition?yes, as long as it is partition 5 or higher.

> **Buce said:**
> Thanks for the link! After poking around on that site for awhile, I found a suggestion to change boot.ini to use partition 4 instead of 3...and editing that file from Ubuntu worked! All I had to do was choose "Use the last known good configuration" on the error screen that came up after booting. I've only had a cursory look at each of the OSes, but they all seem to boot fine. I'm guessing there'll be hardware issues with Ubuntu, but that's nothing I can't handle...the only thing I'm really worried about is the fact that I didn't install GRUB to sda3 the first time around. Will that cause problems, or did using the last known good configuration fix everything?
If it works, don't fix it.

---

