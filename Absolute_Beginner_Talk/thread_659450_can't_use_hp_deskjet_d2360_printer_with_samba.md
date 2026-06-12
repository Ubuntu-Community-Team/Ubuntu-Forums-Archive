---
title: "can't use hp deskjet d2360 printer with samba"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by emredmrl on 2008-01-05
Hi.
I have a hp deskjet d2360 printer which is installed on a windows pc.and i share this printer for my network to access with my laptop. the printer sharing works perfect with windows xp.
but in my laptop with ubuntu,even though i can see the printer,i cannot print any file.
when i try to print a test page,ubuntu successfully adds the file to the queue,then nothing happens.
printing does not start.

i will be grateful for anykind of help.
:)

---

### Post by sdellava on 2008-05-07
Hi, I've the same problem.

Some more details:
- Spools works correctly in both Ubuntu and Windows.
- After printing, in the Windows spool the job remains in the queue in PRINTING state.
- after some noise and ping that normally precede the printing phase, the printer hang.  
- To resume the printer, I've to reset it.

I can't verify with other printers if the problem is independent from the printer type, but I've verified that from other Windows PC the Windows shared printer works.

So I suppose that the job sent from the CUPS contains some data that cause the printer hang.

This is what CUPS report:

Description: DeskJet_D2300
Location: my-laptop
Printer Driver: HP DeskJet D2300 Foomatic/hpijs, hpijs 2.8.2
Printer State: idle, accepting jobs, not published.
Device URI: smb://WORKGROUP/MY-SERVER/HPD2300 

Thanks in advance for your support.

---

### Post by emredmrl on 2008-05-19
sdellava  explained better than me.
but still the printer does not work.
any solutions?

---

### Post by malangaman on 2008-05-19
This forum is ARCHIVE and not really active. Why don't you post your problem here:
[http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php)
Many more will see, and respond.

---

