---
title: "Can't install Jokosher  :`("
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Stickymaddness on 2007-05-09
After very excitedly finding out about Jokosher, I immediately attempted what I expected to be a simple install... 

Anyone know how to fix? I'm lost...:confused:

---

### Post by Kobalt on 2007-05-09
How did you attempt to install Jokosher : compile or .deb ? It looks like a dependencies problem toward gstreamer to me ...

---

### Post by Stickymaddness on 2007-05-09
Doh!

I wasn't aware that there was a .deb file! I used [this]("http://www.jokosher.org/download#ubuntu") to install Jokosher, only know do I notice that it is for Edgy and dapper, and I'm running Feisty.

I completed the installation using synaptic, and the program runs! Only problem is, when I attempt to play, I get the following error. I tried re-installing everything again, but still no luck!

---

### Post by Stickymaddness on 2007-05-10
Hmm, I have just found [https://bugs.launchpad.net/jokosher/+bug/108921]("https://bugs.launchpad.net/jokosher/+bug/108921")

---

### Post by Kobalt on 2007-05-10
There is a Gstreamer-gnonlin package in the repos, you can try to install that and see if it works...

---

### Post by Stickymaddness on 2007-05-10
Cool, I'll give that a try since the link to the cvs is down for maintenance :(

---

### Post by xyz on 2007-05-10
Did you try Add/Remove > Search > Jokosher?

---

### Post by Stickymaddness on 2007-05-10
> **Kobalt said:**
> There is a Gstreamer-gnonlin package in the repos, you can try to install that and see if it works...

I had it installed already, but I re-installed it, which fixed my error! However, If I hit play, then stop, then play again it wouldn't play.

> **xyz said:**
> Did you try Add/Remove > Search > Jokosher?

This broke it again, and now I'm back to square one with the same error. Re-installing Jokosher or Gstreamer-gnonlin doesn't fix this problem now.


I wonder if the playback problem was related, or if that's a whole different problem?

---

### Post by Stickymaddness on 2007-05-10
I tried

```

sudo apt-get upgrade gstreamer0.10-gnonlin

Which gave:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

But somehow I now have playback again. Everything seems to work fine, but once I stop playback everything locks up.

---

### Post by Najand on 2007-05-10
The package must be at universe repositories:
> Package: gstreamer0.10-gnonlin
State: not installed
Version: 0.10.7-1
Priority: optional
Section: universe/gnome
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 188k
Depends: libc6 (>= 2.5-0ubuntu1), libglib2.0-0 (>= 2.12.9), libgstreamer0.10-0 (>=
         0.10.11cvs20070110), libxml2 (>= 2.6.27)
Description: non-linear editing module for GStreamer
 GStreamer is a streaming media framework, based on graphs of filters which operate on media
 data.  Applications using this library can do anything from real-time sound processing to
 playing videos, and just about anything else media-related.  Its plugin-based architecture
 means that new data types or processing capabilities can be added simply by installing new
 plug-ins. 
 
 Gnonlin is a set of GStreamer elements to ease the creation of non-linear multimedia editors.
 It works together with the GStreamer multimedia framework to give developers a powerful and
 flexible set of tools for quickly assembling applications which needs to handle non-linear
 multimedia editing. 
 
 This package contains the GStreamer plugins for Gnonlin.


---

### Post by Stickymaddness on 2007-05-10
Yep, it is and I have 0.10.7-1 installed, but Jokosher still locks up after stopping playback...

---

