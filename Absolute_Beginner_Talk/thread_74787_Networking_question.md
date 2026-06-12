---
title: "Networking question"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by ~J~ on 2005-10-12
This 'may' not be a beginner question as such, but it's something I don't know due to total lack of knowledge.

Here goes....

I have my PC and a Netgear834G Wireless router.  The router also comes with 4 ethernet ports to connect additional devices.  No probs there.

Starting next week, I'll be working from home upto the new year, and I'd like to know if it's perfectly feasonable to do the following...

1) Use the wireless card on my PC to the wireless settings of my router to have 1 dedicated connection

2) Use a CAT5 cable from my PC to the router to have a second dedicated connection

3) Use the Ubuntu/Gnome Remote Desktop application to connect to a Windows XP computer via a VPN of either the wireless or the ethernet connection.

4) Use the other connection to have internet connection 'outside' of the VPN.



Basically, what I'm saying is that I'd like to connect to my VPN and access the PC yet still be able to download stuff, few websites on my own connection.  If I had a modem attached to the PC, I guess it would be difficult as my PC would only see one connection to one place.  But, by having 2 different methods of connecting to the internet (wireless and ethernet), would I therefore be able to have both a VPN AND a normal internet connection through the router?

Toughy or easy? :)

---

### Post by mlomker on 2005-10-12
I'm not clear on this.  You need to VPN into work and then access a WinXP machine at the office?  What brand of VPN software are you using?  If properly configured you can still access the Internet while connected to a VPN (I'm the firewall admin for my company), but the technology that you're using or security policies may vary.

Whether or not a dual connection will work will depend upon the VPN software, so I can't answer that.

Rdesktop connects to WinXP without a problem.  I'm a Windows network admin and use it all the time to manage my servers.

---

### Post by ~J~ on 2005-10-12
Thanks for the reply.

Yes I need to VPN into work to access a WindowsXP machine.  Ideally I'd like to use the built in Windows Remote Desktop, but I have no problems in installing VNC on it if that's a better option.

I'll have a look at RDesktop.

Thanks again,

---

### Post by mlomker on 2005-10-12
> I'll have a look at RDesktop.


Rdesktop is the Windows remote desktop client.

---

