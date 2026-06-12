---
title: "Can't boot from hard disk"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-04-06
I had three partitions. The first one had Ubuntu, the second one had OpenSuSE, and the third one had Windows XP. My bootloader then was OpenSuSE's GRUB.

I reformatted the second partition (it deleted OpenSuSE), and moved my Ubuntu home partition there.

When I rebooted, I cannot boot from hard disk. That happened to me before. What I did before was to start with a Linux live CD and select from there the option to boot from hard disk. It worked before but it did not work this time.

When I booted from the hard disk by choosing it from the live CD's first options, it said that there was something wrong with the partition table. 

Now, I do not have a /boot/grub/menu.lst, for some reason.

How can I fix GRUB?

---

### Post by mac.ryan on 2007-04-06
Try to reinstall Grub from the scratch, so that the MBR will point to a freshly installed /boot/grub on your ubuntu partition.

You can do it via the SuperGrub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Best luck!

---

### Post by overdrank on 2007-04-06
> **wersdaluv said:**
> I had three partitions. The first one had Ubuntu, the second one had OpenSuSE, and the third one had Windows XP. My bootloader then was OpenSuSE's GRUB.

I reformatted the second partition (it deleted OpenSuSE), and moved my Ubuntu home partition there.

When I rebooted, I cannot boot from hard disk. That happened to me before. What I did before was to start with a Linux live CD and select from there the option to boot from hard disk. It worked before but it did not work this time.

When I booted from the hard disk by choosing it from the live CD's first options, it said that there was something wrong with the partition table. 

Now, I do not have a /boot/grub/menu.lst, for some reason.

How can I fix GRUB?

Hi this thread helped me with the grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck!

---

### Post by wersdaluv on 2007-04-06
I installed Ubuntu to a new partition.

When I rebooted, I still was not able to boot from hard disk. I had to use the Ubuntu Live CD and choose the boot from first hard disk option. For some reason, it worked.

How do I boot from hard disk without the Ubuntu Live CD?

---

### Post by mac.ryan on 2007-04-06
> **wersdaluv said:**
> How do I boot from hard disk without the Ubuntu Live CD?

Follow either of the two suggested methods above. Probably the second one will now work (I am not sure it would have before, due to the lack of /boot/grub directory at the time of your first post). The second method looks like quicker and simpler than the first one.

---

### Post by wersdaluv on 2007-04-06
I tried to restore GRUB, but it still did not work. I still need the Live CD for me to boot from hard disk.

---

### Post by mac.ryan on 2007-04-06
What procedure did you try? What was the outcome (what did it go wrong with that)?

Also, what does exactly happen if you try to boot your system normally (i.e. without LiveCD)? What is the error message you get?

---

### Post by zvacet on 2007-04-06
[http://ubuntuforums.org/showthread.php?t=401472]("http://ubuntuforums.org/showthread.php?t=401472")

---

### Post by mtdewulf on 2007-11-07
I'm having the same issue.  I don't get anything when I boot without a cd in the drive.  Nothing.

When I put the ubuntu disk in the drive, i can chose to boot from the first hard disk and then things work.  I think this works with the vista install disk too - if I don't press anything to boot from cd then i'll boot normally.  However, no disk -> no boot and no warning message.

---

### Post by mtdewulf on 2007-11-07
Hmm.  OK. So I have a foxconn motherboard (suspect this was the issue - silently failing when it did not find a boot device).  I pressed escape when booting and the choose hard-disk, then the first disk.  I suspect it was not looking at the correct disk for the boot record.  Hope this helps others.  Anyway, I'm not sure if this is what did it, but now it works.

---

