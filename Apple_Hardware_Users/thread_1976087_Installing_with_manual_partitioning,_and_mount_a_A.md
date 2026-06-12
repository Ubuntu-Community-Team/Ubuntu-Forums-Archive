---
title: "Installing with manual partitioning, and mount a Apple hfsplus filesystem broken"
date: 2012-05-08
forum: Apple Hardware Users
---

### Post by smurphy on 2012-05-08
FYI - in case you install Ubuntu 12.04, and configure the installer to use /dev/sdax as /Volumes/Media (sharing my iTunes disk between iTunes and Amarok), the installer will mark the partition /dev/sdax as 0007 if it is a GPT partition and propose to format it. If you unmark the format tag, and mount it anyway - the paritititon tag will remain 0007. OS-X won't recognize it any longer.

Fix is under linux, stargt gdisk /dev/sda and put the partition back to AF00 - and you're done.

The funny thing is, that linux recognizes the partition and mounts it without issues even though the partition type is wrong (Reason you probably only realize this when booting back into OS-X).

---

