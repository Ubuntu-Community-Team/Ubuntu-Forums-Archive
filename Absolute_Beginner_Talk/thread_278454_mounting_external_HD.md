---
title: "mounting external HD"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-16
I'm having problems mounting my external harddrive in Ubuntu
the drive appears but isn't mounted i can't access it and when i right-click and click "mount volume" it give me Unable to mount volume "failed to mount '/dev/sdd1': operation not supported

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
Edit/Delete Message



any help?!

---

### Post by an.echte.trilingue on 2006-10-16
First, try to mount it from the terminal:
```
sudo mount /dev/sdd1
```
and see what error messages it spits out.

Then, try to mount it read only:
```
sudo mount -ro /dev/sdd1
```
and see what error messages it spits out.

Let us know what you see.

Good Luck!

-mat

---

### Post by an.echte.trilingue on 2006-10-16
Also, be sure to install ntfs read/write support if you have not done so yet:

[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

Again, good luck!

-mat

---

### Post by givré on 2006-10-16
It's seams that you installed ntfs-3g.
This error appear when the ntfs journal file is unclean due in the majority of the case to an unclean unmount of the drive. Basicly, you forgot to click on eject before unplugging it.
Unfortunatly, linux don't have an equivalent to chkdsk, so you'll have to :
- find a windows box
- plug the device.
- eject it safely with the eject button of explorer.
- unplug the device.
And that's should be ok.

---

