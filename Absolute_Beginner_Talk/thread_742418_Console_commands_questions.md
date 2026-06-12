---
title: "Console commands questions"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by SergeiFranco on 2008-04-01
I am building a kommander script that will work as device manager/system monitor/process manager.
I am having difficulties finding info on commands that will allow me to:
1) disable/enable device - load/unload module? modprobe "module name", -r to remove? or there is a better way?
2) how to find which process using the device/files?
3) view the list of the logged-in users/kick them out?
4) is there easy way of getting CPU usage?
5) what about process management?

Thanks.

Sergei.

---

### Post by alexforcefive on 2008-04-01
> **SergeiFranco said:**
> 
2) how to find which process using the device/files?
3) view the list of the logged-in users/kick them out?

lsof lists open files and the process/user using them. It's got squillions of options, too

users displays the logged in users. Not sure about kicking them

hope this helps a bit!

---

