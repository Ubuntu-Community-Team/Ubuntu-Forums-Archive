---
title: "synaptic conflict"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by David Valentine on 2006-01-20
I used [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) to generate my /etc/apt/sources.list file (using all repositories but kubuntu, cvs and opera), then did sudo apt-get update to get my sources.list processed for synaptic.  Everything went swimmingly during my subsequent update on synaptic (100+ packages updated), except I got an error message about a conflict that read:> E: /var/cache/apt/archives/libfame-0.9_0.9.0-0.1_i386.deb: trying to overwrite `/usr/lib/libfame-0.9.so.0.0.0', which is also in package libfame0  I worked with it some, and found essentially that dvdrip wants to install libfame-0.9, while libfame0 is depended on by gstreamer plugins.  The descriptions of both libfame packages are very similar.  Thus I can install either dvdrip or gstreamer, but not both.  How do I get around this?

I'm running ubuntu 5.10 (breezy) k7 on a 32-bit amd athlon.  

Thanks in advance for any help.

---

