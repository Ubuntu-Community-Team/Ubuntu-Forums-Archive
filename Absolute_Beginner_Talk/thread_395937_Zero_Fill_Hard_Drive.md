---
title: "Zero Fill Hard Drive?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Syan48306 on 2007-03-28
I was wondering if anyone knew the command to Zero Fill a hard drive under Ubuntu Linux. Also, how safe is the data on the drive after the drive has been zeroed out; Usually deleting the data (normally) doesn't actually delete the data because it just allows you to write over it, but if write zeros to it, is it still possible to retrieve the data?

If I boot off of a live CD with the desired hard drive in an external enclosure (USB), what is the specific command to fill up every last bit with zeros?

Thanks.

EDIT: Excuse my typos >.< gosh i was really smoking something when i typed it up heh.

---

### Post by jordanmthomas on 2007-03-28
```
dd if=/dev/zero of=/dev/hda 
```
You'll need to replace /dev/hda with the drive you intend to rape.

**edit** and I assume you know to be careful

---

### Post by oilchangeguy on 2007-03-28
quote=allows you to wright over it, but if right zeros to it. first let's use the correct word. in this case it's not wright, or right, it's write! and what exactly are you trying to do? delete data so no one else can retrive it?

---

### Post by h0ax on 2007-03-28
Let's just say if there's something on there that you need to be able to hide after a zero-fill operation, then it's probably sensitive enough that whoever wants to read it may have something to get it back.

You're probably fine after zero-filling it, though.

---

### Post by mcduck on 2007-03-28
zero-filing is no use, it's pretty easy to recover as the data used to overwrite existing data is same for every bit on the disk. Use random data instead, replacing /dev/zero with /dev/random :Ddd ```
if=/dev/random of=/dev/hda
```

Then, if you want to really be sure, repeat that many times, as the read/write heads of hard disk can move at slightly different places when writing to disk, leaving traces of overwriten data that could would still allow to recover the data with special tools.

---

### Post by Syan48306 on 2007-04-05
So if i was to unplug all of the drives in my computer and then connect only the hdd i want to wipe into SATA 1 port in the system it would be if=/dev/random of=/dev/sda ? or would i have to mount it first or wat not.

Plus it doesn't seem to like the "random" command...is that a valid command?

---

### Post by LaurelLynn on 2007-04-05
Just an observation,

Writing random values to the whole drive will realy mess up the partition table.  I don´t know how the Live CD will react when it tries to mount existing partitions.

I would add the options:   bs=512 skip=1

To skip over the MBR.

Laurel Lynn

---

### Post by wpshooter on 2007-04-05
try this:

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

or this:

[http://www.killdisk.com/](http://www.killdisk.com/)

---

