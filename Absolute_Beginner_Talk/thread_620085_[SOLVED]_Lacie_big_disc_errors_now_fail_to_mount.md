---
title: "[SOLVED] Lacie big disc errors now fail to mount"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by hogwartsnigel on 2007-11-22
Hi all,
I've been having niggly errors with my usb drive..it is formatted to ntfs and has a single partition it is 1Tb. Commonly it has come up with errors after using for a short time, the last time it did this I promised to move everything to a back up usb drive and reformat to ext3...haven't been able too and now it fails to mount I have 180gb of music , stored elsewhere but unorganised (took 2 weeks).

I get the following error trying to mount drive
[I]nigel@nigel-ubuntu:~$ sudo mount -t ntfs-3g /dev/sdd5 /media/sdd5
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdd5': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
nigel@nigel-ubuntu:~$ 
[/I]

I am going to try and resolve this without windows any ideas.

Thanks

Nigel

---

### Post by szaka on 2007-11-22
[http://ntfs-3g.org/support.html#ioerror](http://ntfs-3g.org/support.html#ioerror)

---

