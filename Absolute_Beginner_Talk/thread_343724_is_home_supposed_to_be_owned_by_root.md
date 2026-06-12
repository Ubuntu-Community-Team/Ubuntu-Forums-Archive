---
title: "is home supposed to be owned by root?"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by MkfIbK7a on 2007-01-21
i was alerted to this because my thing said $home/.dmrc file was being ignored

i changed the permission of my user file in home to me and it stopped is home supposed to be owned by root?

---

### Post by Bachstelze on 2007-01-21
/home is indeed owned by root. However, _your_ home (i.e. /home/username) should be owned by you and CHMOD'ed 644.

---

### Post by aysiu on 2007-01-21
/home itself may be owned by root, but /home/wert should be owned by wert.

The problem may have to do with the permissions on the file, not necessarily the ownership.

[This thread](http://ubuntuforums.org/showthread.php?p=2023490) should help you.

---

### Post by MkfIbK7a on 2007-01-21
thx my owner on /home/wert/ was root

no idea how it got that way...

---

### Post by aysiu on 2007-01-21
> **wert613 said:**
> thx my owner on /home/wert/ was root

no idea how it got that way...
The only thing I could think of is this:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by MkfIbK7a on 2007-01-21
no im careful **NOT** to do that for that very reason...

this happend right after trying to install the aim client (which i gave up)

---

