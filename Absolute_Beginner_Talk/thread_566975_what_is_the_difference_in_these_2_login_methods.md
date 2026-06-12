---
title: "what is the difference in these 2 login methods?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by klep on 2007-10-04
hi,

I have a fairly serious problem. Suddenly, when I try to login my computer freezes. That is, when I reach the login screen i have approx 2 seconds before everything freezes (keyboard, mouse etc).

If i go in to single user mode and then issue /etc/init.d/gdm start I can log in without problem.


What is different between these two methods? Why doesn't this also lock up? I really need to solve this problem quickly. 

Thank you for your help.

---

### Post by zekica on 2007-10-04
When you choose single mode, it doesn't start any of services that are running in multiuser mode. You then only type: **/etc/init.d/gdm start** and this starts only gdm. You can try typing: **init 2** and see if it freezes, because then it will start all services as a normal boot.

You can (from single mode) go to **/etc/rc2.d** and see all scripts that start services when you choose normal boot. You can move some of scripts here to another folder (for example you can create **rcbackup** in root's home folder (**/root**). You can move one by one file and see which one causes the problem.

---

