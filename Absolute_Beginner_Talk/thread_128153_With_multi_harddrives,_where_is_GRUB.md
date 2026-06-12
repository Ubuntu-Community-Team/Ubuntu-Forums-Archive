---
title: "With multi harddrives, where is GRUB?"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by poiuytr on 2006-02-10
This may sound like a silly question, but I have a multiple harddrive desktop machine, with several Linux Operating Systems on the different drives.  Each has its own GRUB and menu.lst.

How does my computer "know" which GRUB to use?  

Is it a question of order of precedence in the BIOS (e.g. some setting which says basically, "Boot from Drive 1, and if that is not possible then boot from Drive 2...etc)?

Or...?

---

### Post by RaptorRaider on 2006-02-10
[QUOTE=poiuytr]Is it a question of order of precedence in the BIOS (e.g. some setting which says basically, "Boot from Drive 1, and if that is not possible then boot from Drive 2...etc)?[/QUOTE]
Yes, that's it I believe.

---

### Post by GargoyleMusic on 2006-02-10
I believe the Ubuntu install will detect all other hard drives, partitions, operating systems, etc. It will then prompt you and ask whether or not you want to write to the master boot record of the drive you're installing it to.

On my computer, then, I had to set the bios to boot from my Ubuntu hard drive (in this case, I set it to boot from my slave drive, instead of the master). Ubuntu should have configured grub to give you a menu and then boot whichever OS you want - but it must boot from the hard drive that Ubuntu has created the menus for.

Hope that helps (and that I'm not off the mark!)

---

### Post by skirkpatrick on 2006-02-10
Nope, you're on it.  The BIOS will boot GRUB from whichever drive you have selected as the boot drive.  Normally, it's the master drive on the primary cable.

---

