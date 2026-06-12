---
title: "Formatting floppys"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-10-04
How do I give a new format to a floppy?

---

### Post by wpshooter on 2007-10-04
put the floppy in the drive.

right hand click on the drive icon and mount the media

after mounted, right hand click on the drive icon and format the drive.

---

### Post by yabbadabbadont on 2007-10-04
> **wpshooter said:**
> put the floppy in the drive.

right hand click on the drive icon and mount the media

after mounted, right hand click on the drive icon and format the drive.

You can't mount the media if it has not yet been formatted...  ;)

To the OP, I believe that you can format a floppy through the manage drives app under System->Administration.  I don't have Gnome installed at the moment, so I'm not sure of the exact name of the menu entry.

---

### Post by philinux on 2007-10-04
just install kfloppy from synaptic

---

### Post by plucky on 2007-10-04
To format floppy

Applications>Terminal
```
mkfs -t ext2 /dev/fd0
```

should format floppy in ext2 format

```
man mkfs
```

for information on using different formats

cheers 

:)

---

