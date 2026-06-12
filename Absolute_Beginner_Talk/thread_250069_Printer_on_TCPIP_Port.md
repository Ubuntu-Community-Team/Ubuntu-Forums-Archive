---
title: "Printer on TCP/IP Port?"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by ArneB on 2006-09-03
(Absolute Beginner)

Is it possible to install a printer on a TCP/IP port locally, as in Window's? If yes, how and where?

Thanks y'all for helping develop this excellent alternative.

Arne

---

### Post by benfindlay on 2006-09-03
I take it you mean to install a printer onto your pc that is connected to another pc? Or do you mean to plug a true ip network printer into your ethernet port and print to it?

If you want to connect to a printer, say on your windows pc via your home network then just use the normal config tool and specify the ip address/network name of the computer it is connected to. As for your precise printer model, a quick google search using the words > ubuntu linux [printer model] drivers will tell you the best "generic" driver to use to get your printer working. I personally have a conon i560, running on a canon BJC-7000 driver.

If you're wanting to install a true ethernet printer then it should just simply be a case of using the same printer config and just specifying the ip address of the printer itself on your network!

Hope this helps!

---

### Post by benfindlay on 2006-09-03
PS forgot to mention printer config is ocated in:

System>> Administration>> Printing

Hope this helps!

---

### Post by Tibor60 on 2006-12-27
I was happy to see this topic but it is not the solution for me:(
I have a CONNECT2AIR WLAN AP-600RP-USB wifi adapter. I t works fine with XP, but I can not make it print from Ubuntu (no Dapper, no Efty) For the printer the adapter have an USB connection, any USB printer can be connected.

In the XP install wizard the steps:
1. Local or Network printer: Choose the local printer option
2. Select a Printer port: Create a new port, choose Standard TCP/IP Port
3. Add port:
                        Printer name or IP address:  192.168.1.254
                        Port name:                                IP_192.168.1.254
4. Configure Standard TCP/IP Port Monitor
                         Port name: IP_192.168.1.254
                         Printer name or IP address: 192.168.1.254
                         Protocol: LPR
The completing wizard confirms:
SNMP:  NO
Protocol: LPR, WLAN Printing
Device: 192.168.1.254
Port name: IP_192.168.1.254

Finish, and all works fine.

I tried any possible options in Ubuntu, no success:((((
But of course I fired out on "create a new port..." no such option in linux.

Mayber somebody can help?

---

### Post by halitech on 2006-12-27
you didn't get this from me but check this website out for adding a network printer on TCP/IP

[Ubuntu printer]("http://xerox.dynu.com/ubuntu_printer/")

---

### Post by Tibor60 on 2006-12-28
It is clear for me how to add a network printer. It is not a network printer, the CONNECT2AIR WLAN AP-600RP-USB adapter simply have an USD port to connect there any USB printer.

---

### Post by doncristobal on 2007-07-07
I have a very similar problem with my siemens gigaset sx541 wlan dsl router. 

my windows-only instruction goes very much like tibor60's, and it's also a wlan router with an usb port for the printer. 
the configuration tool of the router tells me about the printer: a) ip address is 192.168.2.1, and b) device is "USB-Drucker" (german for usb printer). 

that's all i know, and i'm helpless. Any hints are huuuugely appreciated!

---

### Post by doncristobal on 2007-07-08
i have just solved my problem with the siemens and the hp! 
:mrgreen:

Have a look here: [http://ubuntuforums.org/showthread.php?t=369972](http://ubuntuforums.org/showthread.php?t=369972)

I hope this helps other people, too.

---

