---
title: "Yaboot didn't load"
date: 2008-02-01
forum: Apple PPC Users
---

### Post by Venom_Man on 2008-02-01
on my install i got an error that told me it couldn't install the yaboot and it may be unbootable. what happend and how can i fix it this is my first time trying to install ubuntu and i dont know what to do any help would be great

---

### Post by frog_pilot on 2008-02-02
without any additional information, nobody can halp you.

tell some details about your hardware.
which version of ubuntu do you use?
Did you use alternate or desktop cd for install?
did you use the whole drive/ the whole empty space when you prompted for partitioning during the install?

try to reinstall using the whole drive/ the whole empty space and dont try to partition manually to avoid this problem.

A workaround is using the option-key on startup. If the install went fine besides the yaboot problem, the Linux-Volume will be shown in the OF boot menu.

---

### Post by stream303 on 2008-02-02
Typically I've seen this when trying to install on external firewire drives.  Yaboot is trying to "bless" the internal drive instead of the external.  Getting yaboot to "bless" the external drive can be done, but it's not for the timid. :)

---

### Post by Venom_Man on 2008-02-02
yea im trying to install on an external firewire drive,actually  a ibook in targetdisk mode, im useing the whole disk and im doing the install with a iMac G3 600 mhz with 356 mb of ram. I tryed holding down option but it didn't show up as a bootable drive.

---

### Post by stream303 on 2008-02-02
I've done it with an external firewire, although I had different versions of Ubuntu installed on both internal and external drives.  Here's a little writeup from 2006 that might help:

[http://ubuntuforums.org/showthread.php?t=314237](http://ubuntuforums.org/showthread.php?t=314237)

For the least amount of pain though, I'd just install OSX to the firewire drive, and install Ubuntu to the internal drive.  Saves precious gray-hairs. :)

---

