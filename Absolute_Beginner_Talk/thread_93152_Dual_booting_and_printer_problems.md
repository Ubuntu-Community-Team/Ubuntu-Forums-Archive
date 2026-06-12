---
title: "Dual booting and printer problems"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by tomfieldt on 2005-11-21
Hello everyone, just installed Ubuntu 5.10 and have some questions about dual booting with windows XP (wife still likes it, lol). Any easy suggestions on how to do it? Also I have an HP Deskjet 722C that isn't recognized. Do I have to go and get Linux drivers for this? Thanks for all your help!:D  Also, I know Mandrake/Mandriva uses urpmi, does Ubuntu have the same type of site for updates/installs?

---

### Post by Zunflappie on 2005-11-21
Hello.
Also I have problems with our printer.

At home we use a Edimax Printserver (PS 1001).
I have downloaded drivers.... but cant install it.
It is a simple .exe-program... but I cant run it.

Yes, i am new and I don't know how to use this Ubuntu.... so please explain.
The main problem is that I cant install/run applications.
If I know only that... I will be on my way.

Thanks in advance.

Zunflappie
(member for 3 minutes now)

---

### Post by Zunflappie on 2005-12-05
[QUOTE=Zunflappie]Hello.
Also I have problems with our printer.

At home we use a Edimax Printserver (PS 1001).
I have downloaded drivers.... but cant install it.
It is a simple .exe-program... but I cant run it.

Yes, i am new and I don't know how to use this Ubuntu.... so please explain.
The main problem is that I cant install/run applications.
If I know only that... I will be on my way.

Thanks in advance.

Zunflappie
(member for 3 minutes now)[/QUOTE]

Oke, now iam a week-old-member :cool: 
But still, i cant install this printer-server.

If I will use my printer (and thats the goal) i have to add a printer-port.
Using the installer/drivers it will work.

**Question 1:**
How do i, manually, add a printerport?
And give it a name etc...

**Question 2:**
How do i execute a .bin-file?
From [www.edimax.com](www.edimax.com) i downloaded the drivers (only windows???)
Its a .zip-file.
No problem > extracted.
Result: a .bin-file where i cant lay my hands upon it.


Thats all. If this works i'am realy close to complete :D

---

### Post by schdefan on 2005-12-05
tomfieldt: just run gnome-cups-manager and at the printer HP Deskjet 722C.
It is fully support with cups.
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_722C]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_722C")


Zunflappie: As I see your printserver is an independent hardware device the file you downloaded is a driver for this box. I think you can configure the print server with a browser by typing http://<ip_of_printserver> 
There has to be a page where to assign the printer port.
If you want to share the printer in a network you can do this with cups also.

schdefan

---

### Post by Zunflappie on 2005-12-05
I will try ;)

The printer in case is a HP LaserJet 4L.
Ps how can i find the ip of te printer?

Just guessing isnt smart ;)
Ps the device is already configured. Only Linux not ;)
So thats the problem.

In Windows XP (before Linux) the device worked from my pc... so the device is OK.
Linux not (yet).

**Edit**
Found the ip...
i think now it will make it.
(ps where can i find where my Edimax PS1001 is a IPP, a SMB or a LPD?

---

### Post by schdefan on 2005-12-05
install nmap with synaptic or
```
sudo apt-get install nmap
```

in a terminal do a 
```
nmap -sP 192.168.1.*
```

This will list you all host in your network that are online
On of those must be your printserver

schdefan

---

### Post by Zunflappie on 2005-12-05
thanks!

It works!
Thanks to your help, now i can print!
Superb!!!!!!!!

Thanks a lot:cool:

---

### Post by schdefan on 2005-12-05
Great that it is working for you now. Can you explain what steps you have done to get it working so other people with similar problems can benefit from your new knowledge.

schdefan

---

