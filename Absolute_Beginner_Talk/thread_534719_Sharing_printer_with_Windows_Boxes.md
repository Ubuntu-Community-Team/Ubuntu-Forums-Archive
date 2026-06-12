---
title: "Sharing printer with Windows Boxes"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by pencil86 on 2007-08-25
I have Ubuntu installed and a printer installed as well. How do I make it so that Windows boxes can see this printer? Is there a printer sharing option in Ubuntu so windows boxes can see the printer?

---

### Post by oilchangeguy on 2007-08-25
have you enabled file and print sharing in windows?

---

### Post by pencil86 on 2007-08-25
No, the printer is connected to the box running Ubuntu. The windows boxes are the ones that need to see the printer over the network....

---

### Post by scrooge_74 on 2007-08-25
You need to run the samba server so you can share printers and folders with Windows machines

---

### Post by mspendlo on 2007-08-26
OK, just got this going myself on a fresh Feisty install and printer sharing works with XP and OS x.

I used this URL as a guide BUT, rather than editing the cupsd.conf by hand I just enabled the checkboxes for sharing in the web manager :

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

Cups should be running by default. If so, you can hit the config in your browser :

[http://localhost:631/admin](http://localhost:631/admin)

and check the sharing checkboxes.

OS x found the printer itself and I used the instructions at the bottom of the first url to add a network printer to XP.

HTH

---

### Post by mmtowns on 2007-10-13
I'm running Feisty and am trying to share my printer with my MacBook via the network.

I think I follow your how-to, but am confused at the following step...

--------
Below those lines add another "Listen" configuration corresponding to the IP address of the computer sharing out the printer. For example, if the IP address is 192.168.1.2, add this line.

Listen 192.168.1.2:631
----

I'm assuming this should be the IP of my Linux box?  If so...I'm running DHCP, so this IP address will change after reboots, etc.  Is there a workaround?

---

