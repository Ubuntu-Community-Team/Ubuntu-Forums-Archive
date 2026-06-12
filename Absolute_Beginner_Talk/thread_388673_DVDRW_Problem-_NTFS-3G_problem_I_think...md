---
title: "DVDRW Problem- NTFS-3G problem I think.."
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-03-19
running 6.0.6lts...
right basically i screwed up my ntfs read/write viewing.tried loads of different methods on top of each other instead of doing it one by one:$
now even when i plug in my 2gb pen drive it says this:
ntfs signature is missing.

failed to startup volume: invalid argument

failed to mount '/dev/sda1': invalid argument

the device '/dev/sda1' doesn't have a valid ntfs.

maybe you selected the wrong device? or the whole disk instead of a

partition (e.g. /dev/hda, not /dev/hda1)? or the other way around?

how do i fix this and how do i remove all traces of installing ntfs-3g etc and all the things that i've done in terminal.otherwise how do i fix it.

i get things like: (BEWARE LONG LIST)

this for either sda1 or sdb1 and they are the drives:

root@mypc:~# sudo umount /dev/sda1
umount: /dev/sda1: not mounted
root@mypc:~# sudo mount -a
NTFS signature is missing.
Failed to startup volume: Invalid argument
Failed to mount '/dev/hda2': Invalid argument
The device '/dev/hda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
Volume is scheduled for check.
Please boot into Windows TWICE, or use the 'force' mount option.
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
Boot Windows and shutdown it cleanly, or if you have a removable
device then click the 'Safely Remove Hardware' icon in the Windows
taskbar notification area before disconnecting it.
Or
Run 'ntfsfix' on Linux unless you have Vista, then mount NTFS with
the 'force' option read-write, or with the 'ro' option read-only.
Or
Mount the NTFS volume with the 'ro' option in read-only mode.
root@mypc:~#

EDIT:

oh and this

root@mypc:~# df -h
Filesystem Size Used Avail Use% Mounted on
varrun 506M 80K 506M 1% /var/run
varlock 506M 4.0K 506M 1% /var/lock
udev 506M 128K 506M 1% /dev
/dev/hdb2 190G 77G 113G 41% /media/200GBMAXTOR
/dev/hda1 35G 8.9G 26G 26% /media/WINDOWS


Cheers for any input.I'd REALLY like this working so whenever i plugin a pendrive or ntfs i can use it.
cheers:D

---

### Post by keef247 on 2007-03-19
i get this:
mount: no medium found

mount: no medium found

error: could not execute pmount

have had problems setting up ntfs-3g but don't think i touched any cdrw lines...
help please.
much appriciated.

---

### Post by Thirsteh on 2007-03-19
What command are you executing when you get this error? What application are you trying to run? Is there actually a drive at the specified location?

---

### Post by keef247 on 2007-03-19
lol turns out it was nothing.i have my case open and when booting had pulled ide cable out then connected it whilst in ubuntu but forgotten about this.now restart and its fine.cheers anyway people.

---

