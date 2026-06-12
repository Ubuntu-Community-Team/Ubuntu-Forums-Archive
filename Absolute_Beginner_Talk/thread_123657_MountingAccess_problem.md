---
title: "Mounting/Access problem"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-01-30
I have created a Fat Partition which has been mounted onto the Desktop. I can read & write to it. fdisk shows the item as #hda7, but etc/fstab does not show #hda7 so I cannot make a change to it. When I reboot the desktop icon hda7 has gone.Any advice how to deal with this is appreciated.
Thanks

---

### Post by Sokraates on 2006-01-30
You need to edit a file called fstab to have your partition mounted on every startup. 

Take a look at [this](http://www.ubuntuguide.org/#automountfat) guide. Just dont forget to use /dev/hda7 instead of /dev/had1.

---

