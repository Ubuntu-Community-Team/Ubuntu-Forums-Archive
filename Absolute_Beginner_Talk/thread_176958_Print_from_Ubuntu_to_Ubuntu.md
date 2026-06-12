---
title: "Print from Ubuntu to Ubuntu"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by GaFFy on 2006-05-15
Still trying to figure out how to print to another Ubuntu computer.
My printer is set up and prints locally fine but when I print from my laptop to my server it just gives this error:

I [15/May/2006:14:11:16 -0400] Generating server key...
E [15/May/2006:14:11:16 -0400] Unable to create server key file "/etc/cups/ssl/server.key" - No such file or directory
E [15/May/2006:14:11:16 -0400] encrypt_client: Unable to encrypt connection from 192.168.1.104!
E [15/May/2006:14:11:16 -0400] encrypt_client: A record packet with illegal version was received.

Can I just disable encryption somehow? ](*,)

---

### Post by GaFFy on 2006-05-15
could it be that they are different cups versions? ](*,)

---

### Post by richbarna on 2006-05-15
[QUOTE=GaFFy]
My printer is set up and prints locally fine but when I print from my laptop to my server it just gives this error:

I [15/May/2006:14:11:16 -0400] Generating server key...
E [15/May/2006:14:11:16 -0400] Unable to create server key file "/etc/cups/ssl/server.key" - No such file or directory
E [15/May/2006:14:11:16 -0400] encrypt_client: Unable to encrypt connection from 192.168.1.104!
E [15/May/2006:14:11:16 -0400] encrypt_client: A record packet with illegal version was received.
 ](*,)[/QUOTE]
Take a look at this :-
[http://docs.kde.org/stable/en/kdebase/kdeprint/server-encryption-support-configuration.html]("http://docs.kde.org/stable/en/kdebase/kdeprint/server-encryption-support-configuration.html")

---

### Post by GaFFy on 2006-05-15
how do i get to that window?, i am using gnome :-/

---

### Post by richbarna on 2006-05-15
Ahhhh, ok, that window is from the kde desktop ;) silly me.
Ok for gnome, try Alt+F2 (run dialogue)
> gnome-cups-manager

---

### Post by richbarna on 2006-05-15
If you are running the cups server, you should be able to configure it by opening your localhost printer port. Try this :-
[http://localhost:631]("http://localhost:631")

---

### Post by GaFFy on 2006-05-15
[QUOTE=richbarna]If you are running the cups server, you should be able to configure it by opening your localhost printer port. Try this :-
[http://localhost:631]("http://localhost:631")[/QUOTE]

I have been using localhost:631 but it doesnt have options for encryption.
And gnome-cups-manager doesnt either. ](*,)

---

### Post by richbarna on 2006-05-15
okay, last but not least, edit the config file :-
> sudo gedit /etc/cups/cupsd.conf
Scroll down the list and at the bottom it says "authtype" I think if you change that to "none" as well as commenting out the lines related to encryption further up, that might just work.

---

### Post by GaFFy on 2006-05-16
[QUOTE=richbarna]okay, last but not least, edit the config file :-

Scroll down the list and at the bottom it says "authtype" I think if you change that to "none" as well as commenting out the lines related to encryption further up, that might just work.[/QUOTE]

i have Authtype None and Encryption Never set but still get that error ](*,)

---

### Post by richbarna on 2006-05-16
Ok, lets give this a shot :-

> /etc/hosts.lpd
 Which machines are allowed to print to the printer connected to this (printer) server.
> Printer Sharing with LPRng and the /etc/hosts.lpd File
For pure Linux or Linux/UNIX environments, printer sharing can be controlled using the /etc/hosts.lpd file. This file is not created by default; as root, create the file /etc/hosts.lpd on the machine to which the printer is attached. On separate lines in the file, add the IP address or hostname of each machine which should have printing privileges:
falcon.example.com
pinky.example.com
samiam.example.com
pigdog.example.com
yeti.example.com
  To have LPRng use /etc/hosts.lpd for access control, you must add the following line to /etc/lpd.perms:
ACCEPT SERVICE=X REMOTEHOST=</etc/hosts.lpd

This came from :-
[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/admin-primer/s1-printers-sharing.html]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/admin-primer/s1-printers-sharing.html")

Even though it's a RedHat guide, I think it applies to all print servers using CUPS on anetwork.

Let me know how you get on.

---

### Post by GaFFy on 2006-05-16
Whoa it worked!  You are awesome. :D 
I did both things from that page you linked and then restarted cupsys
Now that this is fixed I can let my hair grow back, I was so frustrated I pulled it all out!

You saved me from a long argument with my windows loving girlfriend that wants her laptop back :twisted:

---

### Post by richbarna on 2006-05-16
Awesome no, just trying to help.
It worked, excellent.
Have fun printing :)

---

