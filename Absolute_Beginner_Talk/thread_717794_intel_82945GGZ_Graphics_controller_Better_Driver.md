---
title: "intel 82945G/GZ Graphics controller Better Driver??"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2008-03-07
I have the intel 82945G/GZ Integrated Graphics controller chip in my desktop system.

I am having problems with some games using this controller in wine.

These same games would work perfectly in windows using this controller.

Is there a better driver for this graphics engine for ubuntu?

thanks

---

### Post by sayakb on 2008-03-07
> **linuxjerk said:**
> I have the intel 82945G/GZ Integrated Graphics controller chip in my desktop system.

I am having problems with some games using this controller in wine.

These same games would work perfectly in windows using this controller.

Is there a better driver for this graphics engine for ubuntu?

thanks

If any better driver is available, you would be notified by the update manager. Make sure you have all your repos enabled in the sources.lst file.

---

### Post by linuxjerk on 2008-03-07
I have all 5 boxes checked in software.sources. Is there something I'm missing or not doing?

Maybe it's just not a very good driver??

I tried the 915resolution thing and got this:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  915resolution
0 upgraded, 1 newly installed, 0 to remove and 204 not upgraded.
Need to get 15.5kB of archives.
After unpacking 127kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe 915resolution 0.5.3-0ubuntu1 [15.5kB]
Fetched 15.5kB in 4s (3246B/s)        
Selecting previously deselected package 915resolution.
(Reading database ... 105687 files and directories currently installed.)
Unpacking 915resolution (from .../915resolution_0.5.3-0ubuntu1_i386.deb) ...
Setting up 915resolution (0.5.3-0ubuntu1) ...
Starting 915resolution: Panel id function not supported
*** Your 915resolution was not automatically configured! ***
Please read /usr/share/doc/915resolution/README.Debian then define
MODE, XRESO, and YRESO manually in /etc/default/915resolution .
For now a default will be set, which might be inappropiate.
915resolution.

---

