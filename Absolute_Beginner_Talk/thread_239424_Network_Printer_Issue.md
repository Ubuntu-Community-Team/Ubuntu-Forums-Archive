---
title: "Network Printer Issue"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Derspankster on 2006-08-19
I installed Ubuntu on an old drive in a box I put together for the purpose. Played with it, set up my HP 5P network printer (running on a Linksys print server) without issue. Swapped out the old drive for a newer, bigger drive, reinstalled Ubuntu 6.06.1 without issue but now I cannot print to the network printer. Entered fixed printer IP just as I did before but it will not print! Guess I'm stumped. I've read all posts referrring to network printers and tried a variety of drivers but cannot print.

---

### Post by Chuck_W on 2006-08-20
Not sure why it worked before but doesn't now. Maybe my experience will help. first of all, if you have created any printers usng System>Administration>Printers delete them. I never had any luck with changing the settings on an already created printer. It just worked better to start over. My Kyocera printer is on my network through a Hawking Technologies print server. It has a fixed IP address. I set it up as a network printer using UNIX Printing (LPD). The host is the IP address (192.168.xxx.xxx)) The queue is lp1. You shouldn't have any problems with drivers. Ubuntu seems to have a ton built in. Even my printer was listed.
Good luck.

---

### Post by Derspankster on 2006-08-20
Thanks for the reply. I have tried what you described but tried again. Still not working. I get this message- Printing: Network host '192.168.1.XXX' is busy; will retry in 30 seconds...

---

### Post by wpshooter on 2006-08-20
> **Derspankster said:**
> Thanks for the reply. I have tried what you described but tried again. Still not working. I get this message- Printing: Network host '192.168.1.XXX' is busy; will retry in 30 seconds...

Just to let you know, that is exactly the same message I get when **trying** (using CUPS) to setup my HP Laserjet 2100 printer so that I might be able to print from one of my other Ubuntu Dapper Drake workstations to the Ubuntu workstation on which the printer is hooked up to LPT1.  

I have just about given up on getting this to work.  I think this problem (at least in my case) has something to do with the way my Verizon modem/router is assigning IP addresses to my 4 different computers.  I have almost come to the conclusion that this problem is somehow related to the DNS assigment of IP addresses and that if I used static IP addresses for each machine that might solved this problem but not knowing too much about networking I am dubious about trying this because I don't know what else this might mess up.

Good luck, let us know if you find a solution.

---

### Post by Derspankster on 2006-08-20
I have 4 computers (2 wired, 2 wireless) connected to my router and a Linksys printserver (wired). 3 of the computers run Windows XP and all can print to the HP 5P.  The IP of the printer is fixed outside of DHCP.  Like I said earlier, the first time around with the initial Ubuntu install, the printer configured and worked perfectly.  After installing another hard drive, I installed 6.06.1 and cannot print from the Linux box. The only difference was the first install was 6.06 and the 2nd 6.06.1.

---

### Post by Derspankster on 2006-08-21
Problem solved! Found this reply in another thread and this has solved my problem:

Hi
Here's a more or less general reply on the subject of using a hardware printserver. I have a Netgear FR114P router with firewall and print server. I'm running Ubuntu 6.06. Under 'printing' I checked 'detect LAN printers'then add new printer. In that dialog I selected Unix printers LPD and for host 192.168.0.1 --the Netgear default-- for queue I entered FR114P. Apparently cups needs the name of the router/printserver as the queue name. I selected my Epson printer in the next dialog, and then 'apply' When I clicked on print test page it printed the Ubuntu test page perfectly. This same setup worked on Mac OSX as well. Now I print from XP, two Ubuntu boxes and a Mac and it all works. Hope this is usefull.
Ken

The only difference for me was that I used my fixed IP address for the printer not the printserver default. Works perfectly!

---

