---
title: "Kill iptables"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-11-11
Hi,

I need to get  vpn connection working and I've been struggling my *** off! Before i learn to configure iptables, how to I kill it? It doesn't seem to be in /etc/init.d? I just want a clear line to the internet.

---

### Post by Colro on 2007-11-11
Just install firestarter:

```
sudo apt-get install firestarter
```

and open the port(s) you need. If you really must, then just 'stop' firestarter (which will, in turn, disable iptables).

---

### Post by RudolfMDLT on 2007-11-11
I have tried firestarter - but it needs to be bound to an interface. When binding to the Athoros card, it gives me an error: Device not ready. So i just want to stop all firewalling! :)

---

### Post by salamba on 2007-11-11
iptables might not be your problem,  but to find out:

sudo iptables -L    <--   will list any current rules
sudo iptables -F    <--  will clear (flush) the rules.

so flush the rules then see if your vpn works.    How are you trying to make the vpn anyway?

---

### Post by RudolfMDLT on 2007-11-11
I installed firestarter on the desktop pc and it was blocking a port. now that I stop it, the connection goes through I presume and I get a bad username or password error. The username and password I use work in windows.

How I set it up:

I click on the network icon top right and select vpn connections, then I click configure vpn and select the PPTP option. I then add the server, 146.141.3.2. click next and click finish. 

When I activate the connection I get a "connection error". stopping the firewall doesn't make a difference now, although it used to block a port.

Enabling MPPC compression generates an instant "Bad Username or password" error. And I can't get passed that! 

here are the instructions given by the university:

> Mac OsX VPN Account Setup

1.Click on &#8220;Go&#8221; &#8594; &#8220;Network&#8221; and then open &#8220;Internet Connect&#8221; (from the Dock)
2.From &#8220;Internet Connect&#8221; click &#8220;File&#8221; &#8594; &#8220;New VPN Connection&#8221;
3.Select &#8221;PPTP&#8221; and then &#8220;Continue&#8221;
4.Click on the arrows next to &#8220;other&#8221; in the &#8220;Configuration&#8221; field and select &#8220;edit configurations&#8221;
5.From the Edit Configurations screen, enter
I.In the &#8220;Description&#8221; field enter any name that will help you identify the connection
II.In the &#8220;Server Address&#8221; field enter 146.141.3.2
III.In the &#8220;Account Name&#8221; field enter the account name given to you (usually your staff/student number)
IV.In the &#8220;User Authentication&#8221; field, make sure the password radio button is selected.
V.In the &#8220;Encryption&#8221; field select &#8220;Maximum (128 bit only)
6.Click &#8220;OK&#8221;
7.Enter your password and click connect to make a VPN connection

They are for mac, but it's the best info available. Windows has a client that needs no configuration so I can't learn anything from it.

In order to use the "built in" vpn functions you need to install the VPN extensions to network manager from Synaptic. also the VPN extensions don't work if your running Kubuntu! 

Also, the university staff told me that they use IPsec.... Some how that conflicts with PPTP? or not?
Thanks for any help!

Rudolf

---

