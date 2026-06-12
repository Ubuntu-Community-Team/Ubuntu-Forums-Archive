---
title: "problems in upgrade to 7.10"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by broshe on 2007-10-25
Hello
I tried to upgrade my Xubuntu 7.04 to 7.10.
For some reason the update was not complete.
There are many problems that did not exist before the update:
1. when I try to restart, shut-down or hibernate, I get the message: "Either the password you entered is invalid or the system administrator disallows shutting down this computer with your account".
2. When I try to use the update manager, I get the error message: "E: dpkg was interupted, you must manually run 'dpkg -- configure -a' to correct the problem. E:_cahce-> open () failed, please report.
3. The upgrade added about 1 Gbyte to my system. Apparently, it did not clean up after the installation.

Is it possible to clean the system up ?
How can I repair the installation ?


Thanks
Eli

---

### Post by julian67 on 2007-10-25
as suggested run ```
sudo dpkg -- configure -a
```

---

### Post by DutyDuty on 2007-10-25
Are you actually running 7.04 or 7.10?

---

### Post by broshe on 2007-10-25
I ran:
sudo dpkq --configure -a
It made a lot of work in the terminal window.
I think I am now running 7.10.
One of the problems disappeared: I no longer get an error message when I try to run an upgrade.
However, the other problems remain.
also, I noticed that the system cannot read the disk on key.
What should I try next ?


Thanks
Eli:confused:

---

### Post by julian67 on 2007-10-25
> **broshe said:**
> 
However, the other problems remain.
also, I noticed that the system cannot read the disk on key.


what is disk on key?

---

