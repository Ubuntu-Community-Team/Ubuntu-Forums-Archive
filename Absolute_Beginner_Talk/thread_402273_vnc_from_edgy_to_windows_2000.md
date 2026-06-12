---
title: "vnc from edgy to windows 2000"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by alan34 on 2007-04-05
Hi all!                           love the forums great help:) 

Tried for 2 weeks now to connect to the network at work - pptpconfig (Client to Lan) is now running showing connected to the router but!!!!    (Sure its laughing at me!!!)

I cannot VNC to my pc at work I really need this. We run a Debian server which I sometimes need to look at but I can "putty" through to this from my win2000 machine at work, so the problem I have got is how to see my remote win2000 desktop.

Tried "Terminal Server Client" but just does not work. I can ping the router at work at its fixed IP address but I cannot ping any machines on the local network.

I have seen that edgy is "broken" as far as VNC is concerned but not sure, if I have to wait for feisty thats okay. Please let me know. 

Thanks I think this is a difficult one.............  Going for another free beer now
Listening to Pink Floyd:guitar: 


Ps I put Ubuntu on my pc only 2 months ago not had so much fun in ages its like Oric 1 I just love it!!!!!

---

### Post by BillGod on 2007-04-05
what version of ubuntu are you running.  there is a known bug with edgy when connecting to microsoft ppp vpns.  this was the reason I upgraded to feisty.  The network manager (up by your clock) now has an option to setup a vpn.  I tried for 6 months to get it working on edgy and never got a full connection.  It said it was connected but could never ping anything.  Feisty worked in about 2 minutes.

---

### Post by alan34 on 2007-04-05
Thanks for the response. I have seen that edgy elf just does not "do" VNC/VPN  if I have to wait thats okay just dont want to try whats impossible.   Cheers
:guitar:

---

### Post by steve.horsley on 2007-04-05
Hold yer horses. I'm using Edgy, and I use PPTP into work (MS access serever) and the use VNC over that to work on (windoze) servers at work. 

Terminal Server client works fine. Just choose VNC protocol and enter the server address. When you click connect, a small password window appears.

PPTP took some googling and several text files edited by hand. I used this guide, and chose to configure by hand:
[http://pptpclient.sourceforge.net/howto-debian.phtm](http://pptpclient.sourceforge.net/howto-debian.phtm)
Actually, I did the configuration in Breezy and have just copied the configuration files from Breezy->Dapper->Edgy when I upgraded. The command to start the VPN is **pon <target-name>**
and then I use 
**plog -f**
to watch its progress connecting.

---

### Post by Azalin on 2007-04-06
> **BillGod said:**
> what version of ubuntu are you running.  there is a known bug with edgy when connecting to microsoft ppp vpns.  this was the reason I upgraded to feisty.  The network manager (up by your clock) now has an option to setup a vpn.  I tried for 6 months to get it working on edgy and never got a full connection.  It said it was connected but could never ping anything.  Feisty worked in about 2 minutes.

You say you got it up and running within 2 minutes, in Feisty I get a connection but for some reason I can't VNC nor TSC anywhere on the VPN. When I ping I either get a message saying I am not allowed to ping to that address (which is the address of the VPN server). When I take down the firewall, I don't get messages saying pinging to the address is not allowed, it just doesn't show anything. It seems it can't find the address. My router is set up properly and the VPN server is working properly as well since I cán access the VPN with a Windows VM but I hate using a VM for VPN access. Any ideas?

---

### Post by alan34 on 2007-04-06
Hi again,

Thanks for all the ideas. I'm afraid  I totally trashed my edgy elf operating system last night - lost gnome/everything - not a happy bunny.

I cannot continue this until I get everything back up working again.

Thanks again

I will be back:) 

:guitar:

---

