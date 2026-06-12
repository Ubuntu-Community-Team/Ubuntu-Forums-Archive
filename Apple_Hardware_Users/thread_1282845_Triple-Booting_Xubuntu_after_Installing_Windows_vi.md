---
title: "Triple-Booting Xubuntu after Installing Windows via BootCamp"
date: 2009-10-04
forum: Apple Hardware Users
---

### Post by Sniipeh on 2009-10-04
I have Mac OSX 10.5.8 and Windows XP running on my laptop.  OSX is allowed 80GB on my hard drive and XP is allowed 30.  I made the mistake of installing XP via BootCamp and now I want to triple-boot with Xubuntu 9.04 natively.  I will give Xubuntu 10GB,  but obviously I can only have two partitions with BootCamp.  I've been looking around and can't seem to find a definitive solution to install Xubuntu without having to get rid of the XP partition, and I also want some expert advice before I take the risk of messing up my partitions.  So: How can I safely create a third partition and install Xubuntu (I have the live CD) without having to restore my partitions?  I do have rEFIt, by the way, but I'm not sure how that will help.  I just installed it too (with the two partitions present), which I hope won't mess up the process further.

Thanks for the advice.

---

### Post by Lars Noodén on 2009-10-05
I can't / won't say anything about Windows.

However, I've triple (quad) booted OS X, Kubuntu (one or more versions) and OpenBSD using rEFIt.  

As usual, back everything up first.  

You can get rEFIt at Sourceforge:
   [http://refit.sourceforge.net/](http://refit.sourceforge.net/)

---

### Post by WuIsMe on 2009-10-28
Well I've gone ahead early and tried it(with ubuntu rather than Xu). What has happened is that where previously windows loaded without any problems, it now starts up on grub, and from there I have to choose to load windows.

**Windows Doesn't load**
giving the error : /system32/hal.dll is missing or corrupt

I searched around, and tried changing the boot.ini file, so that instead of going to partition2 it went to 3. This looked a little more promising, since the xp logo came up, however it consistently went into BSOD seconds later.

Mac still works fine tho.

In short we're in the same boat hahaa and i haven't yet found a solution to this.
Don't install unless you wanna bugger up your Windows Partition.

---

### Post by sebovzeoueb on 2009-10-29
Not sure about configuring the triple boot after using bootcamp, however from my trial and error successful triple boot ([http://ubuntuforums.org/showthread.php?t=1303459](http://ubuntuforums.org/showthread.php?t=1303459)) I have managed to acertain the following which may be of some help:

-rEFIt is uneccesary (as it seems to bring up GRUB when booting Windows or Linux, same as if you hold down [alt] and select Windows partition).

-Windows must be the 4th partition on your hard drive (including the small EFI partition before OS X), so you should have the following: 

1: EFI 
2: OS X
3: Linux
4: Windows
5: Linux Swap (may not be needed)

-so I THINK (not know) that if you split your OS X partition without moving the Windows one at all you should be OK, but not 100% sure, as I just scrapped my previous bootcamp install when setting up my triple boot. My experiences have been similar to WuIsMe, with Windows struggling to deal with a new setup, but OS X managing fine.

By the way, my advice constitutes noob advice, not expert advice, so you may want to get confirmation before going ahead.

---

### Post by pizzacake on 2009-10-29
> **WuIsMe said:**
> Windows Doesn't load[/B]
giving the error : /system32/hal.dll is missing or corrupt


There are two errors I've found when installing/running Windows XP due to bugs on the windows side

disk error:
using partitions greater than 30GB during installation causes the installer to fail on reboot

hal error:
windows doesn't like the partitions following its own.  Say XP is on partition 3 remove any later partitions if possible.

---

