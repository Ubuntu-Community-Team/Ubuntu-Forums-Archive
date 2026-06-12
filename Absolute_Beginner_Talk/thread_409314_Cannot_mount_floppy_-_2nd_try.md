---
title: "Cannot mount floppy - 2nd try"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by alfonsos on 2007-04-14
[This's my 2nd posting in an attempt to solve this problem] 

Can't seem to remount the floppy after I unmounted it.

Here's the content of /etc/fstab:

# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Here's the printout following the mount command:

$ mount /media/floppy0
mount: I could not determine the filesystem type, and none was specified

Isn't "auto" a legitimate value for <type>?

Also tried: $ sudo mount /dev/fd0 /media/floppy0

Same result

Also tried: $ sudo mount /dev/fd0 /floppy -t vfat

Same result

Al
Edit/Delete Message

---

### Post by energiya on 2007-04-14
If nothing else worked for you, try this:
- modify /etc/fstab to look like this:
```

#/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

```
(just deactivate the floppy part)
- reboot
- in a terminal:
```

sudo su
mkdir /media/floppy
mount /dev/fd0 /media/floppy
umount /dev/fd0
mount /dev/fd0 /mdedia/floppy

```
Does this work? If it does, you could put
> 
mount /dev/fd0 /media/floppy

in a script and make a shortcut or something for it (the same for the unmountig part), or just use the terminal.

---

### Post by alfonsos on 2007-04-14
Revised /etc/fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/fd0        /media/floppy0  auto rw,user,noauto     0       0

<Reboot>

~$ sudo mkdir /media/floppy


~$ sudo mount /dev/fd0 /media/floppy
mount: you must specify the filesystem type
~$ umount /dev/fd0
umount: /dev/fd0 is not mounted (according to mtab)
~$ sudo mount /dev/fd0 /media/floppy
mount: you must specify the filesystem type
~$

Oh well, assuming I executed your instructions properly, no go -  that filesystem specification error message seems to show up regardless what's tried.

Thanks,

Al

---

### Post by alfonsos on 2007-04-14
I got it to work by using "vfat" for file <type> instead of "auto".

/etc/fstab:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat rw,user,noauto     0       0

I wonder why "auto" doesn't work.

Al

---

### Post by Sladi on 2007-06-06
I still get this error. I use Xubuntu 64 bit and it seems I could format the disk but I always get this filesystem error. 
Isn't there a way to get a floppy drive to work? I need to copy files to it. 


edit:
It works after formatting the disk with: 
```
mkdosfs -c /dev/fd0
```
The c option is for checking for bad sectors.

---

