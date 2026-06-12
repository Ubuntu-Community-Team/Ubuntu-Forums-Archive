---
title: "Installing a 3rd hard drive - help needed"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by lonegranger on 2006-06-17
I was on the other night getting help installing a 3rd HD but unfortunately I ran out of time and had to log off. My motherboard is a Gigabyte K7 Triton GA-7N400 Pro2. When I was on XP the 3rd drive was recognised so the BIOS must be set ok. The drive is on IDE 3.

Any further help will be really appreciated.

---

### Post by djsroknrol on 2006-06-17
I take it you're trying to set up the drive for Linux to see...

post your /etc/fstab here and maybe someone can be of some help...sounds like you need to write it into fstab....

---

### Post by lonegranger on 2006-06-17
My /etc/fstab is below

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext2    defaults        0       2
/dev/hdb1       /media/hdb1     ntfs    user,umask=0200        0       0
/dev/hdb5       /media/hdb5     ntfs    user,umask=0200        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by djsroknrol on 2006-06-17
Are you still running XP? It looks like you aren't...

is the 3rd drive formatted ext2, ext3, fat, NTFS? Depending on how it's formatted, you need to edit fstab to include the 3rd drive to be mounted at bootup, which is a pretty straightforward thing...

---

### Post by lonegranger on 2006-06-17
I think it must be formatted ext2 or 3. The reason I'm not sure is that the PC used to belong to my son and he dual booted with XP and Linux. Is there any way of finding out??

---

### Post by djsroknrol on 2006-06-17
If you're running Dapper, go to:

System>Administrative>Gnome Partition Editor...that would tell you what you need to know.

In Breezy, it's: Applications>System Tools

If nothing else, google "GParted live CD, burn the iso and boot off the CD.

Then once you have your data, a line entry in fstab to the order of:

```
/dev/hdbX /media/hdbX OOOO user,umask=0200 0 0
```

where "X" is your partition and "O" is the format (ext2, ext3, fat or NTFS)

Like they say back home...easy money...:)

---

### Post by aysiu on 2006-06-17
I don't believe umask works with Ext3.

---

### Post by djsroknrol on 2006-06-17
I believe aysiu is right...

you might try:

"user,auto   0   0  "   instead...

P.S. great sig aysiu

---

