---
title: "How to fix this problem bet Helix and Realplayer??"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by webbie180 on 2007-10-17
Get this error while trying to install Helix, 

E: /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb: trying to overwrite `/usr/share/locale/de/LC_MESSAGES/libgtkhx.mo', which is also in package realplay

And I cant use synatic or apt-get -f install to resolve it, someone pse help...

Now my update-manager not working, have to fix the problem first.

---

### Post by webbie180 on 2007-10-17
This is wat I got from update-manager.


Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by webbie180 on 2007-10-17
This is wat I got from using "sudo apt-get -f install" in a terminal,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  helix-player
The following NEW packages will be installed:
  helix-player
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4062kB of archives.
After unpacking 10.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 172902 files and directories currently installed.)
Unpacking helix-player (from .../helix-player_1.0.6-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de/LC_MESSAGES/libgtkhx.mo', which is also in package realplay
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

How to get around this?

---

### Post by webbie180 on 2007-10-17
Can Helix and Realplayer co-exist in the same system??

---

### Post by jayaramk on 2007-10-17
helix and real player cannot co exist in the system.... its either helix or real player to be installed but not both...... try removing the helix and then try installing real player this will work!!!!

---

