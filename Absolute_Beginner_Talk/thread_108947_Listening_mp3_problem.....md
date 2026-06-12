---
title: "Listening mp3 problem...."
date: 2005-12-27
forum: Absolute Beginner Talk
---

### Post by \root\home\ on 2005-12-27
I have read on this forum if i want to listen mp3 i need to download gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb so i have download it and try to install it with this command :

sudo dpkg -i /home/zlatan/Desktop/gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb

And i got this error :

Selecting previously deselected package gstreamer0.8-mad.
(Reading database ... 56661 files and directories currently installed.)
Unpacking gstreamer0.8-mad (from .../gstreamer0.8-mad_0.8.11-0ubuntu5_i386.deb) ...
dpkg: dependency problems prevent configuration of gstreamer0.8-mad:
 gstreamer0.8-mad depends on libid3tag0 (>= 0.15.1b); however:
  Package libid3tag0 is not installed.
 gstreamer0.8-mad depends on libmad0 (>= 0.15.1b); however:
  Package libmad0 is not installed.
dpkg: error processing gstreamer0.8-mad (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gstreamer0.8-mad


Please can you helo me to listen mp3 and ubuntu is perfect :)

---

### Post by Pablo_Escobar on 2005-12-27
Type in 
> sudo apt-get install gstreamer0.8-mad

but make sure You have multiverse enabled in /etc/apt/sources.list.

---

### Post by \root\home\ on 2005-12-27
I got this error message :

Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-mad is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-mad has no installation candidate

I think that i dont have respositories list or something, can u help me to fix that and how to do that ? Because i also try to download bitchx and i cant download it.... :(

---

### Post by chimera on 2005-12-27
try mp3blaster

get it with

sudo apt-get install mp3blaster

start it with

mp3blaster

---

### Post by xmastree on 2005-12-27
[QUOTE=\root\home\]I have read on this forum if i want to listen mp3 i need to download gstreamer[/QUOTE]The trouble with linux is that there are as many opinions as there are ways to do something.
If you want to listen to MP3s, go to synaptic, find XMMS and install that. It's basically a winamp clone.

---

