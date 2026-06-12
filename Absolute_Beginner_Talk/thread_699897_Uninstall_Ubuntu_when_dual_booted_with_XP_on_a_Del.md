---
title: "Uninstall Ubuntu when dual booted with XP on a Dell."
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by spacesearcher on 2008-02-17
Ok so I dual booted Ubuntu with XP on a dell computer and want to uninstall Ubuntu not because I don't like it I love Ubuntu but there are reasons why it must be removed not important here. Anyways, Im running a dell computer that had XP installed on it and a separate partition to recover/reformat. when grub is displayed it has these options

Ubuntu 7.10
Ubuntu 7.10 Recovery Mode
Memory Test
Other OSes:
Windows XP
Dell Utility partition


I tried just deleting the ubuntu partitions the actual os partition and the swap space I think. then gurb had an error so i reinstalled ubuntu and I could boot to XP again. How do I remove Ubuntu and "regrow" the partition with XP on it without using grub. so basically just like it was before Ubuntu was installed?

---

### Post by emarkd on 2008-02-17
You can use gparted on your Ubuntu Live CD to merge the partitions back together, but you'll need to use a Windows CD to reinstall the Windows bootloader.  Can you burn one from the recovery partition?

---

### Post by overdrank on 2008-02-17
> **spacesearcher said:**
> Ok so I dual booted Ubuntu with XP on a dell computer and want to uninstall Ubuntu not because I don't like it I love Ubuntu but there are reasons why it must be removed not important here. Anyways, Im running a dell computer that had XP installed on it and a separate partition to recover/reformat. when grub is displayed it has these options

Ubuntu 7.10
Ubuntu 7.10 Recovery Mode
Memory Test
Other OSes:
Windows XP
Dell Utility partition


I tried just deleting the ubuntu partitions the actual os partition and the swap space I think. then gurb had an error so i reinstalled ubuntu and I could boot to XP again. How do I remove Ubuntu and "regrow" the partition with XP on it without using grub. so basically just like it was before Ubuntu was installed?

Hi and this link will help
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by spacesearcher on 2008-02-17
> **emarkd said:**
> You can use gparted on your Ubuntu Live CD to merge the partitions back together, but you'll need to use a Windows CD to reinstall the Windows bootloader.  Can you burn one from the recovery partition?

Maybe.. I do have an install disk that came from dell, do you know if it is likely that you can just reinstall the windows boot loader and not have to reinstall the whole thing?

---

### Post by emarkd on 2008-02-17
No idea.  Sorry.

---

### Post by iansane on 2008-02-17
not sure but seems to me, if you deleted the ubuntu and swap partitions, you would need to reinstall or rewrite the windows boot loader. When ubuntu installed it overwrote the windows loader with grub so it would need to be rewritten. Can you do that with a windows disc or fixmbr from a bootable floppy? That's where I would start. I would have to go do some research at windows technet or someplace like that though.

---

### Post by spacesearcher on 2008-02-17
> **emarkd said:**
> No idea.  Sorry.

Its okay, just one more question, is this the best order to do this:
1. get the windows boot loader to work
2 run Ubuntu from a live disk and use gparted delete the ubuntu partition and grow the old xp partition

---

### Post by spacesearcher on 2008-02-17
I'm going to try this [http://www.softwaretipsandtricks.com/forum/other-operating-systems/25744-windows-bootloader.html](http://www.softwaretipsandtricks.com/forum/other-operating-systems/25744-windows-bootloader.html)
*crosses fingers*

---

### Post by iansane on 2008-02-17
> **spacesearcher said:**
> Maybe.. I do have an install disk that came from dell, do you know if it is likely that you can just reinstall the windows boot loader and not have to reinstall the whole thing?

Should be a recovery option on the disk that will not do a fresh install over your existing files.  Or a fresh install that saves back up of all your files in folder called windows.old in C drive. Just depends on your system but some of the new systems have that option. 

Hopefully someone knows how to just do the boot loader though. Would be easiest way.

---

### Post by anewguy on 2008-02-17
There is a how-to on Ubuntu forums for removing ubuntu and leaving Windows.  Iw ould suggest you look at it:


[http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")


The easiest way to work with the boot sector is in those instructions - doesn't require a Windows disk of any kind.

:)

---

### Post by spacesearcher on 2008-02-17
> **iansane said:**
> Should be a recovery option on the disk that will not do a fresh install over your existing files.  Or a fresh install that saves back up of all your files in folder called windows.old in C drive. Just depends on your system but some of the new systems have that option. 

Hopefully someone knows how to just do the boot loader though. Would be easiest way.

OK so far I have booted the CD pressed R to go into the recovery thing, selected my partition of windows there was only one option for that. then I could type commands I typed FIXMBR and it gave me a "are you sure" option typed Y pressed enter typed exit pressed enter and it booted to XP without going into grub or anything.
So yay I think we fixed it. Just have to remove the partitions Ubuntu put on my system.

---

