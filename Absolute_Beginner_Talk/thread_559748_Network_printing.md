---
title: "Network printing"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by stubish on 2007-09-25
Hi,
   Not sure how to proceed on this. See screenshot below:

[IMG]http://i118.photobucket.com/albums/o91/stubish/Screenshot-Aficio-700-CUPS12.8MozillaFirefox.png[/IMG]

The XP computers that can print fine on the network all use a raw socket to the IP address with a port number of 10001. They can all print fine.

Everything looks like it's working, however nothing will print, it takes a LONG time to spool, which then causes the printer to time out; printing nothing or whatever was managed to make it to the printer (usually less than 1/2 a page).

How can I fix this please?

Regards
Stuart Bishop

---

### Post by stubish on 2007-09-25
now the stasus reports:

"Network host '192.168.1.180' is busy; will retry in 15 seconds..."

---

### Post by dbott67 on 2007-09-25
Have a read of this post to verify that everything is set-up and configured properly:

[http://ubuntuforums.org/showthread.php?p=2413840&highlight=cups#post2413840](http://ubuntuforums.org/showthread.php?p=2413840&highlight=cups#post2413840)

-Dave

---

### Post by stubish on 2007-09-25
Hi,
   thanks for the quick response. I'm trying to connect to a ricoh Aficio 700 which is on 192.168.1.180 and has it's own print server (the printer that is).

I can ping the printer fine.

The thread you sent appears to be for sharing a printer connected locally to a linux box via cups?

---

### Post by dbott67 on 2007-09-25
My printer also uses a print server (HP Jet Direct).  In order to use CUPS, you have to go through the motions of setting up the printer, but instead of selecting "Local or Detected Printer", select "Network Printer".

The drop-down menu has choices for IPP, SMB, LPD and TCP/HP Jet Direct/RAW.  In my case, I selected the TCP/HP/RAW option and then I entered the IP of my Jet Direct server and the default port of 9100.  I am not familiar with the Ricoh, but if the others are printing using port 10001, then change the port number from 9100 to 10001.

Next, be sure to select 'Detect LAN Printers' and also to edit the ports.conf file as noted in my post above.

Keep us posted.

-Dave

---

### Post by stubish on 2007-09-25
Hi Dave,
            Ok, here's where I'm at. Here's the contents of the /etc/cups folder.

**********************************
stuart@Darkone:/etc/cups$ ls -a
.   cupsd.conf  mime.convs  ppd            printers.conf.O  raw.types
..  interfaces  mime.types  printers.conf  raw.convs        ssl
stuart@Darkone:/etc/cups$ 
**********************************

there's no ports.conf file that i could see?

---

