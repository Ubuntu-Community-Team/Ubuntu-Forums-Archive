---
title: "Software index is broken"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by y6FgBn)~v on 2006-09-18
Tried to install Helix player via Synaptic and started receiving error message:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Ran "sudo apt-get install -f" in terminal and get the following error message:

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  helix-player
The following NEW packages will be installed:
  helix-player
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
Need to get 0B/4062kB of archives.
After unpacking 10.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 118669 files and directories currently installed.)
Unpacking helix-player (from .../helix-player_1.0.6-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de/LC_MESSAGES/libgtkhx.mo', which is also in package realplay
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bwilliams@bwilliams-desktop:~$

Tried unmarking Helix for install but unable to. 

Any suggestions will be appreciated.

Bill

---

### Post by y6FgBn)~v on 2006-09-18
Disregard I believe I fixed it by going back into Synaptic and just removing the one that showed the dependency error with Realplay. After I did that things got back to normal. False alarm thanks anyways #-o 

Bill

---

