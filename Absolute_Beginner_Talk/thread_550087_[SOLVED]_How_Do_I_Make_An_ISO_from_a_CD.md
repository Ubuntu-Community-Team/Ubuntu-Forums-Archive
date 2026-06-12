---
title: "[SOLVED] How Do I Make An ISO from a CD ??"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-13
I need to make an ISO of my Ubuntu Feisty Fawn Live CD in order for me to use the application 'Reconstructor'

How do I manage to this from my CDROM ?

---

### Post by chrome307 on 2007-09-13
Found the answer already :)

To make an ISO from your CD/DVD, place the media in your drive but do not mount it. If it automounts, unmount it. (ubuntu automount so you need to unmount, that's quite easy, just choose the option unmount from the shell).

dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi

the comments after the # are not required just to let you know which one to used

---

### Post by asmoore82 on 2007-09-13
> **chrome307 said:**
> Found the answer already :)

To make an ISO from your CD/DVD, place the media in your drive but do not mount it. If it automounts, unmount it. (ubuntu automount so you need to unmount, that's quite easy, just choose the option unmount from the shell).

dd if=/dev/dvd of=dvd.iso # for dvd
dd if=/dev/cdrom of=cd.iso # for cdrom
dd if=/dev/scd0 of=cd.iso # if cdrom is scsi

the comments after the # are not required just to let you know which one to used

**pipemeter** is an excellent program that can tell you how fast and close to being done the copying is.
It wasn't in the repos yet last time I checked but is extremely quick to compile: [http://spamaps.org/pipemeter.php](http://spamaps.org/pipemeter.php)

after installing you could create an ISO file with live speed stats like this ...

```
~$ dd if=/dev/cdrom | pipemeter >cd.iso
```

EDIT: Their site has .deb packages available ~ big Duh! for me.

---

