---
title: "Ubuntu from XPpro"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Margrove on 2007-01-27
Hi there,
I've just had my first taste of Linux by courtesy of Ubuntu and I must confess that I am very impressed.
I have 3 machines in the house running XP Pro, wirelessly networked. For maintenance I can access my daughter's and wife's machines from my own using Remote Desktop Connection, which works quite satisfactorily at the moment. A 4th machine is connected to an ADSL modem via a wireless router with Ethernet cable, in the customary manner.
It's occurred to me that for network security it would make better sense to have this 4th machine (running Ubuntu) link up directly to the www and the have the rest of the network access the Web through this machine, using VNC. Ideally each user would run his/her own instance of Firefox through seperate accounts, invisible to each other and preferably simultaneously.
Is this possible at all or even a good idea?
If so could any kind and knowledgeable person give me a broad idea of how one would implement this?
I'm obviously a newbie so please don't get too technical just yet!
TIA
Martin
Reply With Quote

---

### Post by riven0 on 2007-01-27
I've never done such a setup myself, but it seems to be possible. Here are some howto's to get you going. See what works best for you:

[ HOW-TO Secure Remote Access - Hamachi+VNC]("http://ubuntuforums.org/showthread.php?t=135036&highlight=vnc")
[URL="http://ubuntuforums.org/showthread.php?t=122402&highlight=vnc"]
 HOWTO: Set up VNC server with resumable sessions[/URL]

Hopefully, that'll be some help. Just remember to follow step by step and copy and paste the instructions, so you don't mess up with it.

---

### Post by ondrugs on 2007-01-28
i'm not too cluded up on the whole ubuntu thing, but i would imagine you install something like _vnc-server_. then each user should run:

**vncserver -password**
**vncserver -depth 16 -geometry 1280x768 :4**

that will set the password and then the colour depth and resolution for the vnc session. as well as the vnc port to connect to.
so on your windows machine, install a vnc client (eg tightvnc) and connect to the ip of your ubuntu box with a **:4** on the end:

eg 192.168.2.4:4

that's the theory of course. :D

---

### Post by Margrove on 2007-01-28
[I]>>>each user should run:

vncserver -password
vncserver -depth 16 -geometry 1280x768 :4

[/I]
From windows?

---

### Post by ondrugs on 2007-01-28
no sorry,
each user needs to SSH in, or do it from the machine directly in a console session (like xterm). they only need to set the password once, but will need to set the vncserver session up each time the box is rebooted.

---

### Post by Margrove on 2007-01-28
Thank you, I understand.

---

### Post by medley on 2007-01-28
> **Margrove said:**
> Hi there,
I've just had my first taste of Linux by courtesy of Ubuntu and I must confess that I am very impressed.
I have 3 machines in the house running XP Pro, wirelessly networked. For maintenance I can access my daughter's and wife's machines from my own using Remote Desktop Connection, which works quite satisfactorily at the moment. A 4th machine is connected to an ADSL modem via a wireless router with Ethernet cable, in the customary manner.
It's occurred to me that for network security it would make better sense to have this 4th machine (running Ubuntu) link up directly to the www and the have the rest of the network access the Web through this machine, using VNC. Ideally each user would run his/her own instance of Firefox through seperate accounts, invisible to each other and preferably simultaneously.
Is this possible at all or even a good idea?
If so could any kind and knowledgeable person give me a broad idea of how one would implement this?
I'm obviously a newbie so please don't get too technical just yet!
TIA
Martin
Reply With Quote

If it were me, I'd set up the Linux system as the internet gateway through which all the other XP boxes access the internet. This does two things: it allows you to set up fairly sophisticated firewalling and logging, and also precludes having to use VNC (or something like it) on the the XP systems. This is a bit slow and there's no need.

Take a look at Guarddog. You can have your modem plugged into the Linux system, and on all the XP boxes, tell them that the 'gateway' is the IP address of your Linux system. Set this one up with a static IP address (that is, tell it what it's address is, rather than using DHCP from the wireless router), and then tell all the other systems to use that one as the gateway.

I've thought about doing this myself, rather than having all the systems on my network talk directly to the router for internet access.

---

### Post by rccharles on 2007-01-28
> **Margrove said:**
> Hi there,
I've just had my first taste of Linux by courtesy of Ubuntu and I must confess that I am very impressed.
I have 3 machines in the house running XP Pro, wirelessly networked. For maintenance I can access my daughter's and wife's machines from my own using Remote Desktop Connection, which works quite satisfactorily at the moment. A 4th machine is connected to an ADSL modem via a wireless router with Ethernet cable, in the customary manner.

Does the route have a firewall?  Work with the firewall in the router.  Configure your firewalls in each machine for added security ( perhaps ).


I would not rely on VNC providing extra security.  Since the machines would be still attached to the Internet, an attacker still could attack your machines unless you used some firewall to prevent this.

I think you are a bit worried.  There are lots of malware attached to email and ie security is poor.  I'd:
-- switch to firefox for web browsing
-- power off your machines when not using.
-- provide instruction about opening email.

Robert

---

### Post by Margrove on 2007-01-31
Thank you all! Exactly what I was looking for. I'll do some experimenting  and let you know how I'm getting on.
Martin

---

