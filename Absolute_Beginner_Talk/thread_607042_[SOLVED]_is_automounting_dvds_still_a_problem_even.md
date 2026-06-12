---
title: "[SOLVED] is automounting dvds still a problem even in gutsy?!"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by unebaguettesvp on 2007-11-08
i've read on the forums (somewhere, i lost the link) that automounting dvds is a bug in ubuntu. this person posted that when edgy was out. is this still true?

i have a fresh install of gutsy and my cds automount perfectly. but when i insert a dvd (movie), i get an error that says something about line 7 in my /etc/fstab and that it can't find /media/cdrom0.

this person also suggested to mount it manually by:

sudo mount -t /dev/cdrom /media/cdrom

that works great. and i can play the movie just fine. but why doesn't this automount? does anyone else have this working?

if this is a bug, this is extremely embarassing to the linux community imho.

---

### Post by Pumalite on 2007-11-08
Post:
cat /etc/fstab

---

### Post by mschraier on 2007-11-08
what does the "cat" stand for?

---

### Post by _sluimers_ on 2007-11-08
concatenate or catenate
- to link together; form into a connected series.

In this case it's files formed into one long string displayed in the terminal.

cat <file 1> <file 2> .. <file n>

---

### Post by eternalsword on 2007-11-08
Just so you know, there's no need to mount a dvd to watch it, just open up your player and it will automatically detect the disc.

---

### Post by unebaguettesvp on 2007-11-09
i guess no one else is having any problems?

oh well. here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system>					<mount point>	<type>		<options>			<dump>	<pass>
proc						/proc		proc		defaults			0	0
UUID=ca52ec2f-6de1-4400-85a6-5a3200e0b0f2	/		ext3		defaults,errors=remount-ro	0	1
UUID=6c4925fc-9ee6-4386-aae8-f61e3df53973	/data		ext3		auto,users,rw			0	0
/dev/hdc					/media/cdrom0	udf,iso9660	udf,iso9660 user,noauto,exec	0	0
/dev/fd0					/media/floppy0	auto		rw,user,noauto,exec		0	0
```

thanks for any help!!!!

---

### Post by Pumalite on 2007-11-09
Your CD-ROM is mounted automatically at boot(it's in your fstab):
/dev/hdc					/media/cdrom0	udf,iso9660	udf,iso9660 user,noauto,exec

Backup your fstab:
sudo cp /etcfstab /etc/fstab.back
gksudo gedit /etcfstab
Remove one of the udf.iso9660
Save exit and reboot. Let's see what happens

---

### Post by unebaguettesvp on 2007-11-09
where do i remove udf,iso9660? from the type or the options column? and what do i replace it with?

or do you want me to remove that whole line altogether? thanks!!!

also, i just noticed this... in the options column for the cdrom drive:

udf,iso9660 user,noauto,exec

there is a space between iso9660 and user! i think that's what's screwing it up! maybe?

---

### Post by eternalsword on 2007-11-09
no, there is meant to be a space between iso9660 and user.  udf,iso9660 is the filesystem type and then starting with user are the options.  Also, why would you want to mount a dvd video?  Any player will play them fine without mounting, and you end up disabling automatic mounting of data discs.

---

### Post by mivo on 2007-11-09
For what it is worth, when I put a DVD in the drive, it is auto-mounted in Gutsy. This also had worked for me in Feisty alrready on three different computers. The bug you experience doesn't seem to affect everyone.

---

### Post by unebaguettesvp on 2007-11-09
> **eternalsword said:**
> no, there is meant to be a space between iso9660 and user.  udf,iso9660 is the filesystem type and then starting with user are the options.  Also, why would you want to mount a dvd video?  Any player will play them fine without mounting, and you end up disabling automatic mounting of data discs.

yeah, but there already is a udf,iso9660 defined for type. then somehow it got repeated into the options column again and then there is another space. it doesn't look right. here:

/dev/hdc					/media/cdrom0	udf,iso9660	udf,iso9660 user,noauto,exec	0	0

im going to try this when i get home. thanks for the help!!!

---

### Post by unebaguettesvp on 2007-11-10
fixed. all i had to do was remove that extra udf,iso9660! thanks for the help!

---

