---
title: "Gparted cant make disk label"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by etomic13 on 2008-01-22
I clicked on the unallocated space in Gparted and then clicked the New button to add a partition. The next dialog box allows me to add an 'msdos label'. From my understanding its creating a partition table then I get an error saying that it could not create a disk label, how frustrating! Any help?

---

### Post by kellemes on 2008-01-22
You're trying to add an msdos-partition?

---

### Post by etomic13 on 2008-01-22
nope Im trying to take the unallocated space (which is the entire harddrive) and create an ext3 partition out of it. But when I do it wants me to create a Disk Label, which subsequently it fails at doing.

---

### Post by vikram on 2008-01-22
**e2label(8) - Linux man page**

  **Name**

 e2label - Change the label on an ext2/ext3 filesystem **Synopsis**

 **e2label** *device* [ *new-label* ] **Description**

 **e2label** will display or change the filesystem label on the ext2 filesystem located on *device.* If the optional argument *new-label* is not present, **e2label** will simply display the current filesystem label. 
If the optional argument *new-label* is present, then **e2label** will set the filesystem label to be *new-label*. Ext2 filesystem labels can be at most 16 characters long; if *new-label* is longer than 16 characters, **e2label** will truncate it and print a warning message. 
It is also possible to set the filesystem label using the **-L** option of ***[tune2fs]("http://linux.die.net/man/8/tune2fs")**(8)*. 
**Author**

 **e2label** was written by Theodore Ts'o ([EMAIL="tytso@mit.edu"]tytso@mit.edu[/EMAIL]). **Availability**

 **e2label** is part of the e2fsprogs package and is available from [http://e2fsprogs.sourceforge.net]("http://e2fsprogs.sourceforge.net/"). **See Also**

 ***[mke2fs]("http://linux.die.net/man/8/mke2fs")**(8)*, ***[tune2fs]("http://linux.die.net/man/8/tune2fs")**(8)*   **REFERENCED BY **

 **[fstab]("http://linux.die.net/man/5/fstab")**(5), **[mount]("http://linux.die.net/man/8/mount")**(8)

---

### Post by wolfen69 on 2008-01-22
you must be root to make changes to a partition. after becoming root in terminal, open gparted in terminal. and partition/drive must be unmounted.

---

