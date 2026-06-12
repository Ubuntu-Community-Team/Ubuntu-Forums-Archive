---
title: "Freezes when I try to burn DVD"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by DrQuincy on 2007-05-30
I used to have no problems burning DVDs; now when ever click Burn Disk it freezes.  How can I find out what's wrong?

---

### Post by apjone on 2007-05-30
open a terminal and become root

sudo -s

now type 

tail -f /var/log/messages

leave the terminal open and now try to burn a cd, you should get some text in the terminal that will give you an idea of whats wrong.

---

