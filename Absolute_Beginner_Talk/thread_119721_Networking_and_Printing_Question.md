---
title: "Networking and Printing Question"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by utab on 2006-01-20
Dear all,

I am using my pc on a network at work and use printer facilities on that network. I use a dual boot system (WIN XP  & Ubuntu). The question is that on Win side to login on the network I use a user name and password and use printers without problems(of course after installing them). When I log on to Ubuntu OS I use a different user name but the same password. I think this is a problem for networking but I can connect to internet(over LAN) from the first moment I installed Ubuntu.

When I try to add a printer from the printing menu, I can see the computers on the network as well as the computer which is connected to an HP Laserjet 4000N.  But when I choose the computer number that is the one the printer is connected, I can not see any printers installed on the list.

1.) How can I check my networking options for the LAN I am connected to?
2.) Can this user name issue be causing problems for my computer to get connected to LAN?

How can I overcome these problems?

Thanks in advance

---

### Post by darth_vector on 2006-01-20
try the following:

1) go to gnome_menu->system->administration->printing
2) select add a new printer
3) choose network printer->hp directjet
4) put in the IP of the printer

and you should be ready to print

---

### Post by utab on 2006-01-20
Thanks first 

there are two boxes 

Host and Port 

Port is automatically filled out with 9100.

Do I have to fill out the IP into the Host Box?

Regards

---

### Post by darth_vector on 2006-01-20
[QUOTE=utab]Do I have to fill out the IP into the Host Box?[/QUOTE]

yes. and use the default port (ie 9100)

---

### Post by Sef on 2006-01-20
> Do I have to fill out the IP into the Host Box?

Yes, that tells the computer where the printer is.

---

### Post by utab on 2006-01-20
Thank you all first

I checked the IP address of the computer on which the printer is on. And filled out the host field with this information(IP number). The printer then comes in the add printer window however when you try to print a document, let's say .pdf, it seems printing but no outcome.

Still can't print using Ubuntu

Regards

---

### Post by tim15856 on 2006-01-20
If the printer is connected to a Windows computer, then you need to print using a smb port. [http://www.willmer.com/kb/2005/05/printing-to-windows-xp-printer-from-ubuntu/](http://www.willmer.com/kb/2005/05/printing-to-windows-xp-printer-from-ubuntu/)

---

