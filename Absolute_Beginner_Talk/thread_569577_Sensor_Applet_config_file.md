---
title: "Sensor Applet config file"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by svdb on 2007-10-07
Hi,
A beginner's question for the beginner's forum:
Where does the Hardware Sensors Monitor applet store its preferences?
Thanks.

---

### Post by svdb on 2007-10-07
up

---

### Post by svdb on 2007-10-08
Solved, kind of.
The reason I asked was because I wanted to manually set the preferences since they were not being saved.
I found this bug report about this specific problem:
[https://bugs.launchpad.net/ubuntu/+source/sensors-applet/+bug/94558]("https://bugs.launchpad.net/ubuntu/+source/sensors-applet/+bug/94558")

The version of HDDtemp available through Synaptic should not be used. Instead HDDTemp 0.3 beta 15 should be used.... So, this beta version works better than the release version?... errr... :-k

---

### Post by h0me5k1n on 2008-01-18
I need to revive this post as the title of it is exactly what I'm looking for!!

Where's the config file for the sensors-applet stored for each user?  Mine must be in my home folder somewhere I guess as I've had to set up each user separately.  If I can can find the config file I should be able to port it to other users and other machines with the same hardware instead of doing it manually!!

---

