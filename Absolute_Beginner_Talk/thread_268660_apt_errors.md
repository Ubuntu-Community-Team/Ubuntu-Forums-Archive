---
title: "apt errors"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-09-30
i can't get around this. please help!

```
shane@shane-desktop:~$ sudo aptitude install xserver-xgl compiz-gnome emerald emerald-themes beryl
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  compiz-core libglitz-glx1 libglitz1
The following NEW packages will be installed:
  compiz-core compiz-gnome libglitz-glx1 libglitz1 xserver-xgl
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1909kB of archives. After unpacking 4989kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 92551 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_0.0.13.38-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.38-0ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz.real', which is also in package compiz-vanilla
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_0.0.13.38-0ubuntu3_i386.deb) ...
Unpacking libglitz1 (from .../libglitz1_0.5.6-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libglitz1_0.5.6-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libglitz.so.1.0.0', which is also in package glitz-cvs
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libglitz-glx1_0.5.6-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libglitz-glx.so.1.0.0', which is also in package glitz-cvs
Selecting previously deselected package xserver-xgl.
Unpacking xserver-xgl (from .../xserver-xgl_7.0.0+cvs20060625_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-core_0.0.13.38-0ubuntu3_i386.deb
 /var/cache/apt/archives/libglitz1_0.5.6-0ubuntu1_i386.deb
 /var/cache/apt/archives/libglitz-glx1_0.5.6-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of xserver-xgl:
 xserver-xgl depends on libglitz-glx1; however:
  Package libglitz-glx1 is not installed.
 xserver-xgl depends on libglitz1 (>= 0.5.1+cvs20060213); however:
  Package libglitz1 is not installed.
dpkg: error processing xserver-xgl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of compiz-gnome:
 compiz-gnome depends on compiz-core (= 0.0.13.38-0ubuntu3); however:
  Package compiz-core is not installed.
dpkg: error processing compiz-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xserver-xgl
 compiz-gnome

```

---

### Post by shanepardue on 2006-09-30
in other words my compiz and xserver-xgl are both corrupt and i can neither remove them or reinstall them. please help!

---

### Post by shanepardue on 2006-09-30
maybe this will help? i'm trying to give as much info as i can for some kinda of reply. i need help! i think this is the package that is throwing everything off.

```
Unpacking libglitz1 (from .../libglitz1_0.5.6-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libglitz1_0.5.6-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libglitz.so.1.0.0', which is also in package glitz-cvs
Errors were encountered while processing:
 /var/cache/apt/archives/libglitz1_0.5.6-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by shanepardue on 2006-10-01
guess i'll reinstall ubuntu then. bleh

---

### Post by kuriharu on 2006-10-15
Dude, I read you loud and clear. I get the exact same error on my system and it worked just 24 hours ago!

I think the next person who says "Linux has better support than Windows" is someone I'm gonna have to kick their ***!! I put two posts on Ubuntu forums and didn't get a reply. This is one area where Linux sucks Donkey D*ck.

---

### Post by Jaymo on 2006-10-16
I just installed Compiz through Automatix Bleeder and I am getting the same issues.

I hope someone here has a resolution for this problem :O.

This is not a Linux problem, this is a Compiz problem; I would at least try to direct the anger towards the correct channels if I were you Kuri :).

---

### Post by kuriharu on 2006-10-16
<rant>
Actually, this IS a Linux problem; it's happened to me about 3 times now. I update packages, and other packages get broken. When I try to fix the 'broken' packages, I've had to downgrade other packages to fix the 'updated' packages.

If the above statement makes little or no sense, you now know how I've felt, spending hours trying to get software that previously worked to a working state after an update. ](*,) 

Maybe this is more of an Ubuntu problem rather than Linux itself. But one of the selling points over proprietary software is that Linux/other open source software is superior because updates happen frequently. If so called updates break the original package (or others), how are the frequent updates an advantage?:-k 

People harp on MS for their updates coming out late. Granted, that's true, but most MS updates are well tested and tend to NOT break other software on a Windows machine. I like Linux a lot, but this is one area where it trails other OS's.
</rant>

---

