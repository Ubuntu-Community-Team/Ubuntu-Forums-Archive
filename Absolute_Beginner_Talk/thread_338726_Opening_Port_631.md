---
title: "Opening Port 631"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-01-14
Is there a way to open port 631 vial the command line?

How is this accomplished?

---

### Post by jonny on 2007-01-14
System >> Administration >> Printing >> Global Settings >> Share Printers

---

### Post by jonny on 2007-01-14
Via the command line is tricky - you need to edit your CUPS configuration files.

---

### Post by chaplanger on 2007-01-14
> **jonny said:**
> System >> Administration >> Printing >> Global Settings >> Share Printers

I know this is the normal route, but the settings will not take in the GUI. Just today the ability to share printers has 'died' and I can find no way to reset this.

Any ideas on how to force an acceptance of "Share Printers" ?

---

### Post by marx2k on 2007-01-14
I'm not sure why it's this hard to find port opening information on ubuntuforums ...

I've found this so far..
[http://www.experts-exchange.com/Networking/Linux_Networking/Q_22065917.html](http://www.experts-exchange.com/Networking/Linux_Networking/Q_22065917.html)
It's for redhat but I think can be generalized to Ubuntu..

Here is the IPChains Howto-
[http://linux.web.cern.ch/linux/documentation/mirror/howto/IPCHAINS-HOWTO.html](http://linux.web.cern.ch/linux/documentation/mirror/howto/IPCHAINS-HOWTO.html)

You can also install FireStarter and use it to open a port... but seriously, there is a severe lack of documentation for how to open a port manually by hand.  (Unless I'm not providing the correct search term to here and google)

---

### Post by chaplanger on 2007-01-15
> **marx2k said:**
> 
You can also install FireStarter and use it to open a port...  (Unless I'm not providing the correct search term to here and google)

I did look to installing FireStarter -- had it up and running. (Wasn't too certain on the settings, so just stayed with the defaults. but my WIN 2000 box on the network seemed to still be able to come through my Linux machine). When I went to add the 631 as an open port it went from htt; to ipp.  After concluding this step -- still no joy -- the printer was not recognized through my WIN 2000 box.

Is there a good FireStarter tutorial out there to help set-up shared printing?

---

### Post by uboat on 2007-01-15
Two Questions,

1. What manufacturer is your printer?
2. Is your printer a network  printer? If yes then you can do the following under system >> Administration >> printing  click add new printer Icon and  once the new printer wizars poop up select apple or HP Jetdirect from the  drop down menu next to Network printer and hit next. When you see the scren pop up then where it says url://       you put in the ip of the  printer and following the ip address 192.168.0.225 you'd put :p9300 which tells the computer to connect to the device over port 9300.

---

### Post by chaplanger on 2007-01-15
> **uboat said:**
> Two Questions,

1. What manufacturer is your printer?

I have a Brother HL-5140. 

> **uboat said:**
> 2. Is your printer a network  printer? If yes then you can do the following under system >> Administration >> printing  click add new printer Icon and  once the new printer wizars poop up select apple or HP Jetdirect from the  drop down menu next to Network printer and hit next. When you see the scren pop up then where it says url://       you put in the ip of the  printer and following the ip address 192.168.0.225 you'd put :p9300 which tells the computer to connect to the device over port 9300.

This printer is not a network printer.

I did have this printer being shared (several days with no problems) but suddenly this connection died yesterday.  Apparently I cannot now open port 631 (I'm surmising this as our WIN computers can no longer "see" the printer).  The GUI will not change the selection back to "Share Printers" in System>Administration>Printing>Global Settings.

I am running Ubuntu 6.10.

---

