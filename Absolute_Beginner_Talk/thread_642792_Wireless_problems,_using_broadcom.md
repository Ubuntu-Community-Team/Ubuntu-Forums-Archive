---
title: "Wireless problems, using broadcom"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by jess523s on 2007-12-17
Hello, my wireless internet isn't working. I just downloaded Dapper Drake as a dual boot on my HP Pavilion ze4600 laptop and I am trying to connect to a ActionTec Modular DSL router (M1000).
The internet works when I boot XP and it is currently working on my other laptop. (Could that also be a problem? Running two wireless laptops at once?)
I have configured the connection in Ubuntu to go to my SSID and entered the WEP. I have activated it and when I hit OK, nothing bad happens. But I am unable to connect to the internet.
When I click on the Network Connection icon in the top right, I get "SIOCGIFFLAGS error: No such device". It also has a red minus sign next to it.
My current idea of what is wrong is that I need to install a driver for my wireless card, which is a Broadcom BCM4306 802.11b/g Wireless LAN Controller. If you think that this is the problem, do you know where I can find a driver for it?


Merci

---

### Post by macogw on 2007-12-17
Getting that card to work with Dapper is going to be hard and not work well.  You'd have to use ndiswrapper and the Windows driver and it's kind of annoying, and I'm not sure if it'll work with an encrypted connection at all.  7.04 and 7.10 both support that card almost out of the box--you click a checkbox to enable it (while connected wired), and they download the firmware, and that's it.

---

### Post by Gone fishing on 2007-12-17
Have a look at these:

[http://ubuntuforums.org/showthread.php?t=405990&highlight=SIOCGIFFLAGS+error](http://ubuntuforums.org/showthread.php?t=405990&highlight=SIOCGIFFLAGS+error)
[http://ubuntuforums.org/showthread.php?t=197102&highlight=SIOCGIFFLAGS+error](http://ubuntuforums.org/showthread.php?t=197102&highlight=SIOCGIFFLAGS+error)

The second link looks promising.

But why use dapper?

---

