---
title: "printing to from a WinXP client"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by gian on 2006-08-15
Hi All,

I have a *local* usb printer setup on my Ubuntu Dapper box.

In order to print from a WinXP client, I tried the following advice:
**************************
Windows Client Machine
      Add the printer to the Windows client by using the Windows "Add Printer" Wizard. Type in the following in the printer URL:
          [http://PRINTSERVERNAME:631/printers/PRINTERNAME](http://PRINTSERVERNAME:631/printers/PRINTERNAME)
    *
      PRINTSERVERNAME is the name or ip address of the print server,
    *
      PRINTERNAME is the name given to the printer on the print server.
**************************

but it did not work...

Questions:
what am I doing wrong?
where can I find PRINTSERVERNAME ? Is it the host name ? Anyway, it doesn't work even using the IP address of the Ubuntu box.

thanks for your time...
-Gian

---

### Post by indytim on 2006-08-15
I followed this guide when I set up a Laser Printer connected to my Ubuntu Gnome Box.  It serves as a server to another XP box,


[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

IndyTim

---

### Post by gian on 2006-08-16
Gindytim,

thanks for your kind reply, I had already seen that doc.

Unfortunately, while everything is fine on the Dapper box, I cannot seem to find the printer from my XP laptop...

Tried the following:

[http://192.168.1.3:631/printers/Deskjet-895C](http://192.168.1.3:631/printers/Deskjet-895C)
error "Unable to connect, Firefox can't establish a connection to the server at 192.168.1.3:631"

[http://servername:631/printers/Deskjet-895C](http://servername:631/printers/Deskjet-895C)
goes to a webpage looking for "servername"

On the Ubuntu box, the printer status says "published".
Somehow, the Win laptop cannot locate Ubuntu.
I haven't installed Samba, 'cause I thought you didn't need it just for network printing, is that true ?

-Gian

---

