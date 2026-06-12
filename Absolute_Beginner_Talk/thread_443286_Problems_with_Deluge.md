---
title: "Problems with Deluge"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Montsegur87 on 2007-05-14
Im using [Deluge]("http://en.wikipedia.org/wiki/Deluge_%28BitTorrent_client%29") as my default BT client. Whenever a I try to download 2 o more torrents at the same time Deluge will crash from Desktop and it wont appear in ps -ejH.

I need to know where to locate a log to this sudden crash wheather it is local to the SO or to the program so that I can report the bug.

---

### Post by mejy on 2007-05-14
To get the cause of the crash, run the program from the terminal.  You can find out what command you'll need by selecting the properties of deluge in the menu editor (alacarte).  If the executable is 'python /path/to/file.py' then you might want to install python2.4 and run it with python2.4 (or python-2.4, I forget which).  Sometimes it's an issue with a specfiic version of python.

---

### Post by Montsegur87 on 2007-05-14
Ok , I did that but I forgot to check the Terminal after it crashed. I'll try that this night.

Thanks

---

