---
title: "Permissions w/ Live CD"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by Sable683 on 2007-05-30
Ok... I had a problem with my computer booting up with and with the live CD for Feisty, but now that is working. Now, I want to re-format the hard drive. I was using Edgy Eft, but with all of the updates, something went south. 

The situation is, I want to pull all of my data from Edgy and copy it to a usb drive, then re-format and partition the HDD and install Feisty Fawn. However, the only way my computer will boot up is with the Live CD and I don't have permissions to copy folders from the old HDD to the USB drive. Is there any way to do this?

Any and all help is appreciated!

~John

---

### Post by ryanVickers on 2007-05-30
Try running gksudo nautilus

This will let you brows your files as root.  It should work perfectly.  If your having trouble mounting the internal drive, type sudo mount /dev/sda1 (it might be a different number, or no number, or possibly sdb)

---

