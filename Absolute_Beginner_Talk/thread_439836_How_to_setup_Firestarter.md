---
title: "How to setup Firestarter?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-05-11
Hi,

I've installed Firestarter to have a GUI to configure the firewall. I connect to internet with ethernet (eth0) and wireless (eth1). However the firewall cannot start when I'm on eth1 and is thus disabled when I'm connected wirelessly :( I've looked into the Preferences and both "Internet connected device" and "Local network connected device" are set to eth0! If I select eth1 as internet connected device when I'm on wireless and start the firewall, I cannot connect anymore. I have to stop the firwall to connect in wireless!!!!!! Why does the firewall no seem to work with wireless connection although it supports eth1?

Moreover even if it were working with wireless, does it mean each time I want to go wireless I have to manually change that to eth1????? If yes that's pretty unconvenient to have to do this all the time, not to mention that Ubuntu doesn't warn me that the firewall is off when this setting is not correct (and as said earlier when I activate the firewall in wireless mode the connection is lost)!!!!

Is there a way to change this so that the firewall remains on when on eth1 or on eth0 without having to manually change that??

Another question: how do I add a rule to open a range of TCP and UDP ports (like 6800 to 6900) in Firestarter??

Thanks

---

### Post by darkworld on 2007-05-11
Er im a newbie but I was told that firestarter isnt a firewall as such.

 Its a graphical front end to what your machine is already doing. As I understand ubuntu installs with all ports closed to start with. If you nmap your ports you can check for any problems.

---

### Post by kilou on 2007-05-11
Yes Firestarter is just the graphical front end but it reflects how your firewall works. When I'm connected to wireless network, Firestarter say the firewall is stopped. If I manually activate it then I cannot connect anymore so I have to stop the firewall through Firestarter but this still means the firewall is stopped ie all ports open. This is weird...

---

### Post by kenny1948 on 2007-06-16
OK,
Newbie here and totally lost. I understand firestarter is not a firewall. It is a management tool--correct?

Problem is everything I read, says find it under Administration--however it isn't there. How do I access it. I want to find out if the firewall is working. Im not concerned about viruses but about someone accessing my computer.  I am on a DSL connection and I access accounts etc online. I do not want someone accessing this information.

:(

---

### Post by ramjet_1953 on 2007-06-16
Three things to consider here:

1. By default, all ports are closed as iptables is set-up that way.

2. Running the GUI for Firestarter requires it to be run in root mode. Doing this is kinda like shooting yourself in the foot, as it is a grave security risk to run an application in root mode on your desktop.

3. If you a re running through a router to connect to the Internet, it can be configured to stealth all ports, anyway.

Regards,
Roger :cool:

---

