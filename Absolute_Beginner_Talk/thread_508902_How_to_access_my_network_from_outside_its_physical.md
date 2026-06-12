---
title: "How to access my network from outside its physical location"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Peter1234123 on 2007-07-24
I want to access my network (A server, running Ubuntu, and 3 clients, 1 running Ubuntu, 2 running Windows XP)...from work, which is not in the physical vicinity of the network, how would I go about doing this? And what apps would I need?

---

### Post by kngunn on 2007-07-24
It depends on the location and setup of the network you have.  If it is sitting behind a cable modem then you are using network address translation (NAT) to give each machine an IP address (since the cable modem only gives you one).

In that case, you'll need a router that support VPN pass-through.  NetGear makes one of these (you have to buy client software -- NetGear Prosafe -- seperately).  Just Google "netgear vpn" for more information.

---

### Post by p_quarles on 2007-07-24
What do you need to be able to do via this connection? Because there are a number of tools that would allow you do different things, most of them free.

If you just want to be able to adminster your server and have access to files, you could use either OpenSSH-Server or Webmin. SSH is a pretty simple command line connection. Webmin is  (as the name suggests) a web-based application that gives you a GUI for operating a range of server functions, including file transfer. 

There are other things out there, too, depending on what you want to be able to do. 

To get any of these things working, though, you'll need to be able to configure any and all routers, modems, and anything that else that has a hardware firewall to forward requests to the appropriate machine.

---

