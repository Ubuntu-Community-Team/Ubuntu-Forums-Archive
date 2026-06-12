---
title: "Cant execute avg because rot owns permissions"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by duderduderini on 2007-05-23
Hi
I installed avg as per the thread but everytime i try to launch i get this error message appears

"Failed to execute child process "/usr/share/applications/avg.desktop" (Permission denied)"
What gives?
I have tried to find answer to no avail..
Thanks Nick
Really trying to become an ex windows addict

---

### Post by Outrunner on 2007-05-23
You need to run it as root

sudo *appname*

or gksudo  *appname* if the respective application has a graphical interface.

---

### Post by duderduderini on 2007-05-23
> **Outrunner said:**
> You need to run it as root

sudo *appname*

or gksudo  *appname* if the respective application has a graphical interface.
HI 
thanks.. where do i run the comand? when i unpack and install avg? I cant edit the avg file in /user/share/applications cause the root owns it?
Im rooted arent i?
Nick

---

