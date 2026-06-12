---
title: "Network - Internet"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by JoeZ on 2006-01-08
I really need some bad help here...
Okey so here is my problem.
One computer is on Windows XP. Has an internet connection to it.
I have a router that both computers are connected to.
The other computer has Ubunto.

How do I share Internet so I can get internet on both?
The one with Windows XP, has a wireless intenet connection to it.

On the router I have one WAN port and four others (1, 2 etc...).
Should I connect the XP computer in the WAN port?

And maybe most important, how do I get intenet on the one with Ubuntu?
I now have the XP computer connected with port 1 on the router. And the Ubuntu computer with port 2. They find each other, I have no manual given IP to any of them.

How do I make this work?
The way I figure it should'nt be that hard...

Thanks for the help ;)... :)...

---

### Post by estel on 2006-01-08
And you're getting your WAN through wireless? Where is it from ultimately? :s

---

### Post by JoeZ on 2006-01-08
Internet is coming through a Wireless connection on the computer with XP.
It grabs signals from 'the house' that my parents live in. I myself is located on the yard.

So I grab signals to the XP computer and connect the XP computer with another router. Which is also connected to the Ubuntu computer...

How do I make this work?
And how do I get internet on the one with Ubuntu?

---

### Post by mips on 2006-01-08
This one should be easy, you can set your Linux PC up for DHCP. Just plug it into one of the wired ethernet ports.

If it does not work please do the following from your windows machine:
Open a command prompt/dos window.
Type **ipconfig /all**
Copy and paste the output here, can xxx out sensitive stuff if there is any.
We can then look at your windows config and do the same on linux

---

### Post by Zahrber on 2006-01-08
Well this is what you do if I understand you correctly. 

1. You plug the computers into one of the ports not the WAN port. 

2. Make sure your router is configured for DHCP. This is usually the default setting for most newer routers these days. If not you log into the router by using a web browser from either windows xp or ubuntu linux. Mine I use the IP 192.168.1.1 in Firefox and then I can login and change things in my router.

3. You then go to your network places and go to properties of your network interface you are using either wifi or NIC and make sure DHCP is selected for network address and DNS servers.

4. Then in ubuntu there is a place under system tools I believe that is called network connections and go to properties of that and make sure DHCP is selected for that device and you should be golden.

I am at work so I can't look at ubuntu to make sure exactly what it is called but is should have eth0 in it when you open it, or something like that.

---

