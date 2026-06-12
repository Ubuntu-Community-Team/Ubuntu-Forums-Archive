---
title: "SetUp Printer"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by zhangkoonwai on 2008-04-17
I have two computers with one windows xp and one ubuntu 7.10. My Printer is HP Photosmart 7450 and connected to the printer server of the broadband router. the windows xp can setup the printer via tcp/ip (192.168.1.1). But I can't setup my printer using ubuntu.
After adding new printer, which of the following options below should I chose? Why no network printer is available?
1. Printer into PDF file
2. LPT#1
3. Windows Printer via SAMBA
4. AppSocket/HP JetDiret
5. Internet Printing Protocol (ipp)
LPD?LPR Host or Printer
Other

Thanks a lot!

---

### Post by aeiah on 2008-04-17
try them all!

nah, i think from a quick google, you'll want 'AppSocket/HP JetDiret' and then perhaps you can choose your specific model, or enter an IP or something

---

### Post by master5o1 on 2008-04-17
Would it not be option 3?

Have you tried that yet? Is the port a serial port on the router or a does the printer itself have an Ethernet port?

Can you access the print server via your browser? Check out [http://localhost:631](http://localhost:631), it gives more options and you might even find it easier to use. Through the CUPS server you can also find this page [http://localhost:631/help/network.html?TOPIC=Getting+Started&QUERY=](http://localhost:631/help/network.html?TOPIC=Getting+Started&QUERY=) which is the internal documentation for configuring a Network printer.Searching for info on CUPS on google might help you if no one here can.

---

### Post by northern lights on 2008-04-17
The printer is connected to the XP machine, right?

On the XP machine, simply right-click on the printer, choose "Properties" and under the "Sharing" tab, share the printer.

On your Ubuntu machine install samba if you haven't already: ```
sudo apt-get install samba
```
Now navigate to "System > Administration > Printing" and select "New Printer". Choose "Windows Printer via SAMBA". Click "Browse". Make sure the XP machine is running. Select the XP comp, select the respective printer. Drivers will be added automatically. Done.

P.S. You have to restart any application you want to print with that has been running during the printer install...

---

### Post by zhangkoonwai on 2008-04-17
.aeiah, master5o1, northern lights,
Thanks ALL very much!!

---

