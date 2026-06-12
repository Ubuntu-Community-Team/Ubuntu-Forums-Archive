---
title: "Remove WinXP from dual boot"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-12-31
I have two internal hard drives, I'm dual booting with XP on one and Gutsy on the other. I originally used the second drive as XP backup, then put Ubuntu on it and used an external drive for backup.

I've been using Ubuntu for almost a year now, and only had to use XP twice - I reckon I'll soon be ready to get rid of it and use that drive as my Ubuntu backup.

Is the best way to use GParted to overwrite is as ext3? Will Ubuntu then recognise it automatically, or do I have to anything else? I've been searching around but haven't found the exact answer.

TIA

---

### Post by Seti on 2007-12-31
GParted will work for what you want to do. Make sure the partition isn't mounted so that you can do stuff to it, and then you can just delete it or reformat it as you see fit. Of course once this is done you can reboot and Ubuntu will detect the partition and you can put it to use.
Cfdisk is another nice tool for managing your partitions.

Good luck!

---

### Post by (((X))) on 2007-12-31
I used Gparted to remove my XP and Gpartedlive to grow ubuntus ext3.
alwaysWorked  for me.

---

### Post by Sbarton on 2007-12-31
If you have grub installed then GParted Live CD will do what you require, just be sure  that getting rid of XP is what you really want to do! I had a similar setup and decided to install a second copy of 'Gutsy' on the slave drive, and use this as a kind of clone.
regards

---

### Post by eternicode on 2007-12-31
> **Seti said:**
> Of course once this is done you can reboot and Ubuntu will detect the partition and you can put it to use.

Yes, Ubuntu will no doubt detect it, but if the Windows partition was auto-mounted (or if you are combining multiple partitions into one), you will probably need to edit your /etc/fstab file to reflect the changes.

Let us know how it goes :)

---

### Post by freesitebuilder on 2008-01-01
> **Sbarton said:**
> If you have grub installed then GParted Live CD will do what you require, just be sure  that getting rid of XP is what you really want to do! I had a similar setup and decided to install a second copy of 'Gutsy' on the slave drive, and use this as a kind of clone.
regards

What are the advantages of that - are you using it for testing?

---

### Post by BL00dFox on 2008-01-01
Isnt it also a good idea to remove it from the GRUB menu?

---

### Post by Sbarton on 2008-01-01
> **freesitebuilder said:**
> What are the advantages of that - are you using it for testing?
The simple answer is to have a complete backup should things go awry on the Master drive whether that is by accident or breakdown of hardware . However, I have found that it is also useful  when upgrading  to the latest version via synaptic and not necessarily through CD. If things go wrong I have a quick answer, change drives!
I also use 'Grsync' to backup my Home folder on the main drive to a 1gig Pendrive so that it is more or less up to date.
regards

---

### Post by candtalan on 2008-01-01
> **freesitebuilder said:**
> I have two internal hard drives, I'm dual booting with XP on one and Gutsy on the other. I originally used the second drive as XP backup, then put Ubuntu on it and used an external drive for backup.
I've been using Ubuntu for almost a year now, and only had to use XP twice - I reckon I'll soon be ready to get rid of it and use that drive as my Ubuntu backup.
Is the best way to use GParted to overwrite is as ext3? Will Ubuntu then recognise it automatically, or do I have to anything else? I've been searching around but haven't found the exact answer.TIA
I believe the places the ntfs partition appears in your ubuntu is in both the file fstab for mounting and also menu.lst for grub choices. The master drive (your existing ntfs partitoned drive I guess) also contains the boot sector which the mainboard bios uses to get started properly, pointing to the ubuntu partiton I guess. As long as you do not change the (ntfs) partiton name or position, you should be able to delete its contents and reformat as you suggest, leaving the boot sector as it is. It will be best to first remove its reference from fstab (use # to comment out) so you don't have any complications starting up ubuntu if it want to to mount a non existent file system.
good luck.

---

