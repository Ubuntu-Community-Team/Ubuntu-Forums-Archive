---
title: "Problems with Add/Remove in Gutsy"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by doctorbighands on 2007-10-22
I'm in a new installation of Gutsy, and I can't seem to install anything from Add/Remove. As an example, here's what it said in the box where the program description should be when I went to install Amarok:

"Canonical Ltd. provides technical support and security updates for Amarok
Amarok cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

Every program listed in Add/Remove gives me exactly the same message. What gives??

---

### Post by doctorbighands on 2007-10-22
I opened my sources.list file to discover that every single source link in the list had been commented! I then UNcommented those URLs, and all now seems to be well.

---

### Post by FredB on 2007-10-22
Looks like you installed your ubuntu when servers were a little overwhelmed ;)

---

### Post by bigr00 on 2007-10-24
problem fix confirmed
I installed my ubuntu 7.10 totally offline, so that must have been the problem.

---

