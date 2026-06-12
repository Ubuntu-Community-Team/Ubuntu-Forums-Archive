---
title: "[SOLVED] Can't get Epson Stylus C45 to print."
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by argie on 2006-07-21
I can't get my Epson Stylus C45 to print. *Nothing* happens. No movement no nothing.

It's listed in the Printers list as a Stylus C44UX. And everytime I try printing anything nothing happens. In gedit, the Print dialog shows the Printer as Paused. If I close everything restart the computer (with the printer disconnected) it shows the status as "Printing", though the printer is quite obviously doing nothing. Switching on the printer and connecting it at this point does nothing either.

Also, I don't have a "System > Administration > Printing", seems to have dissappeared in the upgrade to Dapper. What's the name of that tool, can I execute it from command-line?

---

### Post by slimdog360 on 2006-07-21
check out the recommended driver
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C45](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_C45)

---

### Post by argie on 2006-07-21
Thanks a lot, that helped much. I installed gutenprint and I can access the CUPS thing at:
[http://localhost:631/admin](http://localhost:631/admin)
And there's my printer there on the "Add Printer" list.
But here's the problem:
When I try to add the printer I have to enter a username and password, neither "root" and "<rootpassword>" nor any of the other usernames on the computer and their corresponding passwords works.That authentication screen just keeps popping up.

Thanks again, something tells me I'm doing something really simple wrong.

EDIT: If I persist it finally takes me to a blank page. Completely Blank.

EDIT Again: Nevermind nevermind, now the default page shows me that it's disabled. I'll follow the instructions there. Thanks for the help.

---

### Post by Kilz on 2006-07-21
> **argie said:**
> Thanks a lot, that helped much. I installed gutenprint and I can access the CUPS thing at:
[http://localhost:631/admin](http://localhost:631/admin)
And there's my printer there on the "Add Printer" list.
But here's the problem:
When I try to add the printer I have to enter a username and password, neither "root" and "<rootpassword>" nor any of the other usernames on the computer and their corresponding passwords works.That authentication screen just keeps popping up.

Thanks again, something tells me I'm doing something really simple wrong.

EDIT: If I persist it finally takes me to a blank page. Completely Blank.

EDIT Again: Nevermind nevermind, now the default page shows me that it's disabled. I'll follow the instructions there. Thanks for the help.

try sudo  and password

---

### Post by argie on 2006-07-21
Didn't work. I should've checked the "Home" tab. It said, 
> Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (System > Administration > Printing). /usr/share/doc/cupsys/README.Debian.gz describes the details and how to reenable it again.
Unfortunately, my upgrade from Breezy to Dapper made that "System > Administration > printing" dissappear, so when I found out that it was called gnome-cups-manager I did a "sudo apt-get install gnome-cups-manager" and then set it up through that, which was really simple. 

Thanks slimdog360 and Kilz.

Solution: (for anyone else who chances upon this thread, this is what worked for me)
1. ```
sudo apt-get install gutenprint*
```
2. ```
sudo apt-get install gnome-cups-manager
```
3. ```
gksudo gnome-cups-manager
```
4. Add Printer > Add the Epson Stylus C45.

I just hate it when it all seems so obvious later.

---

### Post by newbie8 on 2006-10-02
I've spent a long time figuring out how to make my Epson C45 work but it seems hopeless.

It does seem that the other website that stated that  Epson Stylus c45 works perfectly made a mistake.

Is there anyone who actually has a C45 that works with Ubuntu?

Please give us the complete idiot's way of getting a driver and making our printer work.

Thanks!

---

### Post by rbp on 2006-12-14
For me the default Epson-Stylus_C45.gutenprint driver wouldn't load because apparently I didn't have permission or it didn't exist but one of the other recommened ones did, the EPSON Stylus C45 - CUPS+Gutenprint v5.0.0-rc2. It prints very slow, but then it is a cheap printer.

---

