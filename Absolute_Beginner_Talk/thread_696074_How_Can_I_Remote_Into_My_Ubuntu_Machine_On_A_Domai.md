---
title: "How Can I Remote Into My Ubuntu Machine On A Domain From My Windows Machine?"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Minker17 on 2008-02-13
I'm trying to remote into my Ubuntu machine at work from my Vista machine at home.

The Ubuntu machine is not on a domain like all the windows machines. I have set remote desktop (on Ubuntu) to Allow users to view/control desktop.

Would it be as simple as connecting to VPN on my Vista machine and then typing in my IP address?

How would I find my IP address? I did the ifconfig in the terminal, but I'm unsure as to what my actual IP address is since all the PCs on the Domain start with 10.1.0.X

Is this going to be possible? Can I put Ubuntu onto a domain to accomplish this?

---

### Post by max renn on 2008-02-13
I actually haven't done this yet, but should get around to it tonight.  I use VNC4 because I have a mixed network and I am used to it.  I have a different network issue to work on first.  

You have one NIC card?  then the adapter is called eth0 when you do the ifconfig.  Do you have your nic installed to automatically get the ip using dhcp?  Then you should have the 'inet addr:10.1.0.XXX' address showing.

As far as whether the RDP are compatible, I am not sure.  I think I read somewhere it was.

---

