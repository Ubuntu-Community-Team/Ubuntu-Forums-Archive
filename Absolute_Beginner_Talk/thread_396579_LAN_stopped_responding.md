---
title: "LAN stopped responding"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by mkjarema on 2007-03-29
I have been using Edgy for around 60 days.  I have accessed wireless through a broadcasted SSID, but have yet to connect with my non-broadcasted SSID.  That isn't the worst problem.  I have two LANs that I use, work and home.  I connect at work fine and plug in at home with no problem.  Today when I plugged in at home, I didn't get a response.  I have check all the network settings that I usually check and I am not getting anything.  I have checked two cables, and the switch all are fine.  I am sending and receiving packets, but I am not getting out to the net.

Please help.  Internet has been my largest struggle with the Ubuntu switch and I need to get this working.

Regards:( :confused:

---

### Post by Jonam on 2007-03-29
Have you tried restarting networking by typing the following in a terminal window:

sudo /etc/init.d/networking restart

I occasionally have my wired ethernet stop working and this fixes it.

Jonam

---

### Post by mkjarema on 2007-03-30
Thanks for that command.  I actually rebooted the modem and it worked, i don't know how, because other PCs in the house worked fine....ohh well, I have that command now for future reference 

Thanks!!!!!!

---

