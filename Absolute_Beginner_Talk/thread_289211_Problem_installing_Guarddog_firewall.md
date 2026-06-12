---
title: "Problem installing Guarddog firewall"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by vince vega on 2006-10-30
I've been attempting to install the Guarddog firewall, and I'm running into a problem. It's telling me that: /etc/rc.firewall does not exist .Any help would be greatly appreciated. 

vega@desktop:~$ sudo apt-get install guarddog
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gawk
The following NEW packages will be installed:
  gawk guarddog
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 954kB of archives.
After unpacking 3445kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main gawk 1:3.1.5.dfsg-4 [466kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe guarddog 2.5.0-1ubuntu1 [488kB]
Fetched 954kB in 5s (182kB/s)    
Selecting previously deselected package gawk.
(Reading database ... 93501 files and directories currently installed.)
Unpacking gawk (from .../gawk_1%3a3.1.5.dfsg-4_i386.deb) ...
Selecting previously deselected package guarddog.
Unpacking guarddog (from .../guarddog_2.5.0-1ubuntu1_i386.deb) ...
Setting up gawk (3.1.5.dfsg-4) ...

Setting up guarddog (2.5.0-1ubuntu1) ...
Unable to start guarddog firewall - /etc/rc.firewall does not exist

---

### Post by Tanker Bob on 2007-01-13
I know that yours is an older message, but I just did this last night.  That message is simply telling you that guarddog hasn't run the first time.  It creates that file after you run it the first time.  All works well after that.

---

