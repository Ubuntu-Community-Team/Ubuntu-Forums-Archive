---
title: "to view process id"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by hammad1337 on 2008-03-02
the "ps" command gives the process ids of processes running thru a particular terminal
which commant should i use to view the process ids of all processes system-wide...including those not running in a terminal?

---

### Post by Yes on 2008-03-02
Try 'top'.

---

### Post by brunolabs on 2008-03-02
ps -e

---

### Post by hammad1337 on 2008-03-02
Thanks.
ps -e is what i was actually looking for.
top is also a good discovery :)

---

### Post by Oldsoldier2003 on 2008-03-02
> **hammad1337 said:**
> Thanks.
ps -e is what i was actually looking for.
top is also a good discovery :)
ps -e is great but i'm a big fan of ps aux and ps -eF

---

