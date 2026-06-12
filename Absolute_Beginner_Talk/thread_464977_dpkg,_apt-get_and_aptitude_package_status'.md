---
title: "dpkg, apt-get and aptitude package status'"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by TheFuzzy0ne on 2007-06-05
Hi everyone.

I'm a little bit stuck with using the CLI based package managers.

Each package has a letter to the left, which I guess defines the status of a package(?).

I can see that:

i = installed
p = package
v = virtual package
B = Broken
A = Auto-installed

Now I can see a "c" by some of my packages, and I'm unsure of what this means. Is there some kind of reference that will tell me what all of these could mean? I've scanned the man pages for aptitude, apt-get and dpkg and they didn't seem to help much...

My problem is that I can install Kino (marked with a "c"), but kinoplus refuses to install, and give me various errors.

me@my-comp:~$ sudo apt-get install kinoplus
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed
  kinoplus
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/83.7kB of archives.
After unpacking 287kB of additional disk space will be used.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
(Reading database ... 224044 files and directories currently installed.)
Unpacking kinoplus (from .../kinoplus_0.3.5-3build1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/kinoplus_0.3.5-3build1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kino-gtk2/libkinoplus.so', which is also in package kino
Errors were encountered while processing:
 /var/cache/apt/archives/kinoplus_0.3.5-3build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What does this mean? I am assuming that kino depends on one file, but kinoplus perhaps uses a different version and wants to replace it. kinoplus, however, depends on kino. I am so confused... :???:

Many thanks.

Daz.

---

### Post by Daishiman on 2007-06-05
try to uninstall kino then install kinoplus. If that doesn't work, install the .deb package with dpkg -i --force-overwrite your_package.deb, which should overwrite that file, but success is not guaranteed.

---

### Post by TheFuzzy0ne on 2007-06-05
> **Daishiman said:**
> try to uninstall kino then install kinoplus. 

That's what I had been doing. :)

> **Daishiman said:**
> 
If that doesn't work, install the .deb package with dpkg -i --force-overwrite your_package.deb, which should overwrite that file, but success is not guaranteed.

Thanks for your input. Any idea what the "c" is?

---

### Post by AncientPC on 2008-03-18
I believe 'c' stands for configuration files.  You may have installed / removed a package, but the config files still remain for it.

Edit: You can also find out what all the flags are by running aptitude, typing '?' to go to the help screen, and scrolling down about a page or two.

---

