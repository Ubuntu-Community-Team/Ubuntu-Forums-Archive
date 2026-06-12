---
title: "Grub Loader Error 21"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by Spookie71 on 2008-01-07
Hello

I installed Ubuntu on a partition of about 40 Gigs on a USB drive. 

When I reboot my O/S after installing Ubuntu successfully. I get prompted with the Grub Error message Error 21 and my screen freezes.

After working on this issue all night last night I gave up and thought I would try one last attempt today by asking on this forum.

I have enabled USB legacy support in the Bios.

I tried reinstalling the O/S and I've tried putting the boot loader in the correct spot, all failing.

Now I'm reading that I should go back and install the windows boot loader with XP. Well if I have to do that, I'm going back to windows. I don't want to do that but I don't know where to go from here.

Can you please tell me what I need to do or any info I need to post to make grub work.

Thank you
Scott

---

### Post by philinux on 2008-01-07
Grub error 21.

21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

Having a look for a fix.

Super grub disk comes to mind as does reinstalling grub from the live cd.

---

### Post by Spookie71 on 2008-01-07
I have tried to reinstall grub from live CD however it doesn't work

It is installing to a location of Hd0

When I load the live CD partition manager all my drives show up as

Sda1 or Sda2 for example.

Where do I need to install the bootloader, or is that not my issue.

Scott

---

### Post by philinux on 2008-01-07
Ignore what the partition manager is saying you need to follow this for grub.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Spookie71 on 2008-01-07
I think I'm going back to Windows.

I followed what you posted in the last article. followed to the T and everything seemed to be going great. Then I rebooted and go the same Error 21.

If I'm having this much trouble with the boot loader I can only imagine how much trouble there will be with the O/S

Thanks for your help.
Scott

---

