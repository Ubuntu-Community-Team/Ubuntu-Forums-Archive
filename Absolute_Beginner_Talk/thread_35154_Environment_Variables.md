---
title: "Environment Variables"
date: 2005-05-17
forum: Absolute Beginner Talk
---

### Post by nsegreto on 2005-05-17
Does anyone know where the PATH variable is actually set for system wide availability?

I struggled to be able to set system wide environment variables.  Placing the variable definition in /etc/profile (where the PATH is defined) works fine if you log in as a remote user or if you telnet localhost.  It does not work when you right-click|New Terminal and start a new terminal session.  In fact I logged out of the GDM session and logged in again and it still was not set. 

Apparently placing the definition in /etc/environment does work.  However, it is not necessary to export the variable.  The file /etc/environment only contains the entries:
LANGUAGE="en"
LANG=en_US.UTF-8

I am uncofortable adding env variables and extensions to PATH to /etc/environment since in all other Linux/Unix systems I have worked on it was in the /etc/profile. Moreover, when do the /etc/environment instructions get executed, before or after the instructions that set all the other environment variables.

So the question is, where is the PATH variable really set?  If someone knows the answer, I would like to modify that file.

---

### Post by defkewl on 2005-05-17
/etc/bash.bash_profile

---

### Post by nsegreto on 2005-05-17
Thanks for you prompt reply.  I don't see a /etc/bash.bash_profile and I am running "ubuntu 2.6.10-5-386". If it is a typo then I assume that you meant /etc/bash.bashrc

I am aware that placing env variable defs in that file works.  However, it still does not make sense to me why placing the defs in /etc/profile does not work since it calls /etc/bash.bashrc.   Perhaps gdm is calling bash.bashrc directly.  That may be so but bash.bashrc makes no reference to PATH, therefore the question is still open if anyone knows which file sets the PATH variable.

---

