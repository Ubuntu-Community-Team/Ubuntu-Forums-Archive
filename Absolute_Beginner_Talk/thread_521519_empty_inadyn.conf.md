---
title: "empty inadyn.conf"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by ben22 on 2007-08-09
I have a problem

1) installed inadyn with synaptic pacakge manager
2) inadyn has status "installed"
3) when trying to edit the inadyn.conf it is empty and cannot find it on /etc/ either.


any suggestion?

---

### Post by splintercellguy on 2007-08-09
Try locating it with locate inadyn.conf?

---

### Post by ben22 on 2007-08-09
> **splintercellguy said:**
> Try locating it with locate inadyn.conf?

entering "locate inadyn.conf" into terminal does not produce anything.

---

### Post by riven0 on 2007-08-09
First, update it with **sudo updatedb**. When that's finished try to locate all the inadyn files with **locate inadyn**.

---

