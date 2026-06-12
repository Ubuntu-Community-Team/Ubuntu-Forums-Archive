---
title: "Vmware server reinstallation problem and download manager"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by mariano.pelizzari on 2007-10-12
I have a problem trying to reinstall vmware server. It can be seen in the image.
Also, can anybody recommend me a good download manager to use with firefox?

Thks

[IMG]http://ibbsa.com.ar/vmware server reinstallation probelm.png[/IMG]

---

### Post by ronald.higgins on 2007-10-12
It looks like it's looking for a file called servies.sh and cannot find it.

run this to see if it's on your system:

"sudo find / -name services.sh"

rH

---

### Post by mariano.pelizzari on 2007-10-12
What an as, I only had to remove the /etc/init.d/vmwar directory.
Thks for your help

---

