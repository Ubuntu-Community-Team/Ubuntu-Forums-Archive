---
title: "Simple stupid wired connection problem"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by moto89 on 2008-01-15
I'm sure this is a very simple problem, but one I cannot solve nonetheless. I have been away from my computer for the entirety of the holidays, and have just now returned (lucky me). When I left I had a fully functional ethernet connection, and now that I have returned I'm having issues. When I boot up Gutsy, I get the typical spinning connection icon, and then get the connected icon, yet have no intranets. When I pull up the properties, I get this:

Interface:                         Wired Ethernet (eth0)
Speed:                              100 mb/s
Driver:                               sis900 

IP Address:                      0.0.0.0
Broadcast Address:       0.0.0.0
Subnet Mask:                  0.0.0.0
Default Route:                0.0.0.0
Primary DNS:                  0.0.0.0
Secondary DNS:             0.0.0.0
Hardware Address:       00:11:D8:24:DD:78 

However, on my feisty install (same machine) I have no problems whatsoever, so I know that it is a software issue. Any help is much appreciated, and I'm feeling kinda dumb at this point since I'm pretty sure that this is a simple problem.

---

### Post by feistybird on 2008-01-15
What type of connection you are using to connect to the internet? via LAN or dial-up ADSL?

Have you tried to run "pppoeconf" again in the Terminal?

---

