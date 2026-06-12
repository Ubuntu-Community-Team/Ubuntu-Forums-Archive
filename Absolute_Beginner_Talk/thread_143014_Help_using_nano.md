---
title: "Help using nano"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by Klejs on 2006-03-11
Hi all,

Im about to change my motd for my breezy to make it look nicer. The thing is that i dont know how to implement commands in the text, like uptime and such. Is there an way to do it, or do I just have to accept that its not possible?

---

### Post by cwaldbieser on 2006-03-11
[QUOTE=Klejs]Hi all,

Im about to change my motd for my breezy to make it look nicer. The thing is that i dont know how to implement commands in the text, like uptime and such. Is there an way to do it, or do I just have to accept that its not possible?[/QUOTE]
What you could probably do is have a short cron script that periodically updates /etc/motd with the inforamation you want.

---

### Post by aysiu on 2006-03-11
It doesn't sound as if your question has anything to do with Nano. Is it just me?

---

### Post by Klejs on 2006-03-11
Ok, so nano itself doesnt have the support for it? How about other text-editors?

---

### Post by taurus on 2006-03-11
Nano, pico, vi/vim, gedit, emacs, kate, etc. are just text editors.  They will not do what you have in mind...

---

### Post by Klejs on 2006-03-11
Ok, but thanks for the help on making that cleared out...:-D :-D

---

### Post by 5-HT on 2006-03-11
[quote=Klejs]Hi all,
Im about to change my motd for my breezy to make it look nicer. The thing is that i dont know how to implement commands in the text, like uptime and such. Is there an way to do it, or do I just have to accept that its not possible? [/quote] 
 Hi, the MOTD is simply an ASCII text file.                                                                                                                                   
As such, any commands entered into /etc/motd will only be echoed back *as is *(irregardless of which editor you use).

So, how can you get the MOTD to be updated some of information you'd like?

The best way that I can think of was provided by cwaldbieser:

[quote=cwaldbieser]What you could probably do is have a short cron script that periodically updates /etc/motd with the information you want.[/quote] 
To do this, just generate a script that generates a MOTD with the information you want, and schedule it with cron.

Here's a nice tutorial on the wiki if you are not familiar with cron:
[https://wiki.ubuntu.com/CronHowto]("https://wiki.ubuntu.com/CronHowto")


Note that depending on reboot/shutdowns, the MOTD may not necessarily reflect immediately up to date information.

HTH

---

