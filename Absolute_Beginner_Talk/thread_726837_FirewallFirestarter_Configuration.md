---
title: "Firewall/Firestarter Configuration"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by dogdog on 2008-03-17
I am setting up a home network with two PC’s – one PC with ubuntu (v 7.10) and the second PC with Vista Ultimate. I use a cable modem so both PC’s are attached to a wired Linksys router. I want the Vista PC to be able to access a shared file on the ubuntu PC. This has been done but I then have a problem when I introduce a firewall onto ubuntu PC (no problem with Vista firewall). I want a firewall on the ubuntu PC even though I have a router in place.
The LAN was originally set up with whatever were the ubuntu default settings for the iptables and the LAN worked fine. I then installed Firestarter. The LAN would not work despite trying to set up the appropriate Inbound Traffic Policies – I tried (i) allow Samba Service from IP address of Vista PC; (ii) allow all inbound traffic from IP address of Vista PC but neither worked.
If firewall is disabled via Firestarter then the LAN connection is established; this connection remains even if firewall is restarted (I think that established connections persist).
Surely it is possible to configure Firestarter to allow PC to PC connection via Samba??
Any suggestions??
What are the default settings for the ubuntu iptables??

---

### Post by ajgreeny on 2008-03-17
As I understand it, all ports are available and open but not listening  for anything in Ubuntu's default setup.  In fact you don't really need a firewall configuration utility in Ubuntu if you aren't running any servers.  Perhaps worth flushing the iptables setup and starting again with ```
sudo /etc/init.d/firestarter stop 
sudo iptables -F 
sudo /etc/init.d/networking restart
```I'm not certain if you will need to restart or reinstall firestarter again but at least this should get your network running again.

---

### Post by dogdog on 2008-03-17
I can get my network running by simply disabling the firewall - that seems analogous to flushing the iptales. However, that is not the real point.

I want to use the firewall configured with Firestarter. Surely there must be a way to cofigure Firestarter to allow the network to connect??

---

### Post by ajgreeny on 2008-03-17
> I can get my network running by simply disabling the firewall - that seems analogous to flushing the iptales.I don't think so but I'm not sure.  I think the iptables is configured by firestarter but not flushed simply by firestarter not running.  You certainly do not need firestarter running all the time, so if you mean that disabling the firewall is simply stopping firestarter, then you certainly have got the whole idea wrong.  Firestarter is NOT the firewall, but merely the configuration editor for iptables, which is the firewall itself.

---

### Post by sayakb on 2008-03-17
This is what I did. I saw all the events that Firestarter blocked. I noted down their ports. Then clicked on Policy tab, then clicked on the Allow Service area and as the Add button became active, I just added the port there. After adding the policy, firestarter allows all traffic from/to that port.

---

