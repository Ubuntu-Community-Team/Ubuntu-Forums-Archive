---
title: "Is there a way to force hibernation"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by derred on 2007-05-18
I have scheduled my laptop to hibernate every night at 2 am.
 Hibernation is set up OK. 
I've scheduled it as root so there's no problem there. 
BUT sometimes it just doesn't want to go. 
I've noticed that some programs like azureus and kttsd usually cause it to fail. 

Is there a workaround?

---

### Post by FuturePast on 2007-05-18
Can you explain exactly the steps you've taken?
I sometimes set my machine to suspend at 4am, and I've had no problems
as long as I use the right commands.

---

### Post by derred on 2007-05-18
tnx FuturePast
i just run gnome-scheduler as su and create a recurent task /etc/acpi/hibernate.sh
sometimes it works but if i have azureus on it gives a HAL error and doesn't want to go

---

### Post by FuturePast on 2007-05-18
Can you do [FONT="Courier New"]$ sudo crontab -l[/FONT] at the terminal just to show what's going on?

---

### Post by derred on 2007-05-18
here it is
~$ sudo crontab -l
Password:
00 2 * * * /etc/acpi/hibernate.sh          >/dev/null 2>&1 # Untitled, 
00 4 * * * /etc/acpi/hibernate.sh >/dev/null 2>&1 # hibernate 2, 

I know there's one at 4 also but that's just a backup in case the first one doesn't do it

---

### Post by FuturePast on 2007-05-18
Well it all looks in order. The only thing I can suggest is to kill or suspend azureus before hibernating.

---

### Post by derred on 2007-05-18
Thanks. I'll post here if I get anywhere with a suspend of problem applications.
Cheers!

---

