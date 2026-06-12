---
title: "How to format a floppy?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by tubunu on 2006-06-27
The floppy is empty (deleted the previous files there) but it tells me it's full. I'd like to format it, but I don't know how... Please help.

---

### Post by Kilz on 2006-06-27
[QUOTE=tubunu]The floppy is empty (deleted the previous files there) but it tells me it's full. I'd like to format it, but I don't know how... Please help.[/QUOTE]
Go to Places, then Computer. You will see the floppy drive, right click on it and choose Format.

---

### Post by tubunu on 2006-06-27
Thanks, but it gives me the following error with standard option checked:

```
Error formating track #0
```

In quick formatting mode it says:

```
mkdosfs: /dev/fd0 contains a mounted file system. (50)
```

Any other way? ;)

---

### Post by confused57 on 2006-06-27
Click on Applications--Accessories--Ala Carte,  click on System Tools, check the floppy formatter.  This will add the floppy formatter to your System Tools menu.

Then you can open floppy formatter and format a floppy with ext2 or fat.

This is with Dapper, with Breezy it's already in your System Tools.

---

### Post by steve.horsley on 2006-06-27
Even easier - with Nautilus, click the Computer icon at the top. There is a  floppy icon that you can right-click and choose format and mount/unmount.

---

### Post by US41 on 2008-06-14
Not any more you can't. In hardy, when you right click on a floppy, there is no option to format.

---

### Post by waspbr on 2008-06-14
OMG!!! you still use floppies?

---

### Post by Dr.Ninethousand on 2008-06-15
assuming your floppy drive is /dev/fd0...

```
sudo umount /dev/fd0
fdformat /dev/fd0
```

then create an msdos file system on it...

```
mkfs.vfat /dev/fd0
```

or Linux ext3 file system..

```
mkfs.ext3 /dev/fd0
```

---

### Post by confused57 on 2008-06-15
Open a terminal(Applications---Accessories---Terminal), enter:
```
gfloppy
```

Click on "Format"

---

### Post by Dr.Ninethousand on 2008-06-15
gfloppy never actually started up for me though..

---

### Post by gitano on 2008-06-19
ok. so i cant remember if i downloaded this or if it came with- but

so just check this first-

add and remove programs : floppy formatter

if you have it, good- otherwise get it

put the floppy in, but dont mount it
if it is mounted automatically, then unmount


spark up the terminal

then type, gfloppy like dude above said


and you will see a window open.  that is the floppy formatting tool.


if this is something you will be doing often,  then go to

system/preferences/main menu

and make sure to check that floppy formatter is listed under system tools.

---

### Post by mtngun on 2008-07-18
This thread did not answer the question about how to format a floppy.

The Hardy version of Nautilus no longer shows a "format" option when you right click on the floppy.   Dunno why, since that was a handy feature.

The solution is to open a terminal, and run "gfloppy".   Gfloppy should already be installed as part of the gnome-utils package.   Gfloppy will give an error if the floppy is mounted, so the floppy needs to be unmounted.

---

