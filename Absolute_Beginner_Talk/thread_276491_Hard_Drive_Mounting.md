---
title: "Hard Drive Mounting"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-13
im having trouble mounting my external hard drive on Ubuntu..any suggestions?
thanks

---

### Post by farmerbee on 2006-10-13
more details ..  mount manually or auto??

---

### Post by Mazen on 2006-10-13
well the drive appears but isn't mounted i can't access it and when i right-click and click "mount volume" it give me Unable to mount volume "failed to mount '/dev/sdd1': operation not supported

mount is denied because the ntfs journal file is unclean. choices are:

 a) shutdown windows properly.

 b) click the 'safely remove hardware' icon in the windows taskbar

    notification area before disconnecting the device.

 c) use 'eject' from windows explorer to safely remove the device.

 d) if you ran chkdsk previously then boot windows again which will

    automatically initialize the journal.

 e) run 'ntfsfix' on linux which will reset the ntfs journal.

 f) mount the volume read-only by using the 'ro' mount option.

error: could not execute pmount
"

---

### Post by Mazen on 2006-10-13
i am hibernating windows might that be the problem? but i did it once before and it was working fine

---

