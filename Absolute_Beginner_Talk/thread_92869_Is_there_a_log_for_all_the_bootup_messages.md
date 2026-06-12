---
title: "Is there a log for all the bootup messages?"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-11-20
If I have the following text during bootup,

* Initializing modules...    [ok]
* Cleaning up ifupdown...   [ok]
* Loading modules...   [ok]
*Setting the system clock.   [ok]..
* Setting up LVM Volume Groups...   [ok]
*Starting Enterprise Volume Management System...   [ok]
*Checking all file systems...   [ok]
.
.
.
* Starting Comon Unix Printing system: cupsd   [fail]
Starting OpenLDAP: running BDB recovery, slad - failed
The operation failed but no output was produced.
* Starting Samba daemons...   [ok]
* Starging web server (Apache2)...   [fail]

Is there a log for all these messages? I check with dmesg, but it does not have the all the output. In fact, correct me if I'm wrong, it does not have a log of the status of all the daemons (ok or fail).

Thanks !

---

### Post by apjone on 2005-11-20
dmesg | tail

---

### Post by towsonu2003 on 2005-11-20
try looking under /var/log for log files. you can use "system log" under "system tools" to open, see, monitor, or close those files tho some will be unaccessible to regular user (non-root).

---

