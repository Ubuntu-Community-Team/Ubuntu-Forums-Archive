---
title: "Floppy Drive won't mount on AMD 64 platform"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2006-07-18
I previously had a x86 version of Ubuntu on my system but I have switched to the AMD 64 one (as I have a AMD 64 3000+ venice) but now the floppy drive isn't working. :confused:  Here's the error message:

> mount: i could not determine the filesystem type, and none was specified

---

### Post by nalmeth on 2006-07-18
What was the exact command you entered?

Did this particular disk work fine on i386?

What is the output of this command, so we can see if the floppy is entered correctly on fstab
```
cat /etc/fstab
```

---

### Post by fatsheep on 2006-07-18
> **nalmeth said:**
> What was the exact command you entered?

I just double clicked on the floppy in file manager


[quote=nalmeth]Did this particular disk work fine on i386?[/quote]

Yes.

> What is the output of this command, so we can see if the floppy is entered correctly on fstab
```
cat /etc/fstab
```

```

fatsheep@fatsheep:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
fatsheep@fatsheep:~$
```

---

### Post by fatsheep on 2006-07-18
I hate to bump my own topics all the time but I really could use a fix for this, all the stuff I was going to import from windows is stored on floppies.

---

### Post by skale on 2006-07-18
in the dev/fd0 line, try changing "noauto" to "auto", save it, open a terminal, type **sudo mount -a**

Post if it doesn't work.

---

### Post by fatsheep on 2006-07-18
Alright I have changed the noauto to auto, saved the file as you said.  Here were my results at the terminal:

> 
fatsheep@fatsheep:~$ sudo mount -a
Password:
mount: you must specify the filesystem type


Hmmm ](*,)

---

### Post by skale on 2006-07-18
on the same line, change the word "auto" (the one after "floppy0", not the one after "user") to "vfat". Post what happens.

---

### Post by fatsheep on 2006-07-18
Done.

> 
fatsheep@fatsheep:~$ sudo mount -a
mount: /dev/fd0 is not a valid block device


EDIT: The strange thing is I can always acess the files of the first floppy I put in.  Any after that do not work.  This is a very strange issue. :-k

---

### Post by fatsheep on 2006-07-18
This is really weird, it's like the computer loads the first set of files put into the floppy drive and that's it.  I can even access files from the floppy after I have taken it out or while I have a new floppy in the drive.  ](*,)

---

### Post by fatsheep on 2006-07-19
To restate the current problem: 

I can acess the files of the first floppy I insert after bootup but not those of the floppies I insert later on.  In order to access another floppy I have to reboot my system. :confused: 

I've tried messing around with the fstab file, rebooting, reverting back to the original, remounting, just about everything I, as a linux newbie, would think of doing.  Should I just give up on this?    :-k

---

### Post by falcon15500 on 2006-07-19
Are you unmounting the first floppy before you physically eject it?

falc

---

