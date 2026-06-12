---
title: "In the Installation I set Windows!"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-04-21
I can't remember the exact thing I did, but when I did manual partition, I choose my linux partion for /, swap for swap, and then (dumb me!) set my Windows XP partition to /windows.

Is there anyway I can remove /windows without deleting my windows partition / files?

---

### Post by BoneKracker on 2007-04-21
using the terminal:

```
sudo nano /etc/fstab
```

Then remove the line that automatically mounts the Windows partition:

[INDENT]press the down arrow until you reach the line that has /windows in it

press **ctrl+k** to delete that line

press **ctrl+o** to save the file (that's an "oh" not a "zero")

press **ctrl+x** to exit
[/INDENT]
reboot

Then Linux will not mount the partition where your Windows files are.

You can then also safely delete the mount point that was created (it's just an empty folder).

```
sudo rmdir /windows
```

---

### Post by freebird54 on 2007-04-21
Not entirely sure what you have ended up with there.  however, if it did mount, all that is necessary is to unmount it.  Deletion is NOT advised :)

If you go to the Places Menu, and select Computer, then select Filesystem, does a Windows directory actually show up?  Or does something else show up anywhere that you think is your Windows partition?

---

### Post by BoneKracker on 2007-04-21
Why would deletion not be advised.  It's absolutely safe and what the user wants to do.

---

### Post by freebird54 on 2007-04-21
I advised against deletion BEFORE unmounting - my post crossed yours.  :)  Just didn't type fast enough I guess...

---

### Post by BoneKracker on 2007-04-21
LOL... okay.  I should have known.  :)

---

