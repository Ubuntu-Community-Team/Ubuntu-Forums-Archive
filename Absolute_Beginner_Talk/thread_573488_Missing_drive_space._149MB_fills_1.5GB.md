---
title: "Missing drive space. 149MB fills 1.5GB?"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by e_james on 2007-10-11
I am working on an elderly PC (ubuntu Edgy) with one hdd partitioned as 3.9GB "/", 500MB "swap" and 1.6GB "/home". Gparted and System Monitor now agree that there is about 83KB free space in the /home partition, but Nautilus says that it contains 642 items totaling 149MB and 0 free space. Has anybody got any suggestions where the 1.4GB discrepancy comes from?

As far as I can tell there are no relevant hidden files or files not deleted.

~$ sudo fdisk -l

Disk /dev/hda: 6480 MB, 6480101376 bytes
255 heads, 63 sectors/track, 787 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         510     4096543+  83  Linux
/dev/hda2             511         787     2225002+   5  Extended
/dev/hda5             511         574      514048+  82  Linux swap / Solaris
/dev/hda6             575         787     1710891   83  Linux


~$ df -H
Filesystem             Size Used Avail Use% Mounted on
/dev/hda1              4.2G   2.4G   1.6G  61% /
varrun                 123M    95k   123M   1% /var/run
varlock                123M      0   123M   0% /var/lock
procbususb              11M   119k    11M   2% /proc/bus/usb
udev                    11M   119k    11M   2% /dev
devshm                 123M      0   123M   0% /dev/shm
/dev/hda6              1.7G   1.6G      0 100% /home

I recall checking for free space about a month ago and I think there was at least 800MB at that time.

---

### Post by steve.horsley on 2007-10-11
I think nautilus doesn't count files in subdirectories unless you right-click a folder and choose Properties. Trust df, and also see **man du**.

---

### Post by ryanVickers on 2007-10-11
Thunar, Dolphin, nautilus, system monitor, commands, and anything else you can think of tend to all give different numbers - I would trust a well-put together command... (but, when you've got a 300Gb HD, a 5GB discrepancy doesn't really matter ;))

---

### Post by ajgreeny on 2007-10-11
Try filelight to see where all your space is being used up.  I once had a load of big files in root's trash after messing up a copy of my /home folder from another partition which I did in the wrong direction and ended up with wrong permissions, (but that's another story).  That was before I was aware I could change permissions.

There was about 29 GB missing after I had got rid of that useless version of /home, and only after looking in filelight did I find out where it had been used up and manage to clear it out.  Could that be your problem?

---

### Post by ryanVickers on 2007-10-11
Another idea, if it's a small and reasonable fast drive (or if you have a lot of spare time ;)), try using the "Disk Usage Analyzer" Tool and scan the whole drive...

---

### Post by e_james on 2007-10-11
ajgreeny

Thanks for the suggestion of filelight. Unfortunately the PC in question is inaccessible for a few hours at least, but I have tried out filelight on my laptop and it's impressive. I could have used something like that many times before.

In the meantime I have had another thought. If the drive in question was going bad and had recently developed a lot of bad sectors, what would linux do about it? Is it possible that the bad sectors would appear to be used space but with no files?

---

### Post by e_james on 2007-10-17
Having replaced the offending hard drive and attempted to recover files from it, I am now 99% convinced that the situation was caused by 2 things.

1. The drive was failing progressively. More and more sectors were going bad.

2. Linux and / or ubuntu was quietly diagnosing the faulty sectors and removing them from use. There were no error messages and the only clues, apart from the reduction in available space, were apparent instability in some applications i.e. occasional unexpected crashes.

Is there a diagnostic procedure which would draw this situation to the user's attention before it's too late to act on it?

---

