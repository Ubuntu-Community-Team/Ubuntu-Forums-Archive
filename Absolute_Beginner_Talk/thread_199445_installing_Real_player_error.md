---
title: "installing Real player error"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by darvina on 2006-06-18
I am installing realplayer as some one suggest on the forum
I recieve this error
How do i fix this problem
sudo dpkg -i realplayer_10.0.7-0.0_i386.deb
Selecting previously deselected package realplayer.
(Reading database ... 62740 files and directories currently installed.)
Unpacking realplayer (from realplayer_10.0.7-0.0_i386.deb) ...
dpkg: dependency problems prevent configuration of realplayer:
 realplayer depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu15.
dpkg: error processing realplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 realplayer

---

### Post by Nikusan on 2006-06-18
[QUOTE=darvina]I am installing realplayer as some one suggest on the forum
I recieve this error
How do i fix this problem
sudo dpkg -i realplayer_10.0.7-0.0_i386.deb
Selecting previously deselected package realplayer.
(Reading database ... 62740 files and directories currently installed.)
Unpacking realplayer (from realplayer_10.0.7-0.0_i386.deb) ...
dpkg: dependency problems prevent configuration of realplayer:
 realplayer depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu15.
dpkg: error processing realplayer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 realplayer[/QUOTE]

Installing Real player is indeed an error ;-)
If you must have it get it from the multiverse repository.

[https://wiki.ubuntu.com/Repositories/Ubuntu?action=show&redirect=AddingRepositoriesHowto](https://wiki.ubuntu.com/Repositories/Ubuntu?action=show&redirect=AddingRepositoriesHowto)

---

