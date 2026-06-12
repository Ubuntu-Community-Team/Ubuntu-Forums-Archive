---
title: "Removing compiled software"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Silvr2008 on 2008-03-31
I am trying to remove kismet from my computer. I downloaded the source and installed it this way. When i try *make uninstall* it says:
make: *** No rule to make target `uninstall'.  Stop.

Anyone know how I can remove it?

---

### Post by FreewareFan on 2008-03-31
You need to have the original source directory that you had in the first place to do the make uninstall.  If you don't have it anymore, go and download it again, do the ./configure, and then the make.   After that, you can do the make uninstall from within that directory.

---

