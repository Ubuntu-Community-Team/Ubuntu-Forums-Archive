---
title: "unmounting volume errors..."
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Hranj on 2007-08-31
ive been having a problem unmounting volumes like flash drives and memory cards since i upgraded to 7.04.

whenever i right click on a drive located on the desktop i get an error message that says:

> Cannot unmount volume
Cannot unmount the volume
Details: Cannot remove directory

I need to figure this out because whenever i put something on a memory card or my flash drive it doesnt write it when i unmount it just gives me this error message. Help please.

---

### Post by alienexplorers on 2007-09-01
Are you sure that all access to the drives (flash cards, etc.) is totally off before trying to unmount them.  If they are being used by any program they will not be able to be unmounted.

---

### Post by joemastro67 on 2007-11-27
I'm having the exact same problem. Does anyone have any clues? The system by all appearance seems to write the file fine. After clicking past the error message the drive does unmount. But after reinserting the drive the file is either not there or a file is there with a size of 0 bytes.

---

### Post by ThanhBT on 2007-12-11
I having same problem, any one can help me?

---

### Post by FuturePilot on 2007-12-11
Try this
Launch Nautilus as root
```
gksudo nautilus
```
and navigate to /media/
Press Ctrl+H to show hidden files, and you should see a file called .hal-mtab
Delete it. Close Nautilus
Should work after that.
Seems that if there's stale entries in that file it messes some stuff up

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95368]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/95368")

---

### Post by joemastro67 on 2007-12-12
Thanks Man. It worked like a charm. I like Linux again! :)

---

