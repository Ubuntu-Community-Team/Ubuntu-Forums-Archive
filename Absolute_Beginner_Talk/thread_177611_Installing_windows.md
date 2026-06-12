---
title: "Installing windows"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by ELD on 2006-05-16
Hi all i have setup my ubuntu box yet again after trying other distributions but i'm back!

A question i wish to freshly wipe my Windows XP install because it has slowed right down and is just really annoying. Will it change the MBR and wipe grub?

What i'm basically asking is if i re-install XP will i still be able to use ubuntu?

---

### Post by nalmeth on 2006-05-16
It will wipe your MBR definately, you'll have to reinstall grub:
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Tip: Create a fat32 partition for window's first, so you can write to it from ubuntu. You can't select it during install.

---

### Post by aysiu on 2006-05-16
[QUOTE=ELD]
What i'm basically asking is if i re-install XP will i still be able to use ubuntu?[/QUOTE] No. You'll have to [reinstall Grub.](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by ELD on 2006-05-16
Can Windows XP run off fat32, thought it could only run on NTFS?
It isn't really needed anyway i keep all work on a seperate fat32 hard drive anyway.

Thanks for the advice.

---

### Post by Popcorn on 2006-05-16
Yeah it can, but I don't think It's recommended from Microsoft.

---

### Post by ELD on 2006-05-16
Mabye i will put on 2000, i always preffered that to XP anyway.

Does 2000 have lower system requirements i can't remember?

---

