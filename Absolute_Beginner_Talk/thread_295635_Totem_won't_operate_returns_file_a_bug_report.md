---
title: "Totem won't operate returns: file a bug report"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-11-08
Totem tried to open/play:

[http://judiciary.senate.gov/hearing.cfm?id=910](http://judiciary.senate.gov/hearing.cfm?id=910)

a webcast from a government hearing.

the feed or stream or whatever returned:

[COLOR="Red"]Totem could not play 'rtsp://avs2.senate.gov/judiciary'.

Internal GStreamer error: negotiation problem.  Please file a bug at [http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer](http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer) .[/COLOR]

The above link is to the United States Senate Hearing. IT IS NOT COPYRIGHTED MATERIAL.

I have used both Automatix and EasyUbuntu as well as following all the steps at Wiki Ubuntu Restricted Formats page, viz:

[http://www.ubuntuforums.org/showthread.php?t=182902](http://www.ubuntuforums.org/showthread.php?t=182902) (top of Ab. Beg. forum)
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)
  and
mark@Lexington:~$ sudo apt-get install gxine
Password:
Reading package lists... Done
Building dependency tree... Done
gxine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
mark@Lexington:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
mark@Lexington:~$

Help! Through Hoary Hedgehog to Breezy Badger to Dapper Drake, Ubuntu remains unable to play any "thing" through Totem, with the exception of audio books from Gutenberg.org.

Why?

---

### Post by Perfect Storm on 2006-11-08
You properly missing something, but it hard to tell what if you say you've done all the links you provided.

Try with mplayer and mplayer mozilla plugin.

---

