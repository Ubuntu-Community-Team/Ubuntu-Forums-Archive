---
title: "ndiswrapper errors"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Zargon2000 on 2007-04-28
When trying to install the net5513.inf file for my wireless using ndiswrapper, it seems to install okay.  But when I do a "ndiswrapper -l" to list, it lists net5513 with an error "invalid driver".  I downloaded the latest net5513.inf from D-Link.  Do I need to use one that is specifically for Linux?  Thanks

---

### Post by Kobalt on 2007-04-29
Ndiswrapper does not only need a xxx.inf file, it also needs a xxx.sys : did you point to ndiswrapper the location to the full archive for the drivers and not the .inf file only ?

---

### Post by Zargon2000 on 2007-04-30
Oh yeah.  That was it!  Thanks for your help.

---

