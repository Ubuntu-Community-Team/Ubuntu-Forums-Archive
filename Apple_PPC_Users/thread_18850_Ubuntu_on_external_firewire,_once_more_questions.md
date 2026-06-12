---
title: "Ubuntu on external firewire, once more questions"
date: 2005-03-09
forum: Apple PPC Users
---

### Post by matthis on 2005-03-09
Dear Ubuntu users, I would like some advise on how to make Ubuntu boot from an external firewire drive. This is what I have done so far:

_Install on the firewire drive has been successful, except for yaboot.
_I have therefore from the install CD's console chrooted to the installed root filesystem and manually created a yaboot.conf, then run mkofboot -b /dev/sda2, and then run ybin -v --boot /dev/sda2 --config /ect/yaboot.conf
The result is that can access yaboot when booting my powerbook, and the kernel loads, but I get an error at:
"VFS: Cannot open root device "sda3" or unknown-block (0,30)"
and then it reboots.
/dev/sda3 is where the ubuntu filesystem is installed.

Exactly the same thing happens if at the yaboot prompt I enter "linux root=/dev/sda3"


My yaboot.conf is:
ofboot=fw1/disk@1:
partition=3
timeout=30
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
default=linux
image=/boot/vmlinux
label=linux
root/dev/sda3 ro
initrd=/boot/initrd.img
defaultos=linux
delay=10
enable cdboot

Does anyone know how to make this work? THanks for any help!!

---

### Post by skabber on 2005-03-12
I am looking in to installing ubuntu on my powerbook, using an external firewire drive.  But I am holding off until I have found that it is possible.

isn't this what YellowDog just announced.
[http://www.terrasoftsolutions.com/news/2005/2005-03-09.shtml](http://www.terrasoftsolutions.com/news/2005/2005-03-09.shtml)

---

