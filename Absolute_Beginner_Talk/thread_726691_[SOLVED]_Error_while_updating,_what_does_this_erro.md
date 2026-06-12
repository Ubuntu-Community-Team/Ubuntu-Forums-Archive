---
title: "[SOLVED] Error while updating, what does this error mean?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by udh on 2008-03-16
When I use 'update manager' it says my system is up to date. But when I click 'check' it gives following error message:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
So I ran dpkg command as said above in terminal, but it said I need a 'superuser privilege'.
I have only one account on my system and I suppose it is 'administrator or root'. what is this superuser privilege? How can I run that command and obtain regular updates?
Please take into account that I am using Ubuntu first time, and I had not much knowledge of linux commands. But any help is welcome :)

---

### Post by herbster on 2008-03-16
Superuser means root. You could use "sudo" to run the command:

```
sudo dpkg --configure -a
```

Sudo runs your programs with administrator privileges. The command above will ask you for your user password, type it, hit ENTER and it will proceed.

---

### Post by udh on 2008-03-17
**thanks a lot herbster!**

---

### Post by herbster on 2008-03-17
No sweat bud, mark the thread as SOLVED for others who may run into the same issue :)

---

### Post by udh on 2008-03-17
> **herbster said:**
> No sweat bud, mark the thread as SOLVED for others who may run into the same issue :)

**Done herbster! :guitar:**

---

