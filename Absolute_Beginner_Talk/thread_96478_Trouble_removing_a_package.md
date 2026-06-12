---
title: "Trouble removing a package"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by defubar on 2005-11-28
I am trying to remove "libstdc++6" because it is reported as "broken" in Synaptic.  My problem is that when I go to remove it, it wants to uninstall like 90% of everything installed.  What gives?  I just installed it on accident and meant to install "libstdc++5" so I could install my ATI fglrx driver.  Is there any way to do this without uninstalling everything else?

---

### Post by amohanty on 2005-11-29
Try reinstalling it.

AM

---

### Post by matthew on 2005-11-29
Mark it to be uninstalled, then before you hit "Apply" unmark all the other stuff it wants to uninstall at the same time.

---

### Post by akiro.yamamoto on 2005-11-29
Are you sure you didn't install something that conflict with this package...
As far as I know this is one of the main libraries for the distro....
I don't think you should just un-install that file...
Try marking it for re-installation instead and see what additional changes
the system wants to make before you decide...
Wish I could be of more help, but IMHO move with some caution with that lib....
:smile:

---

### Post by ertai on 2005-11-29
This library is a runtime library. You'll defenitly need one to run ubuntu. Can't version 5 and 6 live both on the same computer?? I think they would because some programs are build with version 6 and older packages with version 5.

---

