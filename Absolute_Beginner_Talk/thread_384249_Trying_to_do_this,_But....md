---
title: "Trying to do this, But..."
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-14
To enable the Universe and Multiverse repositories, edit the /etc/apt/sources.list file and uncomment the appropriate lines:
          
# We want Multiverse and Universe repositories, please

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

I don't know what to edit, this is not detailed enough, I don't want to mess thing up. Could someone tell me what to edit exactly?

---

### Post by Architeuthis on 2007-03-14
You don't have to edit that file; you can enable multiverse too with system>administration>software sources (assuming your using gnome). There you can enable multiverse too.

If you want to do it with the commandline acces the terminal and execute: sudo gedit /etc/apt/sources.list. And then add the two lines you mentioned to the list.

---

### Post by julie_lebou on 2007-03-14
Thanks, problem solved!

---

### Post by xyz on 2007-03-14
Hi again,

A good idea is to keep [THAT LINK BOOKMARKED SOMEWHERE HANDY]("http://www.ubuntuforums.org/showthread.php?t=232059").

I realize there are tons and tons of stuff/links and so on! This can be confusing at first but you'll find lots of links to answer your potential questions in the near futute.

---

