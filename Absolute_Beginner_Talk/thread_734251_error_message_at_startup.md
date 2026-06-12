---
title: "error message at startup"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Professor GU on 2008-03-24
I keep getting an error message at startup that reads:

Information-KdeSudo
No command arguments supplied!
Usage: Kdesudo [-u <runas>] <command>
KdeSudo will now exit...


Any comments will be appreciated!

---

### Post by forrestcupp on 2008-03-24
At what part of start up does that take place?  Is it after you log in or before?  If before, is it before the log in screen?

---

### Post by Professor GU on 2008-03-24
It is after the login screen.  The desktop is already loaded, but it is also asking for my admin password for internet and Kontact.

---

### Post by forrestcupp on 2008-03-25
You have some script or app in your KDE session start up that uses kdesudo.  I'm sure if you found out what it is and removed it, all of your problems would be solved.  Unfortunately, I don't know much about KDE, so maybe someone else can direct you how to find your session start up settings.

---

