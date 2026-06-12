---
title: "Hard drive keeps running every few seconds - SICK OF IT"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by xoros on 2006-06-13
Ok every couple seconds the HD keeps running and I am tired of it.  What service or monitoring program is causing this and is it ok to stop the service? 

I have Kubuntu (dapper)  here is what I see running under system services:
atd
cron
cupsys
dbus
kdm 
klogd
mdadm
sysklogd

Which one is it?  Arrgh I am sick of it.

---

### Post by IYY on 2006-06-13
You could try running: 

lsof / | grep -v mem | less

to list all open files.

---

### Post by xoros on 2006-06-14
Thanks for that command.  I've found it seems it only happens when Firefox is running.... is there some option in firefox that could cause this?

Thanks for the help!

---

### Post by u.b.u.n.t.u on 2006-06-14
My first guess would be an extension? Have you changed the default Firefox at all?

---

