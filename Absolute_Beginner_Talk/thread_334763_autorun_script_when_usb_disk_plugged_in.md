---
title: "autorun script when usb disk plugged in?"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by joey_joe_joe on 2007-01-09
Hi All,
I'm trying to run a shell script automatically every time a usb storage device is plugged in/out. I have seen several people asking this question, on this forum and others, but have not found a solution yet.
I believe that any file in /etc/dev.d/default/ with extension .dev should run when usb device is added or removed? I have also tried adding a rule to /etc/udev/rules.d but this has not worked either. also, from what i have, udev is the replacement for hotplug?? I have seen several sites suggesting use of hotplug and /etc/hotplug files, but these do not exist on my system, 6.06 dapper. 

If anyone can talk me through what is involved in setting this up, using hotplug, dev or any other method, it would be much appreciated.

Thanks.

---

### Post by joey_joe_joe on 2007-01-10
if anybody is wondering about this, i found a solution.
 
the hotplug method is now deprecated apparently, and the method of choice is to create a rule in /etc/udev/rules.d directory. see 'man udev' for detailed info on rule creation.

Example rule:
SUBSYSTEM=='block', RUN+="/usr/bin/something"
 
save to file in /etc/udev/rules.d and call it something like 99-myrule.rules. restart udev service. /usr/bin/something should now be executed when you plug in usb disk.

---

