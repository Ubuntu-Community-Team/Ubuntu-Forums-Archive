---
title: "[SOLVED] Ubuntu Scrapped It's Own Dvd Mounting Mechanism, Can't Mound Dvds Anymore."
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by LeDechaine on 2008-02-27
This is pissing me off.

It looks like i'm back on Windows, but i'm not. Everything works, and, suddenly, for no freaking reason at all, without warning me, without even telling me that something scrapped/has gone wrong/whatever, without even noticing me anything, something stops working.

First, after wasting most of my time trying to setup ubuntu for **days** (though I still haven't had all my answers, **by the way**), I could play CDs, DVDs, and Data DVDs. Everything was working fine. Everything was perfect. Minutes after, I want to listen to another DVD: **NOTHING**. I try another DVD: **NOTHING**.

Since then, **the DVD mounting mechanism is scrapped.**
And yes, I rebooted. But nothing changed, it's still **scrapped**.

Anyone already experienced this? Anyone knows how to repair this? Help me.

---

### Post by LeDechaine on 2008-02-27
Oh, forgot to mention: CDs work perfectly. Only the DVDs stopped mounting.

---

### Post by asmoore82 on 2008-02-27
Have you used any 3rd Party "helper" Apps such as Automatix? If so, which ones??

run these commands in a terminal("Applications -> Accessories -> Terminal") and post the output:
```
cat /etc/fstab
ls -la /media
```

---

### Post by LeDechaine on 2008-02-28
No I haven't, don't even know what is automatix, even though I often heard about it.

**cat /etc/fstab**:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=d8e4bc4e-3ae1-492c-bc14-953fece52910 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=3E5D-0B07  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda5
UUID=4230-2AE9  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda6
UUID=1f9e10a6-297c-406b-97c4-6c3d4a8666cb none            swap    sw              0       0
/dev/hdb1       /media/audiovisuel     vfat    defaults,utf8,umask=007,gid=46 0 0
/dev/hdb5       /media/personnel       vfat    defaults,utf8,umask=007,gid=46 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

**ls -la /media**:
```
total 188
drwxr-xr-x  9 root root     4096 2008-02-27 21:35 .
drwxr-xr-x 21 root root     4096 2008-02-27 21:33 ..
drwxrwx--- 10 root plugdev 32768 1969-12-31 19:00 audiovisuel
lrwxrwxrwx  1 root root        6 2008-01-10 19:15 cdrom -> cdrom0
drwxr-xr-x  2 root root     4096 2008-01-10 19:15 cdrom0
lrwxrwxrwx  1 root root        7 2008-01-10 19:15 floppy -> floppy0
drwxr-xr-x  2 root root     4096 2008-01-10 19:15 floppy0
-rw-r--r--  1 root root        0 2008-02-27 21:35 .hal-mtab
drwxrwx--- 49 root plugdev 32768 1969-12-31 19:00 hda1
drwxrwx--- 24 root plugdev 98304 1969-12-31 19:00 hda5
drwxrwx---  6 root plugdev  8192 1969-12-31 19:00 personnel
drwxrwxrwx  2 root root     4096 2008-02-17 21:45 phoenix

```

This part of **sudo lshw** may also help:
```
*-cdrom
                   description: DVD-RAM writer
                   product: HL-DT-ST DVDRAM GSA-4160B
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: A301
                   serial: K7E49B55353
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2 **status=nodisc**

```
(Note the "*status=nodisc*", there is actually a DVD+RW in the drive.)

Also, the drive is still viewable in nautilus as a «**CD-RW/DVD±RW Drive**».

---

### Post by LeDechaine on 2008-02-29
So what? Ubuntu, the user-friendly distro until it silently scraps itself?..

---

### Post by asmoore82 on 2008-03-01
> **LeDechaine said:**
> No I haven't, don't even know what is automatix, even though I often heard about it.

...

(Note the "*status=nodisc*", there is actually a DVD+RW in the drive.)

Also, the drive is still viewable in nautilus as a «**CD-RW/DVD±RW Drive**».

Can the Drive still read real pressed DVDs or no?

Has this DVD+RW been formatted yet?

---

### Post by AlanR8 on 2008-03-01
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

It's a script that will sort out all your multi media needs. Some say it is like a drink from the Devil's cup...alll that I can say is it works EVER time and has never trashed my system! 

Go for it.

---

### Post by LeDechaine on 2008-03-05
The drive can't read any DVD whatsoever, but can read CDs. And yes this DVD+RW has been formatted, with Brasero, added files on the DVD+RW with it after, everything was ok.

Absolutely nothing is shown in the logs. Anyway, this seems to be a 2005 bug resurrecting, I've responded to this. [https://bugs.launchpad.net/ubuntu/+bug/16351](https://bugs.launchpad.net/ubuntu/+bug/16351)

---

### Post by LeDechaine on 2008-03-14
Well, looks like no one can help me with this, either in launchpad or here, at least i've got Windows XP to read DVD's, i'll try, it *may* be that my DVD drive is scrapped, but if not, it doesn't surprises me that Ubuntu is the problem, since Ubuntu 7.10 is the Linux equivalent of **Windows ME**.

With the exception that bugs under Ubuntu can be corrected, but whatever. Been a pain in the *** to get everything working like I wanted, and now Ubuntu scraps it's own DVD reading mechanism.. This is pissing me off.

---

### Post by IsawSp4rks on 2008-03-14
Do you dual boot with XP/Vista?

Have any games installed that use Starforce protection?

Starforce has been known to cause issues with DVD/RW drives by damaging them via direct firmware writes, causing them to have issues with some media including CDRs and DVDRs/RWs.

The issue may not be ubuntu's fault.

---

### Post by LeDechaine on 2008-03-14
Nah, I don't play games.

(Well, unless the linux enemy territory version contents starforce, but I guess not.)

One minute the DVD drive works flawlessly at least and the minute after: nothing. And since that minute the DVD mounting mechanism in ubuntu is scrapped, haven't done anything weird or whatever, just inserted another (bought) DVD in the DVD drive, no response from the DVD drive since that.

Oh, the DVD drive CAN read CDs, but not DVDs (DVD or DVD+RWs). And even in the "lshw" command, when a DVD is inserted, well, I see "nodisk".
*(scroll up for more info)*

---

### Post by LeDechaine on 2008-03-17
Well, shame on me. The CD/DVD drive is scrapped.

Rebooted under XP yesterday, when even my Audio CDs wouldn't even play under Ubuntu. Tried to play it under XP and it doesn't works, and the Ubuntu LiveCD doesn't even boot, stuck at "searching for boot record in CD-ROM..." or something like that. So, finally, the CD/DVD drive is the problem, not Ubuntu.

Weird coincidence that it scrapped just after installing libdvdcss, when everything was finally working right, though..
(And that the CDs were playing..!)

It may just be a dust problem, so well, whatever, buying a duster can, and if it doesn't solves the problem, a new CD/DVD drive (or I may repair this one).

So thanks everyone, and, sorry :P

---

