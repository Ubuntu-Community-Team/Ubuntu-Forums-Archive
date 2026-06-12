---
title: "Shared Printer"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-19
Been reading through the forum, but I am still a little confused, sorry for posting something that has been asked quite often.

I have the following set up:

printer - pc (windows xp) - router (wireless) - my laptop

I would like to set up the printer in Dapper so I can use it.

What's the easiest way to set it up? System > Administration > Printing ?

And if yes, do I select 'Detect LAN Printers' ?

(If yes, I tried that but was confused by the data it reuested of me to use (cups or ipp?, password for workgroup, host, url...?)).

---

### Post by ReaderRat on 2006-11-19
I don't know, but I will bump you to see if someone will help (I have seen numerous posts about this).

You might go to "Tags" (at the top of the page), click on it and try different tags, like: LAN, Printer, etc. to see if you find something.

---

### Post by PartisanEntity on 2006-11-20
Thanks for the tip. And here is another pseudo bump :)

---

### Post by PartisanEntity on 2006-11-20
p.s. its a Canon i560.

So according to what I have been reading on the forum, I tried the following:

System > Administration > Printing > New Printer

then:

Clicked on Network Printer
Chose CIUPS Printer IPP
URL: I entered the network IP 192.168... of the pc to which the printer is connected.

Then chose the BJC7000 drivers since some here on the forum mentioned that these drivers worked with the Canon i560.

Once all this was done I tried printing, the printer icon appeared in the top panel but nothing happened on the actual printer.

Should I have chosen Windows Printer SMB instead? What's the difference?

---

### Post by tom56 on 2006-11-20
First of all enable sharing for the printer in Windows. There are plenty of guides out there to do this, and it's fairly easy to work out anyway. Then in Ubuntu...

1) Go to "System" -> "Administration" -> "Printing". Enable "Global Settings" -> "Detect LAN Printers".
2) Double click "New Printer".
3) Click "Network Printer", "Windows Printer".
4) Select the computer and printer, and - if applicable - user and password for the printer.
5) The rest is obvious, just use the defaults.

Let me know how it goes. Never done this myself so I'm guessing somewhat.

EDIT: IIRC you enable sharing for the printer in Windows by going to the Control Panel then Printers and right-clicking the printer -> Share this printer.

---

### Post by PartisanEntity on 2006-11-20
What username and password do I have to enter?

---

### Post by tom56 on 2006-11-20
Did Windows ask you to set a password for the printer when you enabled sharing? If so, enter that. If not try not entering nothing and see what happens. If that doesn't work try your Windows login.

---

