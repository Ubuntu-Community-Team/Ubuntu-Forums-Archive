---
title: "ADSL vs DSL"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by DaComboMan on 2007-01-16
Hi,

The other day i ran a CD copy of UBUNTU for the first time and (it is incredible!) could not connect to the internet.

I have a Compaq Presario which connect through a Network on DSL connection and have enough room on it to run UBUNTU directly from the hard disk (after i figure out on how to install it).  But first, i would like to know how to proceed on how to connect to internet.

-Newbie

---

### Post by bunabattoir on 2007-01-16
Insufficient data.

Is there a router between the PC and the DSL modem?
If so, does it have DHCP turned on?
If not, did your provider give you a static IP?

---

### Post by Peti29 on 2007-01-16
Have you tried 'pppoeconf' (in a terminal)?

---

### Post by BarfBag on 2007-01-16
Go to System -> Administration -> Networking.  Make sure it's set on DHCP.

Do you have a router that your PC goes through to access the modem, or is your PC connected directly to the modem?  If it's connected to a router, make sure DHCP is enabled.  Access your router settings.  This is usually done by typing 192.168.1.1 into the address bar of your browser, but the number varies.  A user name and password box should come up.  If you've never done this before, both should be "admin" (without quotes).  If that user name and password doesn't work, contact the person who set it up for you or your ISP.  Once you're in, look around for the DHCP option and enable it.  If you're connected directly to a modem, the instructions in the first line should fix the problem.

---

### Post by DaComboMan on 2007-01-16
My laptop has access to a Network through a wireless connection (D-Link).
Should i find out how it's modem has access to the web?

---

### Post by AlanRogers on 2007-01-16
> **DaComboMan said:**
> My laptop has access to a Network through a wireless connection (D-Link).Search these forums for the model number of your D-Link wireless card. You will probably find that, as D-Link aren't great at supplying Linux drivers, that this is the source of your problem. Try connecting your laptop to your router using a cable rather than wireless, which is as good as guaranteed to work, providing you've followed the remainder of the advice below.

---

### Post by DaComboMan on 2007-01-16
Thank you Alan and a big thank you to the others for dropping a line.
Will keep this thread and test it out as soon as i can find an extra cable somewhere.

:)

---

