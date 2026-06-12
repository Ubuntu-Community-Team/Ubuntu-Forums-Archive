---
title: "Trying to Get a Bittorrent Client Working"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-01-29
I am trying to get Azureus up and running. I forwarded a port in my router and pointed Azureus. From previous Windows experience, I understand that I also have to give it access through the firewall pre-installed in Ubuntu. How would I go about doing this?

Thanks everyone.

---

### Post by smurphy_it on 2008-01-29
I don't believe the firewall is enabled by default.  So you shouldn't have to worry about it.

---

### Post by crjackson on 2008-01-29
> **Crumpets and Jam said:**
> I am trying to get Azureus up and running. I forwarded a port in my router and pointed Azureus. From previous Windows experience, I understand that I also have to give it access through the firewall pre-installed in Ubuntu. How would I go about doing this?

Thanks everyone.

Unless you have installed a firewall GUI like Firestarter, or configured your IP Tables otherwise, the port should be open already.  It's my understanding that Ubuntu doesn't come preconfigured with ports closed, because there are no default services that would respond to any probing anyway (otherwords - it's already stealth so no need).

I could be wrong, I'm no expert on this but I had the same question for different reasons awhile back and that's what I took away from the experience.

---

### Post by Crumpets and Jam on 2008-01-29
> **smurphy_it said:**
> I don't believe the firewall is enabled by default.  So you shouldn't have to worry about it.

I thought all ports were closed by default?

---

### Post by cozmicharlie on 2008-01-29
Are you sure you are firewalled?  Check in Azureus that you have an open port.  Go to tools>NAT/firewall test and run the test. If it says "OK" then you are not blocked and should be good to go .  If it says you are blocked then it could be at the router or a firewall.  I believe there are command line ways to change firewall settings but the easiest is to install Firestarter from Synaptic.  You can use this to change the settings (note Firestarter is not the firewall it is only a graphical interface that allows you to change the tables).  My guess though is you are not firewalled.

---

### Post by bumanie on 2008-01-29
I can't help with azeurus, but I agree all ports are closed on ubuntu by default. I checked the internet,
> By default, Ubuntu ships with no open ports on public interfaces. In other words, a "port scan" would show all closed ports, nothing open. [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security) 

---

