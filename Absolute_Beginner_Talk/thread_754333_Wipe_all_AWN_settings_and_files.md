---
title: "Wipe all AWN settings and files"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-04-13
I've uninstalled AWN as it messed up and now re installed it. All my settings are still there. I've looked under home the .config file and delelted my awn files an they are still there..

I want to wipe all traces of awn and then re install it (like when I first installed awn).

---

### Post by otrojake on 2008-04-13
Have you done a whereis for AWN/avant-window-navigator/avant-window-navigator-bzr?  That might tell you where some of its other parts are hanging out...

```
whereis avant-window-navigator
```  for example.

---

### Post by bluebyt on 2008-04-13
Look at the end of the howto to remove AWN:

[http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981")

---

### Post by bubba_169 on 2008-04-13
Did you install with apt-get, synaptic or from a .deb package? If so then this should do the trick...

```
sudo apt-get purge avant-window-navigator
```

AWN will probably need to be installed for you to be able to purge all the files and settings.

---

