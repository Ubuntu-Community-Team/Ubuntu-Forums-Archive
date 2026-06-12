---
title: "Xfce"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by anv on 2007-06-17
couple questions from xfce, I don't have trash, it says all things after deleting are permanently lost. is this normal?

secondly I can't right click create icons on desktop or if I have icons I can't drag select them, I have to collect several files one by one, is this normal?

---

### Post by tippit78 on 2007-06-18
For a trash/recycle bin, you can try [this how to]("http://ubuntuforums.org/showthread.php?t=244900"). Not perfect, and you might be able to google for some better solutions.

And as far as having to collect items one by one on the desktop, that is indeed normal behavior for XFCE.

---

### Post by ugm6hr on 2007-06-18
If you install the full xubuntu-desktop, it will include a Trashcan (a single trashcan in user directory for all deleted files).

And, as stated, drag/select doesn't work in XFCE.  If you want to select multiple files, use Thunar File manager and click on Desktop from there (all files on Desktop are in home/user/Desktop).

As for creating icons on desktop - do you mean change the look of an icon, or drag and drop an icon onto the Desktop?  I think you can drag and drop onto the desktop by dragging to home/user/Desktop, and it should appear.  As for changing the desktop icon - I'm not sure.

---

### Post by anv on 2007-06-21
I stopped it when trying to create .Trash in my homefolder, found out that folder allready exists and I can't see it in Thunar (even show hidden on) I suspect it is remnant from earlier gnome desktop and it blocks system I don't know how to remove this non visible target from my Homefolder

---

### Post by diatribe on 2007-06-21
cd ~/
rm -rf .Trash

---

