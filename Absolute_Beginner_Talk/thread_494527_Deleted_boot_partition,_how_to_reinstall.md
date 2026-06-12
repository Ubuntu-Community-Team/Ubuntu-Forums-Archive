---
title: "Deleted boot partition, how to reinstall?"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by SoCalChris on 2007-07-07
I had a dual boot system with XP & Feisty. I was running out of space on my linux partition, and don't use Windows any more, so I deleted Windows, and reorganized the partitions. 

This is how the drives were partitioned
```
/dev/sda1 - NTFS
/dev/sda2 - swap
/dev/sda3 - /
/dev/sda4 - /boot
```

I deleted sda1 and sda4, created a new boot partition at sda1, and grew sda3 to fill the remaining space.

This is how my drive is now
```
/dev/sda1 - /boot
/dev/sda2 - swap
/dev/sda3 - /
```

My files are still on sda3, but I'm unable to repair GRUB. Any suggestions? I have a feeling that my kernal image was on the old /dev/sda4, and are gone now. I have a copy of GRUB SuperDisk, but I'm unsure how to use it for what I need. I also have an Ubuntu live cd an alternate install cd, but haven't had luck getting them to repair my boot partition.

Any suggestions would be greatly appreciated!

---

### Post by mikeyphi on 2007-07-07
I guess that when you wiped Windoze you wiped the Master Boot Record!!
Use the alternate install CD with the text mode installer: choose the option to rescue a broken system line.
You will have to reinstall Grub on /dev/sda

---

### Post by ugm6hr on 2007-07-07
Is there a good reason to have a /boot partition?

I thought GRUB would live happily within the / partition (for Ubuntu).

---

### Post by louieb on 2007-07-07
Hello SoCalChris, I got to say this is a new one. When you deleted the old /boot partition you got rid of a bunch of important stuff like the GRUB program and the Ubuntu Linux kernel(s). (I see you guessed that one).  Plus by moving the /boot partition, now the GRUB pointer in the drives MBR is no longer valid.  

I think your looking at reinstall. If you had a separate /home partition then a reinstall would be fairly  painless. At  this point your just going to have to copy off your data, reinstall Ubuntu and copy your data back.

Just for future reference. Here is a partitioning scheme that I use. [LIST]
[*]/ (root) 5-7 gig.
[*]a second 5-7 gig partition for use to try out a second distro or in a few months Gutsy will be coming out and you could put it here and not worry about messing up you current Ubuntu install.
[*]swap
[*]/home Rest of the drive.[/LIST]I don't use a separate /boot partition. Unless you have a flaky BIOS its more trouble than its worth.

Good luck. I bet you get it figured out.

---

### Post by dptxp on 2007-07-07
> **louieb said:**
> Hello SoCalChris, I got to say this is a new one. When you deleted the old /boot partition you got rid of a bunch of important stuff like the GRUB program and the Ubuntu Linux kernel(s). (I see you guessed that one).  Plus by moving the /boot partition, now the GRUB pointer in the drives MBR is no longer valid.  

I think your looking at reinstall. If you had a separate /home partition then a reinstall would be fairly  painless. At  this point your just going to have to copy off your data, reinstall Ubuntu and copy your data back.

Just for future reference. Here is a partitioning scheme that I use. [LIST]
[*]/ (root) 5-7 gig.
[*]a second 5-7 gig partition for use to try out a second distro or in a few months Gutsy will be coming out and you could put it here and not worry about messing up you current Ubuntu install.
[*]swap
[*]/home Rest of the drive.[/LIST]I don't use a separate /boot partition. Unless you have a flaky BIOS its more trouble than its worth.

Good luck. I bet you get it figured out.


Very nice way to partition. I use similar, but I keep SWAP at the end.

---

### Post by SoCalChris on 2007-07-07
Thanks for the suggestions.

I have a seperate boot partition because I'm using XFS on my root partition, and the installer warned me that GRUB would likely hang if installed on a partition that was XFS.

I tried copying the boot partition from our other computer, and chrooting into the system to try and upgrade the kernel images, but that didn't work either. 

I wound up just backing up my home directory, reinstalling, and then restoring the home directory.

Thanks for everyone's replies.

---

