---
title: "Borked Fstab"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by wwitthoff1 on 2006-04-13
Hey,

I am new at all this linux stuff and in the process of learning seem to have done something to my /etc/fstab.

I get the :   line x in /etc/fstab is bad.


Any ideas.

For reference here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults	errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf	iso9660 	user	noauto     0       0
/dev/hdc        /media/cdrom1   udf	iso9660 	user	noauto     0       0
/dev/fd0       /media/floppy0   auto    rw,		user,	noauto 	0 0

---

### Post by joft on 2006-04-13
Hi,

[QUOTE=wwitthoff1]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults	errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf	iso9660 	user	noauto     0       0
/dev/hdc        /media/cdrom1   udf	iso9660 	user	noauto     0       0
/dev/fd0       /media/floppy0   auto    rw,		user,	noauto  0 0[/QUOTE]

The last 3 lines seem to be wrong. I think there shouldn't be spaces/tabs between options and between filesystems - just commas. You'll have to use:

```

/dev/scd0       /media/cdrom0   udf,iso9660 	user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 	user,noauto     0       0
/dev/fd0        /media/floppy0  auto            rw,user,noauto  0       0

```

Have a look at

```

man fstab

```

to learn more about the format of fstab.

---

