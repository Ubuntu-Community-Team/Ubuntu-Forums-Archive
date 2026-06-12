---
title: "[SOLVED] Konica Magicolor with Samba"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by dndrich on 2008-04-10
OK, this is weird.  I am running Ubuntu Gutsy (love it).  Today I installed my Konica Magicolor 2430 DL in Ubuntu.  That is, I have the printer connected to a wireless router, and shared with a Windows deskop machine.  Now, I am running Ubuntu on a laptop with wireless.  When I look for Windows network printers with Samba, it finds this printer.  I verified the share, and installed using the driver (foozmatic).  The first time I tried a test print, no problem.  Printed fine.  Now, for some reason, it won't print!  I tried rebooting the Windows machine, and the Ubuntu machine, same problem.  I print a test page fine from the Windows machine, but still not from Ubuntu.  Ideas here?

---

### Post by dndrich on 2008-04-10
OK, I solved this problem myself.  I did it a different way.  I simply used the HP Jetdirect protocol by using the IP address of the printer and the RAW port.  It now prints just fine over wireless.

---

