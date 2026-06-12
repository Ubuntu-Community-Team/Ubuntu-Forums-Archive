---
title: "Configure Network Connection"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by danootz on 2006-06-28
I've looked through several threads regarding setting up my network connection and I've tried:

1. "sudo ppoenconf" and I recieved an error. I forgot the exact message.

2. Went to the Network Settings in System and activated eth0. I have it set the DHCP. And even tried static and entered the information I found about the IP address and subnet and all that stuff. I set the default connection to eth0 too.

3. I even went to Firefox and disable the ipv6.

I had this problem initially after installing Ubuntu and I tried all the things I mentioned above and it didn't work. I turned off the computer and the next morning I started up Ubuntu and tried Firefox just to see and it worked. Today I tried and I'm having the problems again.

Any suggestions? Do I need to completely shut down ubuntu after a change in Network Settings? Please help me as I'd like to play with Ubuntu more (wean myself off Windows) but I need to at least have a working connection.

I have a cable modem connected to a Linksys Router. My system is dual boot.

---

### Post by ProjectGod on 2006-06-28
good idea to check your windows settings for internet conectivity.

does your broadband connection require you to always supply a user name password? or is it always "ON".

please print your ifconfig output etc etc...

can you log into the router?

---

### Post by djsroknrol on 2006-06-28
Is your router setup properly?...
i.e. DNS, WAN connection address, subnet mask and default gateway?  I have a Lynksys router also...forgot those things myself...and you should not have to reboot when you make the changes in System>Administration>Networking....

---

### Post by FuzZy2006 on 2006-06-29
if you have an internet connection that uses pppoe i recommend rp-pppoe ([http://www.roaringpenguin.com/penguin/pppoe/rp-pppoe-3.8.tar.gz](http://www.roaringpenguin.com/penguin/pppoe/rp-pppoe-3.8.tar.gz)) cos' i have several problems with pppoeconf ;)

---

