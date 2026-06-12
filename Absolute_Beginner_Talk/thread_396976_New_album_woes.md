---
title: "New album woes"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Roger_Melly on 2007-03-30
I have bought "The Bees" new CD.  Put it in my box and it's unable to mount.  Blurb says "Put this CD in your computer for exclusive bit's n pieces".  Is this some windows media issue that is going to stall us Linux users from buying CD's now!! or am I just rubbish at Linux.

Please tell me how to open and rip my own CD.

Cheers

---

### Post by zvacet on 2007-03-30
```
 mount /dev/cdrom

```

And be sure you have all codec you need.
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Roger_Melly on 2007-03-30
zvacet:  Im being told:
mount: can't find /dev/hdc in /etc/fstab or /etc/mtab
What now?
I've added all the bits....

---

### Post by Roger_Melly on 2007-03-30
Here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=4752f480-93be-4d9e-92ba-a14c2b33323b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=6b957829-5c6c-4822-9c82-f2fc1b2fff2f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Roger_Melly on 2007-04-01
Folks,
can anyone help me please?  I have tried mounting the CD manually using the mount  /dev/cdrom command and simply mount  /cdrom but nothing happens.

All simple albums automatically open on insertion.

---

### Post by annda on 2007-04-01
the exclusives are definitely nicely packaged in a windows application, and the cd is not a standard audio cd.

if you inserted the cd under win, you probably wouldn't even here the music, you'd just see the custom application open.

i've seen this with one or two of my sister's cds with "specials".

yours might be different, though. but this is rather unlikely.

---

### Post by Roger_Melly on 2007-04-01
annda,
any way to open it in Ubuntu though?

---

### Post by annda on 2007-04-01
sorry, none that i know of.

if the cd doesn't mount (and it's deliberately messed up not to mount), i don't think there is much that can be done.

it has some copy protection system and (at least in some countries) you can return it to the store, say it doesn't work on your cd player and get your money back.

---

