---
title: "Printing Problems to USB Print Server"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by landsg on 2006-04-15
Hi All:

I just bought a USB printer server (Netgear) because I was sick of trying to print to my desktop machine (XP).  I am running an IBM Thinkpad T23, and want to be able to print directly to the printer via an IP address.

My XP machine can see printer connected to the print server and print jobs to it, but so far my Ubuntu box cannot.

I travel quite a bit, so I am hoping to be able to print to the home network printer while I am on the road.  Any ideas??

---

### Post by marcos89 on 2006-04-15
I used kcontrol and kdenetwork-filesharing and found a samba module under INTERNET in kcontrol, and added a share printer and with SYSTEM> ADMINISTRATION>PRINTERS added one with a guest account and SUCCESS ;)

---

### Post by landsg on 2006-04-16
Marcos:

Many thanks for the reply.  I am not running the KDE desktop.  Can I use the control module under Gnome to do the same thing?

---

### Post by uteck on 2006-04-16
[QUOTE=landsg]Marcos:

Many thanks for the reply.  I am not running the KDE desktop.  Can I use the control module under Gnome to do the same thing?[/QUOTE]
You should be able to find the print server using System->Administration->Printing.  Then click on New Printer.  I have a Linksys USB printserver, and it uses Cups and Samba, so you could try searching for either type.  

But for some reason my Linksys Printserver gets the driver messed up and everything prints multiple times in various shades of color.

---

