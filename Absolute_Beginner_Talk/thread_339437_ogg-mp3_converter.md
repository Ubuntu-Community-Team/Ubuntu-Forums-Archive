---
title: "ogg-mp3 converter"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Sniper99 on 2007-01-15
ok, so here is the deal, i have a ubuntu 6.06 machine and a windows computer, i use my windows for everything, and my ubuntu for experimenting and learning about other os' so yeah, i only have the ubuntu hooked up to the net, and i would like to know if anybody knew of any ogg-mp3 converter engines for linux or windows, because my zen vision wont work on gnomad i think so yeah, any advice is greatly appreciated

---

### Post by ComplexNumber on 2007-01-15
> **Sniper99 said:**
> ok, so here is the deal, i have a ubuntu 6.06 machine and a windows computer, i use my windows for everything, and my ubuntu for experimenting and learning about other os' so yeah, i only have the ubuntu hooked up to the net, and i would like to know if anybody knew of any ogg-mp3 converter engines for linux or windows, because my zen vision wont work on gnomad i think so yeah, any advice is greatly appreciated
try soundconverter.

---

### Post by Sniper99 on 2007-01-15
do you know of the exact website that i can download it off of

---

### Post by Sniper99 on 2007-01-15
ok, so i downloaded the file.....i just dont know how to install it......is there any kind of special trick

---

### Post by ComplexNumber on 2007-01-15
> **Sniper99 said:**
> do you know of the exact website that i can download it off of
its in universe repository. have you enabled the universe and multiverse repositories in the synaptic package manager?

---

### Post by jem7v on 2007-01-15
It's in the repositories if you're running Edgy.  It might also be in Dapper, but I don't know.

(edit: Okay, I guess I type slowly.)

---

### Post by Sniper99 on 2007-01-15
well, i have the file, and i extracted the file, i just dont know how to install it.....i am clueless about installs

---

### Post by ComplexNumber on 2007-01-15
> **Sniper99 said:**
> well, **i have the file, and i extracted the file**, i just dont know how to install it.....i am clueless about installs
so i guess that that file you have extracted had the extention tar.gz or tar.bzip2? forget about that file. find synaptic in your menu (its in the system -> administrator menu). then select 'settings' in the menu, then select 'repositories'. this should then look like the screenshot. tick all the boxes, then press 'close'. then press the big 'reload' button (although i think it will prompt you anyway to reload). then search for "soundconverter".

---

### Post by bruenig on 2007-01-15
Just do
```
sudo apt-get install soundconverter
```
If that doesn't work do 
```
cat /etc/apt/sources.list
```
and paste the output here so we can look at it.

---

### Post by Sniper99 on 2007-01-15
this is everything

spencer@spencer-desktop:~$ sudo apt-get install soundconverter
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gstreamer0.8-flac gstreamer0.8-gnomevfs gstreamer0.8-misc
  gstreamer0.8-vorbis libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0
  python-gst
Suggested packages:
  gstreamer0.8-mad
Recommended packages:
  gstreamer0.8-plugins
The following NEW packages will be installed:
  gstreamer0.8-flac gstreamer0.8-gnomevfs gstreamer0.8-misc
  gstreamer0.8-vorbis libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0
  python-gst soundconverter
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1712kB of archives.
After unpacking 5263kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe gstreamer0.8-flac 0.8.12-1ubuntu2 [51.3kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe gstreamer0.8-gnomevfs 0.8.12-1ubuntu2 [50.4kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libgstreamer-gconf0.8-0 0.8.12-1ubuntu2 [36.5kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe libgstreamer-plugins0.8-0 0.8.12-1ubuntu2 [114kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe gstreamer0.8-misc 0.8.12-1ubuntu2 [1252kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe gstreamer0.8-vorbis 0.8.12-1ubuntu2 [54.8kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe python-gst 0.8.3-1 [119kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe soundconverter 0.8.3-0ubuntu3 [33.5kB]
Fetched 1712kB in 16s (104kB/s)
Selecting previously deselected package gstreamer0.8-flac.
(Reading database ... 113498 files and directories currently installed.)
Unpacking gstreamer0.8-flac (from .../gstreamer0.8-flac_0.8.12-1ubuntu2_i386.deb) ...
Selecting previously deselected package gstreamer0.8-gnomevfs.
Unpacking gstreamer0.8-gnomevfs (from .../gstreamer0.8-gnomevfs_0.8.12-1ubuntu2_i386.deb) ...
Selecting previously deselected package libgstreamer-gconf0.8-0.
Unpacking libgstreamer-gconf0.8-0 (from .../libgstreamer-gconf0.8-0_0.8.12-1ubuntu2_i386.deb) ...
Selecting previously deselected package libgstreamer-plugins0.8-0.
Unpacking libgstreamer-plugins0.8-0 (from .../libgstreamer-plugins0.8-0_0.8.12-1ubuntu2_i386.deb) ...
Selecting previously deselected package gstreamer0.8-misc.
Unpacking gstreamer0.8-misc (from .../gstreamer0.8-misc_0.8.12-1ubuntu2_i386.deb) ...
Selecting previously deselected package gstreamer0.8-vorbis.
Unpacking gstreamer0.8-vorbis (from .../gstreamer0.8-vorbis_0.8.12-1ubuntu2_i386.deb) ...
Selecting previously deselected package python-gst.
Unpacking python-gst (from .../python-gst_0.8.3-1_i386.deb) ...
Selecting previously deselected package soundconverter.
Unpacking soundconverter (from .../soundconverter_0.8.3-0ubuntu3_all.deb) ...
Setting up clamav-base (0.88.4-1ubuntu1~dapper1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gstreamer0.8-flac (0.8.12-1ubuntu2) ...

Setting up gstreamer0.8-gnomevfs (0.8.12-1ubuntu2) ...

Setting up libgstreamer-gconf0.8-0 (0.8.12-1ubuntu2) ...

Setting up libgstreamer-plugins0.8-0 (0.8.12-1ubuntu2) ...

Setting up gstreamer0.8-misc (0.8.12-1ubuntu2) ...

Setting up gstreamer0.8-vorbis (0.8.12-1ubuntu2) ...

Setting up python-gst (0.8.3-1) ...

Setting up soundconverter (0.8.3-0ubuntu3) ...
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ComplexNumber on 2007-01-15
just use the synaptic package manager instead.

---

### Post by Sniper99 on 2007-01-15
ok, its actually working, if it doesn't work i will do the synaptic package manager....thank you so much, i have been researching it for a bit and i got nowhere

---

### Post by ComplexNumber on 2007-01-15
so is soundconverter installed now then? i'm not quite sure what you mean when you say " its actually working, if it doesn't work". what's "actually working"?

---

### Post by Sniper99 on 2007-01-15
yes thank you, i just converted a huge file, thank you.....

---

### Post by kinson on 2007-01-15
Btw, I don't think transcoding is a good practice though..since both are lossy formats

[http://en.wikipedia.org/wiki/Transcoding](http://en.wikipedia.org/wiki/Transcoding)

Kinson.

---

