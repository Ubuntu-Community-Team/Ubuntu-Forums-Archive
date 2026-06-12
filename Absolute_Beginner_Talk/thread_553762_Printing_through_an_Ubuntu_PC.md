---
title: "Printing through an Ubuntu PC"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by kavon89 on 2007-09-18
I have a Vista laptop and an Ubuntu 7.04 PC connected to a rather old printer. How do I share this printer with my laptop? I forgot how it was, but do I need to add the laptop to the name of the network/workgroup, like MSHOME, then do somthing with Samba??

Thanks

BTW: If you're looking at my sig, it isn't the server I want to print through ;).

---

### Post by mikeyphi on 2007-09-18
I think it will be along the lines of:
on your ubuntu system - install Samba; open System/Administration/Printing select global settings/share printers
then set up your laptop to network with your pc - you should then get access to the printer

---

### Post by justleen on 2007-09-18
in the printer properties make sure it is shared..

On windows:  simply choose add printer, leave the fields  it asks for blank, klik next and it will give you a lsit of all network printers...

---

### Post by kavon89 on 2007-09-18
They don't seem to get along. My laptop can ping the Ubuntu desktop, but the Ubuntu desktop can't ping my router (in access point mode, connected to switch) or the laptop.

Setup:

Desktop - **Switch** - Wireless Router ) ) ) Laptop

(Switch has the modem and a server connected to it also, apparently this forum doesn't like a lil ascii art ;) )


I have a D-Link Rangebooster G, I also tried connecting to the router's config page from the desktop, it seems to be rejecting Ubuntu. :(

---

### Post by kavon89 on 2007-09-18
Update: I managed to get them to see each other now, problem is that when I try and connect to the Ubuntu computer, I'm hit with a username and password required. The Ubuntu computer's regular username and password do not work. What should I do?

---

