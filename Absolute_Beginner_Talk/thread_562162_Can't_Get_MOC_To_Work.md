---
title: "Can't Get MOC To Work"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by troy1of2 on 2007-09-28
So I tried installing this console app called MOC which stands for Music On Console because it sounded really interesting and I wanted to play around with it. Trouble is, even though both Synaptic and APT say it is already installed, when I try calling 'moc' from the command line I get this:

The program 'moc' can be found in the following packages:
 * libqt4-dev
 * libqt4-dev-kdecopy
 * qt3-dev-tools
Try: sudo apt-get install <selected package>
bash: moc: command not found


Which I don't think has anything to do with the moc I am trying to run. There apparently is another moc which is part of the QT developers tools that the system is getting confused with the moc which is a music on console app. I even tried /usr/bin/moc but it wasn't found there. So how do I get it to work?

Also, here's the output from sudo apt-get install moc to re-iterate that it is already installed:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
moc is already the newest version.
The following packages were automatically installed and are no longer required:
  libmtp5 fftw3 mysql-common libtunepimp5 libifp4 rdiff-backup libpq5
  librsync1 libnjb5 libofa0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Seisen on 2007-09-28
Try this
```
mocp
```

---

### Post by troy1of2 on 2007-09-28
Hey! Now that's more like it. A response that works in 2 minutes, gotta love this forum. Thanks!

---

### Post by santiagoward2000 on 2007-09-29
Hi,
I've been testing moc, it's quite cool. But I'm having a problem. When I play some songs, I hear a static-like noise on the background. It seems to happen with some songs and not with others, and it doesn't seem to depend on the file-type.
Any ideas?

---

### Post by santiagoward2000 on 2007-10-03
Any ideas about this noise? 'cause it's really bugging me!!

---

