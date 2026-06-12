---
title: "changing cd-rw drive permissions"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by SteveNorman on 2008-04-10
I cant burn anything with my cd rw. I can in windows so I know it wirks and the disks are good.

I looked in places>computer>cd-rw and saw there is a permissions tab under properties. It says read only, and it will not let me change it to read-write

it is a philips cdd4801 

is this why it wont let me burn cds?

if so how can I change it?

I saw something about ide-scsi emulation,,but the info was vague.

Thanks 
Steve

---

### Post by swoll1980 on 2008-04-11
alt+F2
type gksudo nautilus
type password

in the nautilus window click computer near top

right click your cdrw drive
go to properties
mark the permissions to write for your user name
this will work some say it's not recomended I'm not sure about any of that I just know it works

---

### Post by herbster on 2008-04-11
Are you in the optical group? What do you see when you issue this command:

```
groups
```

If you don't see optical, do this:

```
sudo gpasswd -a username optical
```

---

### Post by SteveNorman on 2008-04-11
-Swoll i will try that if nothing safer comes up..

-Herbster

I got this: 

steve@teampeanut-desktop:~$ groups
steve adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
steve@teampeanut-desktop:~$ sudo gpasswd -a username optical
[sudo] password for steve:
gpasswd: unknown user username
steve@teampeanut-desktop:~$ sudo gpasswd -a steve optical
unknown group: optical
gpasswd: Permission denied.
steve@teampeanut-desktop:~$ 

maybe I am missing something?

also I got gnomebaker to work on an audio cd, but could not burn on anything else,, kb3 etc.

---

### Post by herbster on 2008-04-11
Okay, it's different on Ubuntu then I see.

You don't want to change the permissions of the device itself. So Gnomebaker allows you to make an audio cd successfully, but K3b won't burn anything at all? What error do you get exactly when you try the actual burn in K3b?

---

### Post by SteveNorman on 2008-04-11
I get this:


System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
PHILIPS CDD4801 CD-R/RW C1.3 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM] [Error] [TAO, RAW, RAW/R16]

Compaq DVD-ROM DV-5700B 1.23 (/dev/scd0, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]
Used versions
-----------------------
cdrdao: 1.2.2

cdrdao
-----------------------
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty
Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.
Using libscg version 'ubuntu-0.8ubuntu1'
/dev/scd1: PHILIPS CDD4801 CD-R/RW Rev: C1.3
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0010)
Starting write at speed 8...
Process can be aborted with QUIT signal (usually CTRL-\).
WARNING: No super user permission to setup real time scheduling.
ERROR: Cannot set write parameters mode page.
ERROR: Cannot setup write parameters for session-at-once mode.
ERROR: Please try to use the 'generic-mmc-raw' driver.
ERROR: Writing failed.

cdrdao command:
-----------------------
/usr/bin/cdrdao write --device /dev/scd1 --driver generic-mmc:0x00000010 --speed 8 -n -v 2 --force --eject --remote 23 /tmp/kde-steve/k3b_audio_0_.toc

---

### Post by SteveNorman on 2008-04-12
So is this telling me I need a driver for my cdr?

---

### Post by SteveNorman on 2008-04-13
hello?

---

