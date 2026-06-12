---
title: "Help!!!! Cannot Shut Down"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by wcbardwell on 2007-08-08
I am a fool!!! I once crashed my machine and I forgot how... I just remembered. I wanted to install pidgin and remove gaim (because I had heard that pidgin was the same thing as gaim... just updated). However, when I entered:```
$ sudo apt-get remove gaim
``` It uninstalled ubuntu-desktop and a nautilus package that I can't remember. I now believe that I cannot shut down or else I will not be able to log back in... at least that's what happened last time. could ANYONE help me... I've tried to reinstall ubuntu-desktop using ```
$ sudo apt-get install ubuntu-desktop
``` However, it prompts for the CD... Which I don't have with me and can't get without shutting down and messing up my system (I'm in a public computer lab using a portable HDD with Ubuntu 7.10). PLEASE HELP!!!!!

UPDATE
I found and installed the packages necessary and learned my lesson: leave Gaim alone :D

---

### Post by tgm4883 on 2007-08-08
Oh why must people always have the newest best of everything?

well ubuntu-desktop is only a metapackage, so it is not needed.  I don't know if nautilus-sendto is required though, I suppose that you could see if pidgin installed it though.

---

### Post by eapache on 2007-08-08
Pidgin will install fine beside gaim.

---

