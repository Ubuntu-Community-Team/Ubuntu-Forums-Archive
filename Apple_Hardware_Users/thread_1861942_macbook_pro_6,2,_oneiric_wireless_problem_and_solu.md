---
title: "macbook pro 6,2, oneiric wireless problem and solution"
date: 2011-10-16
forum: Apple Hardware Users
---

### Post by pounsg on 2011-10-16
Hi folks,
after installing oneiric on a macbook pro 6,2, wireless did not work and system froze when playing with nm-applet.
lshw -C network shows me that the wireless card was not using the right driver.
blacklisting bcma and brcmsmac modules solve this problem.

---

### Post by Alejandro Castanaza on 2011-10-19
Thank you pounsg, are you able to connect to wireless N networks with oneiric on the mbp 6,2?

---

### Post by pounsg on 2011-10-20
Actually, I don't know. I don't have a n-router to test this...

---

