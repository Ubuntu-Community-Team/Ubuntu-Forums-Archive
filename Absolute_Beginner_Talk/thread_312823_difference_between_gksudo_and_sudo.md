---
title: "difference between gksudo and sudo"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by rajeev1204 on 2006-12-05
hi

could someone tell me the main difference between sudo and gksudo .

and what different uses does either of the commands have


thanks

rajeev

---

### Post by RAOF on 2006-12-05
gksudo puts up a graphical password prompt, and won't mess up GUI logons when used to run graphical apps.

sudo is basically just a terminal version of gksudo.  It doesn't understand X apps, and so it's occasionally possible for an important file to be owned by root if you use sudo to launch graphical programs.  If that happens, you'll be unable to logon graphically, and will need to re-own the files in your home directory.

---

### Post by Voxxi on 2006-12-05
Psychocats has a great page explaining the differences, and when to use either sudo or gksudo. 

[Here]("http://www.psychocats.net/ubuntu/graphicalsudo") it is.

---

### Post by rajeev1204 on 2006-12-05
hi

thanks man

---

### Post by nickoli_02 on 2007-02-10
good to know! I never knew there was a reason to use one over the other :)

---

### Post by %hMa@?b&lt;C on 2007-02-10
just a note to aysiu, you should updayte that page to include **kdesu** because a good portion of ubuntu users enjoy the KDE desktop environment.

---

