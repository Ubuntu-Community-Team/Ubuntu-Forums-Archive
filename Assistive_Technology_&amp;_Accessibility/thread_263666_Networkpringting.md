---
title: "Networkpringting?"
date: 2006-09-23
forum: Assistive Technology &amp; Accessibility
---

### Post by dema on 2006-09-23
I've a ZyXEL 335WT router with Print Server. My HP PSC 1510 works great with this Print Server when using Windows.

In windows the data are discript like this:
Port: LPT:PS670C-1
Discription: 192.168.1.1,PID:1
Printer: HP PSC 1500 series

How can I get this work in ubuntu?

---

### Post by dejan32 on 2006-09-23
hi you can do this by going to system, administration, printing then click the New Printer Button. click the network printer chose windowes(if thats the case). it will ask you to put in your password. click forword and chose the manufacture of the printer(in your case its hp)chose the HP PSC 1510 modal number andclick forward you dont have to do any thing else just click apply 

I hope this works good luck

---

### Post by dema on 2006-09-24
Well, I've been there.

When a new printer is added, I've to choose between this types of network printing:
CUPS-printing (IPP)
Windows-printer (SMB)
Unix-printer (LPD)
HP JetDirect

I choose LPD, and this it ask me for address and queue. I think the adress is 192.168.1.1 but what about the queue?

---

