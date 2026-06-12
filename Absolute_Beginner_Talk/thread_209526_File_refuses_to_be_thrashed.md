---
title: "File refuses to be thrashed??"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Blur-king on 2006-07-05
I download a file for the openoffice2.03 but was interrupted. So file appear to be corrupted. Cannot remove file to the trash. " Unable to move to trash, acess denied. Any idea how I can get rid of this file. Thanks...

---

### Post by T700 on 2006-07-05
From the terminal, ```
gksudo nautilus
``` and see if you can delete it from the file browser running as root.  If that doesn't work, you might log out of your session and log back in and then try again.  My guess is that there is some rogue process locking it and yes, you could open up a process manager and kill it, but logging out is a quick and easy solution.

Paul

---

### Post by Blur-king on 2006-07-05
Thanks T700. Nautilus works the file is gone. Thanks again:D

---

### Post by T700 on 2006-07-05
Glad to help.

Paul

---

