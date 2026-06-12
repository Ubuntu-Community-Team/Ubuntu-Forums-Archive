---
title: "how to change permissions on usb nfts read-only disks"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by haberlah on 2007-08-23
Dear all,

I have a USB drive in NTFS format where I would like to make changes with Ubuntu (feisty fawn). I have installed ntfs-3g amd ntfs-confic from the Synaptic Package Manager. I have also started gksudo nautilus from the Terminal and accessed /media/usbdrive/ clicked on the tab "Permissions" and tried to set the pull-down menue "Folder Access" below "Owner" root to "Create and delete files" but only get the error message:

"The permission could not be changed. ... because it is a read-only disk"

Any idea how to make this work? I would just love to use the most sexy piece of software Amarok to sort my collection :guitar:

Cheers mates,

---

### Post by mikex on 2007-08-23
I had the same problem and i found no solution, however, when I nuked it and made it an etx3 partition, I could then change permissions. If anyone knows how let us know.

---

### Post by haberlah on 2007-08-25
come on guys - this is a serious question!

---

### Post by xiota on 2007-08-26
I don't really understand what you're trying to do.  Here are some possibilities:

Are you trying to use ntfs-3g to mount, read, and write to ntfs partitions?  Make sure the users you want to have those abilities are in the "fuse" group.

Are you able to read and write using ntfs-3g, but trying to change user- and group-level permissions to prevent users from messing with each other's files?  I think that's not possible with ntfs-3g at the moment.

Are you trying to unset the execute bit so people can't use ntfs partitions to install malware on your computer?  Replace /sbin/mount.ntfs-3g with a script:

[INDENT]#!/bin/sh
/usr/bin/ntfs-3g -o fmask=0111,noatime "$@"[/INDENT]

Remember to change permissions on the script so it will run:

[INDENT]chmod 755 /sbin/mount.ntfs-3g[/INDENT]

---

### Post by chr on 2007-08-26
hello,

i had the some problem some days ago. here is the solution i used.

have a look: [http://ubuntuforums.org/showthread.php?t=527045](http://ubuntuforums.org/showthread.php?t=527045)

brgds

chr

---

### Post by mysticmatrix on 2007-08-26
Since you have ntfs-config package installed, do this at terminal
```

gksudo ntfs-config
```

Check box related to external drives. Enjoy!

---

