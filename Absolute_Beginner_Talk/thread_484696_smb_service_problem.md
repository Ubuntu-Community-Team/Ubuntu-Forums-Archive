---
title: "smb service problem"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by samith on 2007-06-26
guyzzz...

when i try to start , stop or restart samba service. im getting a error call   "smb:unrecognized service"    the command i used is  "service smb start "

Thanx :(:(:(:(:(

---

### Post by samith on 2007-06-26
someone please help me.. I'm trying to do this since today morning..:(:(:(:(:(:(

---

### Post by Gomek on 2007-06-27
try ```
sudo /etc/init.d/samba start
```

---

### Post by Gallows on 2007-06-30
service is a Redhat command but if you used ```
service smb start
``` and got a sensible error back then maybe the name of the service is incorrect.  Try ```
service samba start
```

---

### Post by Seisen on 2007-06-30
What Gomek said is the correct way to start, stop or restart Samba.

---

### Post by tarek on 2007-06-30
Did you install samba?

---

