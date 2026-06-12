---
title: "Help required - Networking"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Bluebaron on 2006-10-12
First of all here's what I want to do:-

I have 2 pc's, 1 running XP SP2 and the other running Ubuntu 6.06, and I want to network the 2 together.

I would like to use the Ubuntu PC as the first point of connection to the internet (it has 2 NIC's.) for use with bittorrent, and the Win XP pc (onboard Gigabit LAN) I just want for normal browsing.

What are the drawbacks of doing it this way around?
What do I need to do in both Ubuntu and Win XP to be able to do this?

---

### Post by Charles Hand on 2006-10-12
This sounds like a reasonable configuration. You can even create sophisticated firewall rules on the linux box to protect the (more vulnerable) XP box.

One thing you'll need is this:
[http://www.ubuntuforums.org/showthread.php?t=88206](http://www.ubuntuforums.org/showthread.php?t=88206)

so that your computers can refer to each other by name.

---

### Post by Charles Hand on 2006-10-12
I think firestarter is going to be able to do all the routing you need to do on the linux box. Then all you do on the XP side is give the linux box address as gateway. 

A search of these forums for "firestarter" will unearth a whole lot of info.

You can run a DHCP server on the linux box and let the XP configure itself through that. I don't know how to set up the dhcp server, but a search for "dhcp server" on these forums ought to turn up the answer pretty quick.

You'll have to have the linux box forward DNS, too. I'm sorry, I don't know how to do that, but I wouldn't be suprised if firestarter did that, too.

---

### Post by Bluebaron on 2006-10-12
Right, I got firestarter installed, but now it tells me that eth1 is not ready.

Any ideas??

---

### Post by Charles Hand on 2006-10-13
Ah. I'm looking at firestarter now. Looks like it will do the trick for you.

What do you get when you type
```
ifconfig
```
in a terminal?

(Start a terminal using Applications->Accessories->Terminal)

---

