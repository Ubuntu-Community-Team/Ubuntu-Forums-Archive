---
title: "Plenty available, but no connections in Azureus"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by CafeHarrar on 2007-02-23
Hi there, I am using Azureus v 2.4.0.2 on Ubuntu 6.06.  I am not connecting to any seeds or peers despite having 80 or more listed.  The bar on the bottom right of the screen has begun to say I have a firewall/NAT TCP reachability problem, but when I perform the NAT/Firewall test in the tools menu it says my port is OK.  My port is 55632.  I have set up the forwarding on my US robotics USR5462 router, and set my firewall (Firestarter) to allow incoming connections on that port.  UPnP is enabled on both my router and Azureus.  As is recommended in the Azureus wiki, I have also run the iptables lines in the terminal, although I am not sure what they mean.  That's all the information I can think of, if more is needed please let me know!

---

### Post by kidders on 2007-02-23
Hi there,

You seem to have done an awful lot of things that might be getting in the way of eachother. Depending on your network, you may need to set up port forwarding @ a modem/router box, _or_ enable UPnP, _or_ play with iptables... but a network would need to be quite complex to require all three.

Could you describe your network?

In the meantime, I'll take a wild guess, and assume your Linux box's internet connection is routed through a domestic DSL modem/router combo, and nothing else. If that's the case, you should undo any manual port forwarding, enable UPnP, and see what happens. Playing with iptables would only be necessary if you're running a firewall on your Linux box. If not, you should undo any changes there too.

With luck, that will improve your connectivity (assuming of course that your ISP isn't blocking bittorrent traffic, which is not inconceivable).

Enabling UPnP on any devices between you and the internet should allow Azureus to configure any necessary port forwarding on its own.

---

### Post by CafeHarrar on 2007-02-23
Thanks for your help!  My network is VERY basic, just a cable modem connected to a wired/wireless router (US Robotics model USR5462)  (2 machines wired, 3 on wireless)

I turned off port forwarding and left UPnP enabled, and Azureus did the forwarding on its own, but I still wasn't getting any connections.  My ISP is listed as a bad ISP in the Azureus wiki, so I had RC4 encryption on as the wiki reccomended.  When I turned the RC4 off, I got a few connections to seeders, but just 1 or 2 on the torrents with only 10 or 15 seeders, none one the one with over 80 (and no peer connections at all)  Any Idea why this might be or how to fix it? 

UPDATE:  It seems I just needed it give it some time, and now I am connecting to at least a few seeders, with semi-acceptable download speeds.

But alas, a new problem.  With UPnP it seems that my computer's firewall is blocking bittorrent traffic... When running, download speed drops to nil, when I turn off the firewall, speed picks back up.  I am using Firestarter v 1.0.3...

And now no DL speed...  WTF?????

---

### Post by kidders on 2007-02-24
> **CafeHarrar said:**
> it seems that my computer's firewall is blocking bittorrent trafficYou should open the required port(s) to incoming traffic.

If you're unsure, one way to *definitively* check the availability of a port is to bind something a bit simpler than bittorrent (a telnet, SSH or web server maybe) to it and try to connect to yourself from outside your LAN. If that works for you, then you know Azureus is the problem.

---

### Post by nonewmsgs on 2007-02-24
where would you enable UPnP

---

### Post by kidders on 2007-02-25
That depends very much on how your network is laid out. In theory, you would activate it on everything between you and the internet that is capable of routing.

**Edit:** It's worth bearing in mind that UPnP should not be used unless you have a particular reason for wanting it (eg more than one computer requiring NAT/forwarding of the same port range on an on-demand basis), because it's not considered particularly safe.

---

