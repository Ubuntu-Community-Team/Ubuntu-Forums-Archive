---
title: "Creating SBM floppy with &quot;dd&quot; command"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by dankdave on 2008-01-18
Hi,

I tried reading many posts but haven't found anyone that has described how to create a SBM (smart boot manager) floppy disk using linux commands.  The help sites seem to describe how this is done in Windows 98, but I don't have a copy of windows.

I found the files mt86plus README.sbm and sbm.bin in /cdrom/install# and have tried the following command:

dd if=/cdrom/install/sbm.bin of=/dev/fd0

and get the following error message:

dd: writing to '/dev/fd0': Input/output error
1+0 records in
0+0 records out
0 boytes (0 B) copied, 1.25175 seconds, 0.0 kB/s

I believe I formated the disk correctly by typing

fdformat /dev/fd0

Is someone willing to walk me through how to make a floppy boot disk?

Thanks in advance.

---

### Post by mattismyname on 2008-01-18
Make sure you execute the dd as root:

sudo dd if=...

dd completely overwrites the disk so formatting is lost.  It doesn't matter how you've formatted the disk.

When you do the dd command, does the light on the floppy drive come on before the error happens?

If so, maybe the disk is bad and you should try a different floppy.

---

### Post by dankdave on 2008-01-18
Hi Matt,

The light doesn't light up when I type that command.  Am I supposed to mount the disk before using the dd command?  Is there a way to see if the command actually worked, i.e. how do I check the contents of a floppy disk?

---

### Post by scorp123 on 2008-01-18
> **dankdave said:**
>  The light doesn't light up when I type that command. Do you really have a plain old floppy drive or are we talking about a USB floppy drive?

Are you really sure your floppy is /dev/fd0 and not something else? Is your floppy drive really a plain old 1990-ish floppy disk drive that connects to an 1980-ish MFM floppy drive controller ... Or are you using a USB floppy drive? In that case the nomenclature would be different: USB devices --no matter what they are-- are seen as "SCSI" devices, so they get names like /dev/sda, /dev/sdb and so on.

---

### Post by dankdave on 2008-01-18
Yep, this floppy drive is definitely "old school" without any usb connection.  The computer is a 600mHz Pentium III with Ubuntu 7.10 server installed on it.

Do you know how I could verify the floppy is located at /dev/fd0 ?

---

### Post by logos34 on 2008-01-18
the path looks wrong:

> dd if=[COLOR="Red"]/cdrom/[/COLOR]install/sbm.bin of=/dev/fd0

the standard mountpoint is /media/cdrom0

---

### Post by dankdave on 2008-01-18
1

---

### Post by dankdave on 2008-01-18
OK, so some new stuff is now happening.  I may have mounted the cdrom in the wrong spot, to be honest I don't remember what I did to be able to find the contents of the cd last evening.

Today, I typed "mount /cdrom" , and am able to navigate to both  /media/cdrom0/ or /media/cdrom/

I tried "sudo dd if=/media/cdrom0/install/sbm.bin of=/dev/fd0" and this time the light on the floppy disk drive lights up for a second and I get the following error:

dd: reading '/media/cdrom0/install/sbm.bin': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.001... seconds, 0.0 kB/s

I tried using two different floppys and get the same error message with each.

---

### Post by logos34 on 2008-01-18
The cdrom should automount.  What's is shown by 

cat /etc/fstab | grep iso9660

And try formatting this way:

sudo mke2fs /dev/fd0

---

### Post by dankdave on 2008-01-18
In response to your first question:

/dev/scd0    /media/cdrom0    /udf, iso9660   user, noauto, exec 0      0


When I tried formatting with the command you suggested, I received a few errors with one disk.  The other disk looked like it went through ok.

---

### Post by logos34 on 2008-01-18
ok.  in a terminal type

gnome-volume-properties

'mount removable media when inserted' box should be checked.  Reload the ubuntu cd. (you're using the LIVE cd, right?)

it should automount at /media/cdrom0

then try dd again

for future ref (formatting floppies):

> fdformat /dev/fd0u1440		-->low-level format 1.44 MB floppy

sudo mke2fs /dev/fd0		-->format floppy with ext2 filesystem

sudo mkfs.msdos /dev/fd0	-->format floppy with DOS filesystem

---

### Post by dankdave on 2008-01-18
I'm not  running the live cd; I have ubuntu 7.10 server installed on this machine.

---

### Post by logos34 on 2008-01-18
I meant you're trying to copy sbm.bin from the live cd, right?  (because IIRC it's not on the alternate cd...just checking)

EDIT: correction...it is.  nm 

So any luck?

---

### Post by dankdave on 2008-01-18
No luck.  I've given up on making a floppy boot, and have started working on getting the computer to take a CD-Rom.  I think I started making some progress, the computer was having difficulty with taking an 80gb hard drive but seems to be doing fine with this 15gb hard drive I pulled from another computer.

---

### Post by scorp123 on 2008-01-18
> **dankdave said:**
> No luck.  I've given up on making a floppy boot Can you read from the floppy drive? You could insert a floppy disk, e.g. one of which you know that there has to be something on it (e.g. an old MS-DOS boot diskette) and then see if you can read from it. Maybe your floppy drive is just damaged? I had that too. Never used my floppy drive in a long time but then when I really needed to use it no disk would work. Turned out that it somehow got damaged over the years.

---

### Post by mattismyname on 2008-01-18
Yeah, floppies go bad quickly with age.  I went through so many of those drives back in the day...

---

