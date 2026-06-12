---
title: "Quick File Search"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by i-am-me on 2007-06-28
Can someone tell a quick file search program for Kubuntu Feisty (similar to Quicksilver would be nice). I don't want Google Desktop and every time I try installing Beagle, I get this:
```
~$ sudo aptitude install beagle
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  libbeagle0 libwv-1.2-3
The following NEW packages will be installed:
  beagle libbeagle0 libwv-1.2-3
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2144kB of archives. After unpacking 6296kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Selecting previously deselected package libbeagle0.
(Reading database ... 129677 files and directories currently installed.)
Unpacking libbeagle0 (from .../libbeagle0_0.2.16.3-0ubuntu4_i386.deb) ...
Selecting previously deselected package libwv-1.2-3.
Unpacking libwv-1.2-3 (from .../libwv-1.2-3_1.2.4-2_i386.deb) ...
Unpacking beagle (from .../beagle_0.2.17-schmidtke1_i386.deb) ...
[I]dpkg: error processing /var/cache/apt/archives/beagle_0.2.17-schmidtke1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libbeagle.so.0.0.0', which is also in package libbeagle0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/beagle_0.2.17-schmidtke1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/I]
Setting up libwv-1.2-3 (1.2.4-2) ...

Setting up libbeagle0 (0.2.16.3-0ubuntu4) ...


```

I've Italicized the problem area.

---

### Post by swisscow on 2007-06-28
Don't know quicksliver but a simple way in a terminal is::

```
sudo update db
```

```
locate filename
```

Works for me

---

### Post by i-am-me on 2007-06-28
> **swisscow said:**
> Don't know quicksliver but a simple way in a terminal is::

```
sudo update db
```

```
locate filename
```

Works for me

The update part doesn't work for me, but the search is quick. That's good. The problem is, I can't actually access the file unless I cd to the directory or launch Konqueror and if there's several files with a certain name, or the part of the name that I know, it's a pain to search.

---

### Post by swisscow on 2007-06-28
My mistake - sorry. The code is:

```
sudo updatedb
```

It's been a long day...

And yep, it's a bit of a pain to then get to the file - but you at least know where it is!

---

