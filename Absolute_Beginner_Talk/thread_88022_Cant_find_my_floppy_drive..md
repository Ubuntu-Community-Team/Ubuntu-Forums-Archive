---
title: "Cant find my floppy drive."
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by Cud on 2005-11-09
Hi, how do I save things onto a floppy using hoary?
When I try to use the command line to mount my floopy drive 
$ mount /dev/fd0
I get
 block device /dev/fd0 is write-protected, mounting read-only
but in etc/fstab I have
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Also the little yellow disc drive light never even goes on.
Any Ideas?
Thank you

---

### Post by Kyral on 2005-11-09
You want to mount /media/floppy0, not /dev/fd0

---

### Post by Cud on 2005-11-09
First thanks,

OK I tried 
 mount /media/floppy0
but still nothing happens.
The terminal just stays at that line, no error messages or anything.
wait... after 5 minutes or so I get
mount: block device /dev/fd0 is write-protected, mounting read-only

---

### Post by Kvark on 2005-11-09
The floppy has two holes, one of those holes has a small plastic thingy that can be slid over the hole to close it. The floppy is read only if both holes are open. But when the hole with the small plastic thingy is closed then it is posible to write to the floppy.

---

### Post by Valencik on 2005-11-10
Similar problem.

Put in a floppy try and open it....

[I]
Unable to mount the selected volume.:
mount: I could not determine the filesystem type, and none was specified[/I]

No idea where to even start.

What si the filesystem type of a floppydrive? How do I find out mine?

---

### Post by Kvark on 2005-11-10
Your floppies are most likely formatted with a Windows file system, either msdos or vfat so one of these two commands should work:
```
sudo mount -t msdos /dev/fd0 /media/floppy0
sudo mount -t vfat /dev/fd0 /media/floppy0
```

Remember to unmount the floppy before you take it out:
```
sudo umount /dev/fd0
```
Yes, there is no n in umount.

---

### Post by Valencik on 2005-11-10
Tried both, now get this error:

Could not save the file "/media/floppy0/test"

----
However a floppy icon [the mount] appears on my desktop once i enter in either:

sudo mount -t msdos /dev/fd0 /media/floppy0
or
sudo mount -t vfat /dev/fd0 /media/floppy0

If i double clikc the icon it'll open up the file but the create folder/file options are greyed out.

Why?

---

### Post by Cud on 2005-11-15
When I
$ sudo mount -t msdos /dev/fd0 /media/floppy0
I get  mount: block device /dev/fd0 is write-protected, mounting read-only

and nothing....

When I $ sudo mount -t vfat /dev/fd0 /media/floppy0
I Get 
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: /dev/fd0: can't read superblock

Still theres no light turning on for the floppy, and it doesn't sound like anything is moving there at all.

Any further Ideas??

---

### Post by whorush on 2008-04-11
i just fixed this on my machine.

make sure the end of your floppy cable is plugged into the floppy.  the middle plug on the cable didnt work.  make sure the power is connected properly.

here's a good test.  make the floppy first in your boot order, and boot with a disk in.  if your floppy is powered and works, it will buzz a bit, find a nonsystem disk, and refuse to boot.  non-system disk error?  remember that from the old days?  try to force one, if  you get it, then your floppy works.

good luck!

---

