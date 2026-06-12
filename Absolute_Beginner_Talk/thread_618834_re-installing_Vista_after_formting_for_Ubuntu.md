---
title: "re-installing Vista after formting for Ubuntu"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by niallabrown on 2007-11-20
Sorry if this has been covered.  I'm visually impaired and cant search easily.

I have a computer with Vista on the harddrive.  I tried to install Ubuntu on an external hard drive assuming it would just put an entry in grub with Vista.  It messed things up.  I then formated the main hardrive and installed Ubuntu and was happy for a time.  I now need my vista install but when I recover from HP backup disks it says: BOOTMGR is missing

How do I fix this?

---

### Post by MegaJim on 2007-11-20
This might be failing because some special bootcode placed in the MBR by the manufacturer is needed to trigger the recovery discs to install vista.  Another possibility is that the discs are not really used but instead there was a "Ghost" partition for recovery purposes which Ubuntu may well have overwritten.

If you tell us the exact model of your laptop, somebody will be more than willing to give you detailed help.

---

### Post by niallabrown on 2007-11-20
Its actually a Desktop.  HP Pavilion a1730n.  It did have a recovery partition and I think your right that it did get overwritten, but I am installing off recovery CD's.  I don't know if that would still effect it?

CORRECTION: I have installed vista from the CD's and removed them.  When Vista tries to start for the first time it says: BOOTMGR is missing

---

### Post by MegaJim on 2007-11-20
Ah just saw your correction.  Ok then that is a completely different issue :)

---

### Post by MegaJim on 2007-11-20
This thread talks about a similar issue [http://ubuntuforums.org/showthread.php?t=319814](http://ubuntuforums.org/showthread.php?t=319814)

---

### Post by niallabrown on 2007-11-20
Yep, I think your right.  The answer is there.  Thanks! I'll give some of the suggestions a try.

---

