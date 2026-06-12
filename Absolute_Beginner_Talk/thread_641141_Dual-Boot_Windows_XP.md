---
title: "Dual-Boot Windows XP"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by amazingDentist on 2007-12-15
Hi everyone,
I have a copy of windows xp that I want to install.
Is there a way to install it so  that it doesn't overwrite my ubuntu 7.10 OS?
I would like to be able to choose during start-up which OS I want to use.

Thanks for listening.

---

### Post by Jack78 on 2007-12-15
APC has a fairly detailed guide on doing this - [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by autocrosser on 2007-12-15
Take a look at the Tutorials & Tips forum--there is a way to do it--but Windoze won't make it easy.......

---

### Post by amazingDentist on 2007-12-15
Nice.  Thanks for the link.
I apologize for being so un-resourceful and posting noob questions. :)  It's late and I'm a few apple rums on my way... \\:D/

---

### Post by SgtDude on 2007-12-15
Unless you're installing to a seperate HD (i.e. not touching your ubuntu install), No.

Microsoft is under the impression that anyone installing windows a machine obviously wants all those other non-windows OS's wiped out, and the installer will happily do that for you.

Well, it doesn't just wipe your drive, but during the installer, any linux partitions will be seen as "unknown format" or "raw", I can't remember.  The windows installer won't let you resize those partitions, you'll have to work around them or delete them.

Your biggest concern, though, is that the windows installer will re-write your MBR on your first HD.  Windows has it's own bootloader that will replace grub, and it won't ask you if that's what you want to do or warn you that it's about to do it.

The best way to get Windows and Linux on a single HD is to load Windows first, then Linux (Linux is much friendlier than Windows, and won't try to kill Windows while installing).

I think the best solution to your problem is probably to backup your files, install Windows, install Ubuntu, and then restore your files.

Sorry this isn't the answer you hoped for.  I suppose you could install Windows in some free space on your HD, and then try to re-install grub manually, but I have no idea how to do that, so I can't help you there.

Sorry for being so long-winded...

---

### Post by amazingDentist on 2007-12-15
That's what I'm doing ATM actually.
Windows XP is going to replace everything, and then I'll install Ubuntu again via live disc install.
Seems like a better idea, based on what i'm reading. :rolleyes:

Much Obliged.
Happy Friday.

---

### Post by siciliancasanova on 2007-12-15
> **amazingDentist said:**
> That's what I'm doing ATM actually.
Windows XP is going to replace everything, and then I'll install Ubuntu again via live disc install.
Seems like a better idea, based on what i'm reading. :rolleyes:

Much Obliged.
Happy Friday.

Agreed.  In the end most likely you will save time and a potential amassing of problems.

---

