---
title: "Cable Modem (Eth) taking an age resolving IP"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by shavenlunatic on 2007-06-12
Hi,

I have a cable modem linked directly to my PC via an ethernet cable.  If I boot into XP it picks up the IP instantly and I'm on the internet.  If i reboot and go into Ubuntu, it takes a fairly long while trying to obtain an IP address.

Now, I have overcame this by making a note of my IP in windows and manually configuring the IP in Ubuntu, problem solved and I have instant internet connection on a reboot.  The problem I will face is when my ISP decides to (and it does occasionally) change my IP.  It's hardly a nightmare but it's an issue I could do without.

Is there a quicker way to get this to obtain the IP or do I just have to either wait of manually configure it?

Incidentally, when I had the cable modem connected using USB it worked fine, but that is no longer possible (unless I get a REALLY long usb cable, and it's hardly ideal)


Thanks in advance

---

### Post by HereInOz on 2007-06-12
You could always get a router which will connect to the cable modem, and that router, once set up,  will initiate PPP authentication and maintain your internet connection.  Then you connect the computer(s) to the router, they get an internal IP address from the router, and all is well.

Costs money, I know, but it will also boost the security and enable you to connect more than one machine to the Internet connection.

---

### Post by Cypher on 2007-06-12
Please get a router with a firewall to put between your cable modem and computer. It is not a good idea to connect the PC directly as you are exposing your computer to all the threats on the 'Net. Windows will be compromised fairly quickly while Linux will stand up for longer..

This will also alleviate any slow-downs of getting an IP as the router will always maintain the IP address your ISP hands out and you will get internal network addresses from the router..

---

