---
title: "AVG error"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by zaz_3333 on 2006-10-12
I have just installed AVG following instructions in this forum and when I try to get un update I receive the following error: Update process failed..
Reason: Can not create file '/opt/grisoft/avg7/var/run/avgupdate.pid'.

I installed as root.

Thanks for any help.

---

### Post by perkan on 2006-11-05
I've got the same problem!

Does anyone know what could be wrong?

Thanks

---

### Post by kerry_s on 2006-11-05
Are you updating with sudo(aka:root)?

---

### Post by perkan on 2006-11-06
Yes, I guess so, since I followed this guide:
[http://www.ubuntuforums.org/showthread.php?t=136064&highlight=avg]("http://www.ubuntuforums.org/showthread.php?t=136064&highlight=avg")

---

### Post by perkan on 2006-11-08
No one?

---

### Post by The Mekon on 2006-11-08
I have AVG installed but I had to run it as "sudo avggui" from a terminal.  This allows me to update.

I have now editted the AVG properties in the Applications Menu with the Command + "sudo avggui" and the Run in Terminal box ticked.

This opens the terminal, asks for my password then runs AVG

Brian

---

### Post by rlozano on 2006-11-08
automatic update of AVG requires root password. so if you want to update, you have to run it in the terminal and use sudo as advised by The Mekon.

or you can create a script to do that.

---

