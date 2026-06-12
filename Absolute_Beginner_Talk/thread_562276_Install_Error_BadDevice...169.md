---
title: "Install Error: BadDevice...169?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by berZirker on 2007-09-28
So here is the error I get when installing something (bittornado here but I tried wine as well)

berzirker@Godzilla:~$ sudo apt-get install bittornado
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  bittornado-gui python-psyco
The following NEW packages will be installed:
  bittornado
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 150kB of archives.
After unpacking, 868kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main bittornado 0.3.17-1 [150kB]
Fetched 150kB in 6s (23.2kB/s)                                                 
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Selecting previously deselected package bittornado.
(Reading database ... 165519 files and directories currently installed.)
Unpacking bittornado (from .../bittornado_0.3.17-1_all.deb) ...
Setting up bittornado (0.3.17-1) ...

berzirker@Godzilla:~$ 

I have followed [http://ubuntuforums.org/showthread.php?t=293023](http://ubuntuforums.org/showthread.php?t=293023) but that didn't work.  I still have a copy of the original /etc/x11/xorg.conf saved as a .backup but I don't think I screwed anything up.  Today has not been a productive day, I'd really just like to fix this and be done with it.:(

---

