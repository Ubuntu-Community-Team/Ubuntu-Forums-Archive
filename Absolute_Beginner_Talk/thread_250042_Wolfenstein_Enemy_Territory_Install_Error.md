---
title: "Wolfenstein: Enemy Territory Install Error"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by WPAStrangla on 2006-09-03
I been playing around with other Distros and Desktop Environemts and decided to stay with Kubuntu. When trying to install Enemy Territory I get the error shown below.
[IMG]http://img56.imageshack.us/img56/3950/snapshot1ej7.png[/IMG]
Its Probably a simple fix...

---

### Post by steve.horsley on 2006-09-03
The installer script is probably trying to "set user" to root, which it can't do because the root account is disabled. Try gaining root's identity before running the installer, with these two commands:
[B]sudo su
setup.sh[/B]

---

### Post by WPAStrangla on 2006-09-03
I tried what you said and still nothing is working.

---

