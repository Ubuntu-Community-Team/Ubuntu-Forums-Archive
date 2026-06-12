---
title: "[SOLVED] error with removable drive &amp;amp; media program"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-03-25
when I click System > Preferences > Removable drive & media I get this error 

[I]The "hald" service is required but not currently running. Enable the service and rerun this application, or contact your system administrator.

Note: You need Linux kernel 2.6 for volume management to work.[/I]

It ran yesterday OK but this morning I installed 7.10 64 bit version, therefore it seems it wont work as it is. 

can someone tell me what I need to get, and how to do it please.

I just checked System > Administration > Services, and do not appear to even have this service to be able to enable it. 

Thanks

---

### Post by Squish on 2008-03-25
A silly question, but have you installed all your updates for your new system yet? Have you restarted the computer yet?

---

### Post by joshrobinson on 2008-03-25
if you run this command, and try again, does it help?

```
sudo /etc/init.d/hal start
```

---

### Post by tropdoug on 2008-03-25
Thank you Josh

the silly questions are usually spot on, and DOH! I had not re booted since updating everything this morning, until right now. I just tried it again and all is OK. Thanks Josh

Douglas:lolflag:

---

