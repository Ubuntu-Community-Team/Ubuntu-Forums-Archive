---
title: "gedit"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by lunamystry on 2007-07-22
so I installed kubuntu on my PC removing ubuntu(gnome) and now i want to get compiz fusion to and I do this in the terminal:

> lunamystry@pardus:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
lunamystry@pardus:~$ sudo aptitude install gedit
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be installed:
  docbook-xml gedit gedit-common libenchant1c2a liblaunchpad-integration0
  libscrollkeeper0 scrollkeeper sgml-data
0 packages upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3225kB of archives. After unpacking 25.4MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main sgml-data 2.0.3 [279kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main docbook-xml 4.4-5 [338kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main libenchant1c2a 1.3.0-2ubuntu1 [162kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main liblaunchpad-integration0 0.1.13 [13.3kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main libscrollkeeper0 0.3.14-11ubuntu7 [49.7kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main scrollkeeper 0.3.14-11ubuntu7 [187kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main gedit-common 2.18.1-0ubuntu1 [1445kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main gedit 2.18.1-0ubuntu1 [750kB]
Fetched 3225kB in 35s (91.1kB/s)
Selecting previously deselected package sgml-data.
(Reading database ... 117541 files and directories currently installed.)
Unpacking sgml-data (from .../sgml-data_2.0.3_all.deb) ...
Selecting previously deselected package docbook-xml.
Unpacking docbook-xml (from .../docbook-xml_4.4-5_all.deb) ...
Selecting previously deselected package libenchant1c2a.
Unpacking libenchant1c2a (from .../libenchant1c2a_1.3.0-2ubuntu1_i386.deb) ...
Selecting previously deselected package liblaunchpad-integration0.
Unpacking liblaunchpad-integration0 (from .../liblaunchpad-integration0_0.1.13_i386.deb) ...
Selecting previously deselected package libscrollkeeper0.
Unpacking libscrollkeeper0 (from .../libscrollkeeper0_0.3.14-11ubuntu7_i386.deb) ...
Selecting previously deselected package scrollkeeper.
Unpacking scrollkeeper (from .../scrollkeeper_0.3.14-11ubuntu7_i386.deb) ...
Selecting previously deselected package gedit-common.
Unpacking gedit-common (from .../gedit-common_2.18.1-0ubuntu1_all.deb) ...
Selecting previously deselected package gedit.
Unpacking gedit (from .../gedit_2.18.1-0ubuntu1_i386.deb) ...
Setting up sgml-data (2.0.3) ...

Setting up docbook-xml (4.4-5) ...

Setting up libenchant1c2a (1.3.0-2ubuntu1) ...
Setting up liblaunchpad-integration0 (0.1.13) ...

Setting up libscrollkeeper0 (0.3.14-11ubuntu7) ...

Setting up scrollkeeper (0.3.14-11ubuntu7) ...
Rebuilding the database. This may take some time.

Setting up gedit-common (2.18.1-0ubuntu1) ...

Setting up gedit (2.18.1-0ubuntu1) ...

lunamystry@pardus:~$ sudo gedit /etc/apt/sources.list
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

** (gedit:10865): WARNING **: Throbber animation not found

** (gedit:10865): WARNING **: Throbber fallback animation not found either
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found


should I be worried because the list opened. 

Thank  you for your time.

---

### Post by RomeReactor on 2007-07-22
Hi. Sorry I can't be useful on your problem installing Gedit; However, since you already have Kubuntu, you could use **kdesu** instead of **gksudo** (which you should be using instead of **sudo** for graphical applications), and **kate** instaed of **gedit** when trying to edit text files:
```
kdesu kate /etc/apt/sources.list
```

By the way, I don't think those particular errors are anything to worry about.

---

### Post by lunamystry on 2007-07-22
A CRASH!! 

I am sorry i seem to be getting a lot of problems today and searching for solutions will eat into study time thus i apologise if this should be somewhere else or was previously answered. My windows decorations crashed I think and this came up:

> (no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1226413856 (LWP 11639)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xffffe410 in __kernel_vsyscall ()
#7  0xb7a63df0 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7a65641 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7a999bb in ?? () from /lib/tls/i686/cmov/libc.so.6
#10 0x0000000b in ?? ()
#11 0xbfa3e0d0 in ?? ()
#12 0x00000400 in ?? ()
#13 0xb6efc38e in XftDrawGlyphs () from /usr/lib/libXft.so.2
#14 0xb7aa17cd in ?? () from /lib/tls/i686/cmov/libc.so.6
#15 0x00000002 in ?? ()
#16 0xb7b607a8 in ?? () from /lib/tls/i686/cmov/libc.so.6
#17 0xbfa40cb5 in ?? ()
#18 0xb7b6081c in ?? () from /lib/tls/i686/cmov/libc.so.6
#19 0xbfa3e64b in ?? ()
#20 0x00000000 in ?? ()

is it a compiz problem? how do i solve it? 

Sorry again for my lazyness i hope someone replies. Thank you

---

### Post by AlexenderReez on 2007-07-22
have you enable your card support?hm....are you using nvidia or ati?which guide did you refer to install compiz fusion?

:)

---

### Post by ravenwere on 2007-07-23
Personally if you are time limited stay away from the eye-candy. Wait for its integrated release beginning with, I understand, ubuntu 7.10.

re:

```
X Error: BadDevice, invalid or uninitialized input device 169
 Major opcode: 145
 Minor opcode: 3
 Resource id: 0x0
 Failed to open device
 X Error: BadDevice, invalid or uninitialized input device 169
 Major opcode: 145
 Minor opcode: 3
 Resource id: 0x0
 Failed to open device
```

This problem can be ignored. It is an error message from xorg.conf caused by support for tablet and stylus devices. Getting rid of it involves editing your xorg.conf file. There are numerous howto's on the forum if you really want to address it.

regards,

r

---

