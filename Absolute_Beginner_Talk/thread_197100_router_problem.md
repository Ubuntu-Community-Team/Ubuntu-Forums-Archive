---
title: "router problem"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by benner on 2006-06-15
I am running dapper on a dell p3 450 w/256MB.  I had no problem connecting to the Internet.  It was set up for a PPPoE/DSL modem.  I just got my windows notebook back from the shop and put a router into the mix.  The windows machine connected without a hitch so I know it is working.  I have a dmz set up for both allocated IP's (192.169.1.1 and 2) so i know it isn't a firewall problem.  i changed the settings in the linux machine from DHCP to static IP and put in the address (192.168.1.2), etc... and I can't get it to connect.  suggestions?  Thanks...

---

### Post by ikilledclown on 2006-06-15
Don't know a great deal about this, but  know my wireless didn't work at first because my ubuntu basically didn't know the laptop had built in wireless.
All I know is I found a menu with all my computer hardware and just activated it from there, I'm sorry it's so vague, and I probably haven't helped you at all! But hey I try!!

---

### Post by Kilz on 2006-06-15
[QUOTE=benner]I am running dapper on a dell p3 450 w/256MB.  I had no problem connecting to the Internet.  It was set up for a PPPoE/DSL modem.  I just got my windows notebook back from the shop and put a router into the mix.  The windows machine connected without a hitch so I know it is working.  I have a dmz set up for both allocated IP's (192.169.1.1 and 2) so i know it isn't a firewall problem.  i changed the settings in the linux machine from DHCP to static IP and put in the address (192.168.1.2), etc... and I can't get it to connect.  suggestions?  Thanks...[/QUOTE]
If you setup a static IP, did you put in the Subnet Mask and Gateway address? The easiest way to find them I know is, since your windows laptop is working bring up a command prompt and type in ipconfig. It should give you the addresses. Someone may know a Linux way to do it, but I havent learned that yet.

---

### Post by benner on 2006-06-15
yep.  same settings as the windows machine except the IP.  doesn't work...

---

### Post by Kilz on 2006-06-15
[QUOTE=benner]yep.  same settings as the windows machine except the IP.  doesn't work...[/QUOTE]
I found this, it may help you work through the problem.
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

