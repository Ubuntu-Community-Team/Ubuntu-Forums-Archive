---
title: "Can you remove GRUB without the Windows CD?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by twoseids on 2007-01-15
Hi everyone,

I'm prepping an old laptop to give to a friend, and am removing Ubuntu so they will just have Windows (I know, I know, save the Ubuntu ambassador talk!). I successfully removed the Linux partitions with Windows Disk Management, and now need to remove GRUB.

But here's the problem - the CD drive on this computer is entirely inoperable. And it seems the primary way to remove GRUB is to use the Windows disk and go in recovery mode.

Is there an alternate way of doing it that doesn't require the CD? I fear I may have screwed up the job and made the entire computer inoperable.

P.S. The USB drive is operable 50% of the time, so I suppose I could try booting to a flash drive, if there is a fix for it there.

---

### Post by BarfBag on 2007-01-15
You shouldn't have deleted the Linux partitions.  There's no way to clear it from the bios, so you're pretty much screwed.  Can you easily replace the CD drive (there's usually a small button that pops the entire drive out)?  Once you do that, Google around for MBR clearing tools.  My Dad used one when he switched back to Windows.  Neither of us can remember what it was called.

Edit - here's another suggestion.  Do you still have the Windows CD?  See if you can replace the CD drive and then reformat the entire drive with Windows.  This will clear the MBR and give you a fresh install.

---

### Post by mahiyar on 2007-01-15
Somewhere on the windows site is a download available for floppies, google it and download, could be here [http://support.microsoft.com/kb/310994/](http://support.microsoft.com/kb/310994/)

---

### Post by clint1010 on 2007-01-15
Your friend may well want a CD drive, if there is no other way of transfering data in and out (other than LAN). You might be better off finding a new/secondhand drive and hitting the HDD with a squeegy, (format and re-install MS win from scratch).

---

### Post by twoseids on 2007-01-15
Sounds like I'm screwed unless I wanna get a new CD drive. Fortunately, for a 5-year-old Inspiron 4100, that's only like $25 including shipping (on eBay). I'll just see if my friend cares that much about it.

Thanks for your input!

---

### Post by twoseids on 2007-01-15
Sounds like I'm screwed unless I wanna get a new CD drive. Fortunately, for a 5-year-old Inspiron 4100, that's only like $25 including shipping (on eBay). I'll just see if my friend cares that much about it.

Thanks for your input!

---

### Post by louieb on 2007-01-15
[http://bootdisk.com/](http://bootdisk.com/) if it has a floppy drive.

---

### Post by Ocxic on 2007-01-15
ms-dos boot disk made form the ad/remove aplications utility, in the control panel(i think it's there), or search window shelp for startup disk or floppy.

---

### Post by steve.horsley on 2007-01-15
Do you get a useable grub prompt after the error message? If so, you can probably still boot windows with commands like this:
[B]root            (hd0,1)
chainloader     +1[/B]
and then there might be a windws command something like **fdisk /mbr**, but check this out first of course.

---

### Post by twoseids on 2007-01-16
> **steve.horsley said:**
> Do you get a useable grub prompt after the error message? If so, you can probably still boot windows with commands like this:
[B]root            (hd0,1)
chainloader     +1[/B]
and then there might be a windws command something like **fdisk /mbr**, but check this out first of course.
No, no prompt. Just Error 22 (if I remember right) and I have to shut down or reboot.

---

### Post by bodhi.zazen on 2007-01-16
here is a how-to on how to make a grub floppy:

[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

You can make a floppy and then boot with the floppy.

See also supergrub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

