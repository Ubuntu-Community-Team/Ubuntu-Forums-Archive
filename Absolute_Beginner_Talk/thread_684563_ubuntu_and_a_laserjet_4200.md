---
title: "ubuntu and a laserjet 4200"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by sleeve_less on 2008-02-01
Hello, all
I have a ubuntu cd running in order to print something from linux, and I can't connect to the laserjet 4200 here at work. 
Details:
I'm using ubuntu 4.10 --running from the CD..not an installation. So, of course, I can't install any drivers in this situation. 
It's on  a lan at work (on a domain), the pc is a dell gx240...with 512m ram. 
I Can look on the network from this pc and see the print server, but I can't drill down any lower in that to "see " the printers. 
 I did go to the sys config and choose printers/new printers...and chose network printer, and cups ...
In the url I input [http://hostname:631/ipp/](http://hostname:631/ipp/)   ---> I input the ip address of the printer, where the hostname is above. Then hp/laserjet 4200...then I clicked apply. It won't print. 
I can ping the printer, input the ip address and it connects to the printer fine. 
I see the printer is ready (in the printer properties), and that seems like it "sees" the network printer. 
NOTE-- someone told me I need to enable cups network printer auto-discovery...by doing the following:
sudo ln -s ../backend-available/snmp /usr/lib/cups/backend/snmp
I put that command in a root window. It doesn't come up with any errors, so I guess it "took" the setting. Did I do that right? I mean I did it all on one line,and in a root window. Is that correct? 
Thanks in advance. 

sleeve less

---

### Post by stump138 on 2008-02-01
Try to use TCP/IP the raw port of 9100, as HP IPP can be flaky at times.

---

