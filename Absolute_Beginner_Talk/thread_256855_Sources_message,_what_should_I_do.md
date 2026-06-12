---
title: "Sources message, what should I do?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by RobsterUK on 2006-09-13
When I went into Add/Remove just now it ran an update, then gave me this message:

> W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)


Do I need to worry about this, if so how can I fix it?

---

### Post by Sef on 2006-09-13
You can comment out a line.  Just put a # in front of it.  The # tells the computer to ignore that line.

Applications > Accessories > Terminal

sudo gedit /etc/apt/sources.list

---

