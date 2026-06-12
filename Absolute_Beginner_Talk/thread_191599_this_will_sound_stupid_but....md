---
title: "this will sound stupid but..."
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by kamon on 2006-06-07
im looking on how to set up dual moniters. i have all the hardware, now every time i look up how to set up dual moniters im directed to your[http://http://www.tldp.org/HOWTO/Xinerama-HOWTO/intro.html]("http://http://www.tldp.org/HOWTO/Xinerama-HOWTO/intro.html")
page.

the trouble is it says that work " needs to be done from the console with-out X running." my question is what is X. and how will i then get out of it.

---

### Post by Xzallion on 2006-06-07
X is refering to the X Window System which runs the graphics on Ubuntu.  To log in to a session without X boot Ubuntu in recovery mode, recovery mode does not load X.  From there, finish the instructions and then restart, boot into Ubuntu normally.

---

### Post by nalmeth on 2006-06-07
Recovery mode will log you in as root, so if the howto describes using sudo, then ignore the sudo command. YOu can also log into a fail-safe terminal session (as your regular user, meaning sudo will apply) from GDM. Click Session, Failsafe Terminal Session.

---

