---
title: "Unhiding a partition."
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Dylan H on 2008-01-20
How would I go about unhiding a partition in Linux? There is a hidden 10GB partition that came with my Acer Aspire 5315 that I would love to use to restore Windows Vista. In short: I want to boot from this hidden partition. You're supposed to be able to use alt+F10 during the boot screen, but Ubuntu messed that up. Help appreciated.

---

### Post by Dylan H on 2008-01-20
Bumpety-bump.

---

### Post by thelatinist on 2008-01-20
> **Dylan H said:**
> How would I go about unhiding a partition in Linux? There is a hidden 10GB partition that came with my Acer Aspire 5315 that I would love to use to restore Windows Vista. In short: I want to boot from this hidden partition. You're supposed to be able to use alt+F10 during the boot screen, but Ubuntu messed that up. Help appreciated.

```
sudo fdisk -l
```

Will show all of your installed partitions.  Post the output here and I'll see if we can help.  But I thought you wanted to install XP?

Personally I doubt that this restore partition is actually bootable.

---

### Post by rosegarden78 on 2008-01-20
**This post could be related to an Ubuntu bug filed at**: b [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The beauty of these OS is nothing is impossible.  Unless your partition uses a proprietary file format called NTFS from the Northwest United States.  The company who faces a second class action lawsuit doesn't like to share standards.  But if the partition is FAT32 is should be recognized automatically.  Unless the disc is damaged or corrupted.

EDIT: ABC and WorldWinner may use OS-sniffing to block Linux users so there are some reasons to keep a dual-boot Windows or Mac.

You can still read NTFS but not write.  You may consider researching how to mount and unmount storage devices and disk drives.
The drives are not hidden but reside in two possible places or more

/etc/fstab
/etc/mtab

Once you have the device number (usually sda# or sdb#) you type
sudo mkdir /media/yourMountPoint  (to create a mount point)
sudo mount /dev/sda2 /media/yourMountPoint (to mount it)

---

### Post by dummyhead3 on 2008-01-20
I got he same PC as you (bought at Wal-Mart lol), and according to GRUB, there is a copy of windows XP, invisible from Windows Vista. I never tied it, I'm kinda scared.

---

### Post by Dylan H on 2008-01-21
I wanted to install XP until I found out about this hidden partition. 

Here you go, and thanks for your help.

dylan@dylan-laptop:~$ sudo fdisk -l
[sudo] password for dylan:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56f68711

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 249 MB, 249822720 bytes
4 heads, 8 sectors/track, 15247 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0x1793ba13

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15005      240075+   b  W95 FAT32

---

### Post by thelatinist on 2008-01-21
Sorry, there's no partition there.  Your entire hard drive was formatted by the Ubuntu install CD.  Any partition that was originally hidden there was erased.

---

### Post by Dylan H on 2008-01-21
Well I am thouroughly DISAPPOINTED in Ubuntu.

---

### Post by mcduck on 2008-01-21
> **Dylan H said:**
> Well I am thouroughly DISAPPOINTED in Ubuntu.

If you select the 'Use entire disk for Ubuntu' during install, that's what you'll get. It's no use blaming others because of it.

---

### Post by thelatinist on 2008-01-21
> **Dylan H said:**
> Well I am thouroughly DISAPPOINTED in Ubuntu.

Dude, you told the Ubuntu install CD to use the entire disk.  Isn't it your responsibility to make sure there's nothing important on there that you don't want to install Ubuntu over?

---

### Post by Dylan H on 2008-01-21
Woah there, I never told it to use the entire disk. I am positive. And then why does it say my HD has only 70GB when I know for a fact that it is 80? I'm just getting recovery cds from acer. Bye.

---

### Post by thelatinist on 2008-01-21
> **Dylan H said:**
> Woah there, I never told it to use the entire disk. I am positive.

Ubuntu would only have written over your hard drive if you chose the option "Guided - use entire disk" at installation, I promise you that.  I'm sorry.: you may not have meant to, but you did.

> And then why does it say my HD has only 70GB when I know for a fact that it is 80?

It says, "Disk /dev/sda: 80.0 GB, 80026361856 bytes"

---

### Post by jpangamarca on 2008-01-22
> **Dylan H said:**
> Well I am thouroughly DISAPPOINTED in Ubuntu.

You did not read carefully the install instructions. Sorry my friend, it's not Ubuntu's fault.

---

### Post by rosegarden78 on 2008-01-26
On behalf of myself and community we feel badly for your recent data loss.  When using Windows or Ubuntu installation discs it's important to have a thorough understanding of hard disk partitions.  Although the instruction at Step 4 seem clear to a veteran user, I was stumped at first because I didn't know the "/" was a file system or to avoid extended partitions.  This happened to me once in XP by mistake when I meant to select Repair instead of Install.  We encourage you to obtain external USB storage or make backup discs of your /home folder.  This is the best way to avoid future data loss.

---

