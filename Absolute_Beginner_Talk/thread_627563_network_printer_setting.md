---
title: "network printer setting"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by hums07 on 2007-11-30
In my office, there are two network printers. In XP they are set up as standard TCP/IP printer. I just put an IP address and port number, and choose printer model and it will work.
How do I set this in Gutsy? I have not found an answer in this link: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

Thanks.

---

### Post by shanepardue on 2007-11-30
In the printing section, click goto server and type the ip address of the server sharing it. 
You'll probably have to check the box saying "show printers shared by other systems.

---

### Post by hums07 on 2007-12-20
I was trying to look over the options today when suddenly I noticed in Printer Configuration on Policies tab that the "Enabled" option is not checked. I checked it, printed a test page and it works.

So this is how to set up:
1. In the Printer Configuration, click New Printer
2. Select AppSocket/HP JetDirect
3. Put the printer IP address in the Hostname box, and port number as set up by the network admin (9101 in my case), then click Forward button.
4. Select printer manufacturer, then select printer model and driver (I just select recommended driver), then click Forward button.
5. GIve a name for the printer and any description, then click Apply button.
Check the Policies tab and see if Enabled option is checked.

---

