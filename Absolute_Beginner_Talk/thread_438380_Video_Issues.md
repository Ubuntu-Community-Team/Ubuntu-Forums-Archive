---
title: "Video Issues"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-09
HI there, I just whiped my linux and ran a fresh install. Since returning however I've had a big issue. I can get all my music to play and everything but I can't get DVD's to play in totem or any other video player for that matter and when I try to install libdvdcss2 i get this in the terminal:

craig@craig-desktop:~$ sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb(Reading database ... 84049 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu2+build1 (using libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb) ...
Unpacking replacement libdvdcss2 ...
dpkg: dependency problems prevent configuration of libdvdcss2:
 libdvdcss2 depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
dpkg: error processing libdvdcss2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdvdcss2
craig@craig-desktop:~$"

Can anyone help me? For some reason when I put in a dvd itll play up and thats no problem but when I try to get back to the menus Totem closes and when I open totem to try and play a dvd I get the "Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it," error. Can anyone help me!? THanks!! :lolflag:

Also, I used this site :[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/) 

to load em both up and i still get the error!!!!!! I loaded up the  gstream stuff and all that when I first installed ubuntu and then loaded those and these are the problems! :)

---

### Post by Martin on 2007-05-09
have you taken a look at automatix? It makes things a whole lot easier. [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by jargoman on 2007-05-09
libdvdcss2 depends on libc6 (>= 2.5-0ubuntu1); however:
Version of libc6 on system is 2.3.6-0ubuntu20.4.

these lines are telling you that libc6 is outdated. 

this might do the trick

$ sudo apt-get install libc6

It should automatically update to the newest one.

---

### Post by Tumpster on 2007-05-09
craig@craig-desktop:~$ sudo apt-get install libc6
Password:
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
craig@craig-desktop:~$

---

### Post by saxin on 2007-05-09
sudo aptitude update
sudo aptitude upgrade

---

### Post by Tumpster on 2007-05-09
Thank you, after utilizing both I got it to work! :) Much sweetness and regards to you guys!! :)

---

