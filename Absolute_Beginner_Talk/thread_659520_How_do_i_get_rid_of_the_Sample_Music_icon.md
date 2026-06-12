---
title: "How do i get rid of the Sample Music icon???"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by SiCkGODV3 on 2008-01-05
ok, i have just joined the Ubuntu side and on my desktop i have the sample music icon....when i try to delete it it says access denied... i tryed to do the SUDO SU in termanil and i still cant delete it...HELP??

---

### Post by Sef on 2008-01-05
Are you right clicking on it?  What company is it from?

---

### Post by SiCkGODV3 on 2008-01-06
it came with ubuntu.......it was there when i installed it

---

### Post by bumanie on 2008-01-06
Generally this will work to get rid of folders that deny access. In terminal type
gksudo nautilus
you then should be able to navigate to the folder you want gone and send it to the garbage. Once in the garbage, it should delete as normal. Be careful what you get rid of, it can't be retrieved as gksudo nautilus gets is root for graphical programs.

---

