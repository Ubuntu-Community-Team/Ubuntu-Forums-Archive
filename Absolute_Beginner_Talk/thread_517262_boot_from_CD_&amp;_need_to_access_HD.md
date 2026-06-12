---
title: "boot from CD &amp; need to access HD"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-08-04
I'm trying to boot from my 6.10 installation CD & access my Ubuntu drive.
From reading the posts it looks like I need the Live CD but I would think there would be a way to do it from the terminal. I had Edgy working fine dual booting until I messed with grub after a Windows upgrade to XP.  Now I cant get back into my Ubuntu files to try any edits.  I've already tried to do the stage1 edit to no avail. The grub screen will get to XP but not to Ubuntu.

---

### Post by overdrank on 2007-08-04
> **garyed said:**
> I'm trying to boot from my 6.10 installation CD & access my Ubuntu drive.
From reading the posts it looks like I need the Live CD but I would think there would be a way to do it from the terminal. I had Edgy working fine dual booting until I messed with grub after a Windows upgrade to XP.  Now I cant get back into my Ubuntu files to try any edits.  I've already tried to do the stage1 edit to no avail. The grub screen will get to XP but not to Ubuntu.

HI you can reinstall the grub using this "how to"
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by agds on 2007-08-04
If you prefer to just edit your existing grub config, you might try the following.  Assuming your Ubuntu partition is formatted as ext3, you should be able to open a terminal while running the Live CD and enter

```
sudo mount -t ext3 /dev/hdXX /mnt
```

where the X's are replaced by the letter and number where the partition resides.  For example, the first primary partition is most likely hda1.  If you're not sure, you can use fdisk to find out:

```
sudo fdisk -l
```

Then your Ubuntu partition should be mounted at /mnt where you can get at it.  Let me know if that works for ya.

---

### Post by garyed on 2007-08-04
Well I tried repairing grub as suggested but it still didn't work.
The grub menu comes up like usual at boot up & my option to go to Windows works fine but if i choose to go into Ubuntu the computer locks up & gives me the same error every time.
I've got Edgy on my 2nd drive & XP on my first. Everything was running fine with 98 & Edgy.
This all happened after I reformatted my first drive & upgraded to XP.

---

### Post by agds on 2007-08-04
Oh, I didn't realize you were upgrading to XP from 98.  In that case, you're probably best off reinstalling GRUB entirely, as suggested by overdrank.

---

