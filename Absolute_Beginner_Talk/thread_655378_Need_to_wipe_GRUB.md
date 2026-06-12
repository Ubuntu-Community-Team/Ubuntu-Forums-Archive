---
title: "Need to wipe GRUB"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Jademalo on 2008-01-01
Ok. so how can i get rid of grub w/o formatting my disk? linux wont install for some reason..

---

### Post by taurus on 2008-01-01
Try the Super GRUB Disk.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by logos34 on 2008-01-01
> **Jademalo said:**
> Ok. so how can i get rid of grub w/o formatting my disk? linux wont install for some reason..

To erase grub from the MBR:

**dd if=/dev/zero of=/dev/hda bs=446 count=1**

What exactly is the problem/error message you get during install?  'Fatal error'?

EDIT: or use the SGD like taurus suggested.  'Uninstall grub' option

---

### Post by meindian523 on 2008-01-01
That's potentially dangerous if even a slight variation is made.

It's preferable to use the SGD.Or maybe use the Windows disk to fixmbr if there exists a Windows installation on the HDD.

---

### Post by Bruce M. on 2008-01-01
> **Jademalo said:**
> Ok. so how can i get rid of grub w/o formatting my disk? linux wont install for some reason..

A little more information would have been good.
But I'm going to assume you have Windows as a second OS.

1.  Boot from your Windows CD, and go for the "Recovery Mode" option ( I don't recall the exact wording)

2.  When at the prompt type:

```

fixmbr

```

fixmbr: **FIX** **M**aster **B**oot **R**ecord

That will delete GRUB and your options from this point on are Windows related.

Continue to "recover" Windows, or cancel at this point, remove the CD and Reboot.  You should be fine.

Optionally if you have a DOS boot floppy, the fixmbr command is there too.

Happy New Year
Bruce

---

