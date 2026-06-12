---
title: "SAMBA/CUPS--&gt;Windows, printer status?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Gorsat on 2007-05-04
We have several computers at home.  Many are running various flavors of Windows, one is running OS X and another, the newest addition, is running Feisty Fawn.  

I've been running a Windows Server box for domain mgmt, file/print serving, SMTP/POP, backup, etc.  I'm trying to configure my ubuntu box to take over all of these tasks.  For the most part, this is going just fine.  I've got SAMBA set up for file serving the way I like, I've written scripts for backups and for quickly configuring a new install, etc.  However, I'm stumped by one basic problem.

I'm using SAMBA/CUPS/TurboPrint to share my LaserJet and Canon inkjet printers for use from all of the other computers in the house.  I've got this configured well enough that I can print just fine, check the queues from the Windows UI, etc.  But the problem is that I can't figure out how to get status messages to flow back from the printers to the Windows clients.  For instance, if the LaserJet runs out of paper or the Canon needs more magenta ink then the end-user (aka my wife) should get a notification on the Windows desktop.  This isn't happening with my current setup.  In fact, given the way the system seems to work (writing the jobs to disk and then spewing them in raw form to the printer) I can't figure out how it would ever work.  I'm hoping there's a way to do this, though, because if I can't make it work then I'll have to keep using a Windows box as my print server.  

Can anyone shed any light on this?  Is there any magic configuration I can tweak in CUPS and/or SAMBA to enable two-way status communication to flow between the Windows clients and the printers attached to my ubuntu box?

Thanks in advance!

---

### Post by Gorsat on 2007-05-04
*ping*


btw, is there a better place to post this?

---

### Post by Gorsat on 2007-05-05
Anyone?  

I'm not looking for someone to solve an issue with my particular setup.  I'm just looking for someone to say whether or not unsolicited printer status messages are supported in linux/cups/samba.  This is supported in Windows via a component called the "language monitor" but I can't figure out how it might be supported in ubuntu. 

When I run in the 7.04 desktop and send a job to a printer that has no paper I don't get any kind of notification -- not even a print failure.  The job just goes to the queue and sits there.  I can't imagine that this is the way it's supposed to work, but I'd like some expert to verify.  

Thanks.

---

