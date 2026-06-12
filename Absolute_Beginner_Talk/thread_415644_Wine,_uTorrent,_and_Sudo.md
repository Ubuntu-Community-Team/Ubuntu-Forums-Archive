---
title: "Wine, uTorrent, and Sudo"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-04-20
In order to use uTorrent, I notice that I have to sudo into wine in order to run it. I have to do:

sudo wine "I:\utorrent.exe" in order to open up the program and for the program to save its settings. I was wondering why I need to use sudo to use wine? If I have to use sudo, I cannot create a launcher on the desktop.

How can I configure wine so that it does not need sudo? Thanks!

---

### Post by dpar on 2007-04-20
I don't use wine, so I'm afraid I can't answer that, but I was wondering why you don't use ktorrent? It's pretty much the same thing.

---

### Post by markl187ld on 2007-04-20
Check the file properties and see if your are the owner of utorrent.exe

---

### Post by rai4shu2 on 2007-04-20
Make sure you're running winecfg normally (without sudo).

Try running without sudo in a terminal and see what happens. You really shouldn't need to use sudo.

---

