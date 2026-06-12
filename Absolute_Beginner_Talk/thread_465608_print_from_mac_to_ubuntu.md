---
title: "print from mac to ubuntu"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Digitallysick on 2007-06-05
I need a little help, i had this setup once upon a time, but now im having trouble. 

When i go to my mac printers, i can see the printer on the network, when i select it, and try to print it says "NT USER ACCESS DENIED"  i have cups setup [http://192.168.1.2:631](http://192.168.1.2:631) when i click around on the tabs from my ubuntu pc, i get 403 forbidden, i just need to print from the mac to ubuntu

---

### Post by dstew on 2007-06-06
Please clarify for us what you are trying to do. The printers you call "mac printers", are they truly Mac shared printers, or network printers? That is, are the printers plugged into the Macs, or do they have their very own network connections? Also, what Mac OS version do you have? You have an Ubuntu PC, but what is your Ubuntu version? For the CUPS administation tool, on your Ubuntu PC, try [http://localhost:631/admin](http://localhost:631/admin). You can also use the System --> Administration --> Printers dialog window to do the same CUPS setup as the web-page tool. However, the problem might lie with the setup of the Mac shared printers, and not with Linux.

---

### Post by Dedoimedo on 2007-06-06
Hello,

You will need to edit your cupsd.conf and permit the relevant IP.

cp /etc/cups/cupds.conf /etc/cups/cupsd.conf.bak
gedit /etc/cups/cupsd.conf

In the file, search for this entry:
#Listen 127.0.0.1:631 OR localhost:631

Beneath, add or change as follows:
xxx.xxx.xxx.xxx:631 OR *:631
Listen /var/run/cups/cups.sock

Substitute xxx.xxx.xxx.xxx with relevant IP address (if static) or wildcard (if dynamic).

Restart cups

sudo /etc/init.d/cupsys restart

Try to connect and print now.

Dedoimedo

P.S. Do you use firewall in Ubuntu?

---

