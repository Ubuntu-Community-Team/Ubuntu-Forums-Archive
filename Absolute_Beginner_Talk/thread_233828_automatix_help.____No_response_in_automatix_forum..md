---
title: "automatix help.    No response in automatix forum."
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by tyner100 on 2006-08-10
updater, after trying automatix, anyone know whats happening?


"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

i tried the thing in terminal it said /var/lib/dpkg/lock

"tyner@tyner-desktop:~$ sudo apt-get install -f
Password:
E: Could not get lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tyner@tyner-desktop:~$"

so i went to /var/lib/dpkg

nothing i see to fix it..

"You have 3 broken packages on your system!

Use the "Broken" filter to locate them""




Anyone kno whats happening?

---

### Post by cstudent on 2006-08-10
You can't have Synaptic open and do apt or dpkg stuff in a terminal at the same time.

---

