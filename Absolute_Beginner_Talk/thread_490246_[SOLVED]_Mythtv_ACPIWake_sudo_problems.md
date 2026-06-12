---
title: "[SOLVED] Mythtv ACPIWake sudo problems"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by El_Matthews on 2007-07-02
I am trying to configure my mythtvbox to automatically shutdown and wake when needed. I followed following doc: [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake?action=show]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake?action=show")

to correctly wake up the mythtv user should be able to launch the following command:```
sudo sh -c 'echo "2007-12-12 12:12:12" > /proc/acpi/alarm'

```
I added the following lines to visudo:```
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/MythShutdown
``` but this doesn't seem to work.
example when I run the command manually```
mythtv@wsubu:/home/mg$ sudo sh -c 'echo "2007-12-12 12:12:12"
> /proc/acpi/alarm'
Sorry, user mythtv is not allowed to execute '/bin/sh -c echo
"2007-12-12 12:12:12" > /proc/acpi/alarm' as root on wsubu.

```

What can I do to make this work ?

---

### Post by El_Matthews on 2007-07-03
nobody an idea how I can solve this sudo problem ?

would a script be able to solve this ? (writing a script executing the command and giving sudo rights to this script).

PS: I tried writing this as a script but my bash knowledge is very limited ;)

---

### Post by El_Matthews on 2007-07-17
Written script and everything works now (except mythwelcome). thread can be closed

---

