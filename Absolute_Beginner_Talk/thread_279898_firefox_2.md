---
title: "firefox 2"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-10-18
how do I install firefox 2?!!!! it's a .tar.gz file and i can't seem to find a way to install it! thanks

---

### Post by ciscosurfer on 2006-10-18
If you just want to try it out, you can extract the .tar.gz on your desktop with right-click, extract here.  Open up a terminal, go to the directory that you've extracted, and type in```
./firefox
```Make sure no other instances of firefox are already up and running, otherwise, this command will simply spawn your older firefox.  To install it, you search the forums for many threads that have already been started that address this issue.

---

### Post by Tanath on 2006-10-18
FYI: You don't need to run firefox in a terminal. You can just double-click it in Nautilus (gnome's file browser).

---

### Post by ciscosurfer on 2006-10-18
I was aware of this, but thanks anyways!

---

### Post by jordanmthomas on 2006-10-18
If you do want to install it, the standard way is to copy the firefox folder into /opt

---

### Post by raqball on 2006-10-18
Just a quick thought but why not give swiftfox a try? Version 2 is exact same as firefox 2 but swiftfox is optimized for Linux... And.... It's faaaaast... All your firefox plugins and extensions work as well

---

### Post by raqball on 2006-10-18
> **Mazen said:**
> how do I install firefox 2?!!!! it's a .tar.gz file and i can't seem to find a way to install it! thanks

To install it, extract the file then go to terminal and change directory to where you extracted it, then this:

./configure
make
sudo make install

---

### Post by bruenig on 2006-10-18
> **raqball said:**
> To install it, go to terminal and this:

./configure
make
sudo make install

raqball, firefox has precompiled binaries. You just extract and run it.

---

### Post by raqball on 2006-10-18
> **bruenig said:**
> raqball, firefox has precompiled binaries. You just extract and run it.

Oooooo, I suck! Thanks for setting me straight :)

Ummmmmm, disregard everything I said EXCEPT for checking out Swiftfox :)

---

