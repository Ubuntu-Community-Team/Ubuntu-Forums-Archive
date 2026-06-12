---
title: "Ubuntu Dual Boot problem"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by honestaitch on 2008-01-27
I had a problem with my Windows XP Home PC. I think it was a boot sector virus.
As I had a spare hard drive, I installed this new drive as the primary disk, and put the old drive in as a slave.
I then booted Ubuntu (feisty) from the installation CD.
Next I partitioned the new disk into three areas. One FAT partition where I would be able to re-install Windows, one for Ubuntu, and lastly one for paging. I then installed Ubuntu and this worked fine, and even managed to install the necessary drivers to set up a wireless network, enabling me to connect to the internet.

I then installed Windows onto the first partition, and this is when my problems started.
The Windows installation worked fine, but it appears to have overwritten the boot sector with its own as I cannot boot Ubuntu anymore. I had tried rebooting from the Ubuntu CD (which works fine) and changing the partition flags, but this results in the PC reboot failing as it is unable to find a system boot disk.
If I change the first partition back to have a boot flag, I can then reboot Windows.

Any ideas as to what I can try now?  Will I have to re-install Ubuntu to set up a dual boot environment ?
I would prefer to not do this, as I will have to go through the reinstallation of various drivers for my wireless card, printer, etc.

---

### Post by Ub1476 on 2008-01-27
[Super Grub Disk]("http://supergrub.forjamari.linex.org/") can restore Grub for you.

---

### Post by Infinity-al on 2008-01-27
> **honestaitch said:**
> I had a problem with my Windows XP Home PC. I think it was a boot sector virus.
As I had a spare hard drive, I installed this new drive as the primary disk, and put the old drive in as a slave.
I then booted Ubuntu (feisty) from the installation CD.
Next I partitioned the new disk into three areas. One FAT partition where I would be able to re-install Windows, one for Ubuntu, and lastly one for paging. I then installed Ubuntu and this worked fine, and even managed to install the necessary drivers to set up a wireless network, enabling me to connect to the internet.

I then installed Windows onto the first partition, and this is when my problems started.
The Windows installation worked fine, but it appears to have overwritten the boot sector with its own as I cannot boot Ubuntu anymore. I had tried rebooting from the Ubuntu CD (which works fine) and changing the partition flags, but this results in the PC reboot failing as it is unable to find a system boot disk.
If I change the first partition back to have a boot flag, I can then reboot Windows.

Any ideas as to what I can try now?  Will I have to re-install Ubuntu to set up a dual boot environment ?
I would prefer to not do this, as I will have to go through the reinstallation of various drivers for my wireless card, printer, etc.
looks like you have to reinstall grub loader...

this should help [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by rkd on 2008-01-27
If you don't want to learn the new stuff the others pointed you to, you could simply install Ubuntu again.

You probably didn't read the advice that said if you are going to install both Ubuntu and Windows onto a new disk, you should install Windows first. Windows doesn't know about dual booting, so it doesn't notice that Ubuntu is already there.

Your Ubuntu system is still there, and you could fix things with those other steps, but since you just installed Ubuntu, you won't lose anything by installing it again, and that might be the simplest solution for you.

---

### Post by honestaitch on 2008-01-27
Thanks to everyone who replied ... I was surprised (but pleased) at how quickly people responded.
The instructions that Infinity-al  gave me worked first time and I got dual boot working again in 5 minutes (the other suggestions may have worked as well, but Infinity-al's was the first one I tried).

Thanks again,
H

---

