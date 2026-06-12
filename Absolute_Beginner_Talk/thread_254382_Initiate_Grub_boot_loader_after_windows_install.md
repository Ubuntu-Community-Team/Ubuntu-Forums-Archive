---
title: "Initiate Grub boot loader after windows install"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Xanthus on 2006-09-09
I Installed Kubuntu the other day and to do so I trashed my Windows partition and repartitioned the table.  I have a 250GB HDD and I have a 175 partition allocated for windows, then a 20-some GB partition for Kubuntu, and a 37ish BG partition. I don't know what happened to the rest of it but this is not the problem.  My problem is that I used the 175 as the swap and I used the 20 for the ext3 Kubuntu.  The install went fine, I then went and installed windows on the 175 a day or so later, yesterday, and now I have no idea how to boot to the linux!!! Help me out!!! oh yeah, and was deleting the swap a bad idea?

-XanthusX

---

### Post by jordanmthomas on 2006-09-09
Deleting the swap was a bad idea.  At least for me it would be.  I need my swap pretty often.

Anyway, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) will get your grub back.

Deleting your swap partition will also make Ubuntu complain at boot.
In /etc/fstab, you will need to comment out the line referring to linux-swap.

---

### Post by msandersen on 2006-09-09
Always carefully plan out how you want to partition a disk, and be careful when installing any OS. Swap should be 1-1.5 times the amount of RAM, eg if you have 1Gb RAM, set aside 1 to 1.5Gb Swap space. I don't think it is critical to the operation of Linux to have it, but it is recommended at least.
I think the LiveCD has gParted so you can check out where all the space is, otherwise go to Windows Disk Management. If you have a good Windows partitioner like Partition Magic, you can use that to fix up any unallocated space and a Swap partition. It is far better than gParted. I always use that to partition the disk first before installing Linux.
It's worth reading one of the Getting Started guides on installation. For instance, it is also advisable to have a separate Home partition simply so that you can trash you System without affecting your personal files. You already found out why it is recommended to install Windows before Linux, namely because Windows won't recognise anything but Windows when setting up its bootloader.

---

### Post by Xanthus on 2006-09-10
I trashed both of the installs and reinstalled windows then linux so the boot loader is working and the 37GB partition is the one that has my personal files on so I don't lose them.  Thanks for the link because what I previously failed to mention is that this is on one of my HDDs, the other has 2 partitions, one for backup and the other runs windows, which needs to be reinstalled.

---

