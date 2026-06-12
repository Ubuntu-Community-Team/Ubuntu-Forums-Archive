---
title: "Cant get an IP address"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-05-14
Hello I have an netgear MA111 usb wifi adapter. The adapter is recognized and associated with my router, but the router will not give it a ip address. When I give it a static ip address wifi radar says that it is connected with that IP address but I still do not have internet and cannot ping anything on the network. 

When I plug this adapter into an XP machine it connects the router no problem. Is it possible that this router (Linksys WRk54G) simply will not talk to a linux machine, or is it a linux configuration problem.:confused:

---

### Post by Resurrection on 2006-05-14
Well considering that your router is based on the WRT54G, and that you can run  Linux on the WRT54G's internal memory (link:  [http://www.batbox.org/wrt54g-linux.html]("http://www.batbox.org/wrt54g-linux.html")) I would think that compatibility with Linux would not be a problem at all.

This sounds like a configuration issue within Linux itself.  I haven't had to set wifi up on Linux, but there is a ton of posts on the forums about this problem, so sit back for a second, and someone will post who can better diagnose your problem.

Edit:  Have a look at this How-to:  [Ndiswrapper how-to]("http://www.ubuntuforums.org/showthread.php?t=31926&highlight=ndiswrapper")
Sounds like you need ndiswrapper.  
From a google search:
> With ndiswrapper, virtually every miniPCI (builtin), PCI, PCMCIA (Cardbus only) or USB wireless network card works in Linux. Although ndiswrapper is intended for wireless network cards, other devices are known to work: e.g., USB to serial port device, ethernet card, home phone network device etc. See Wiki entry List for devices known to work.

Someone else should still confirm me though before you start working on that.

2nd Edit:  In the future please refrain from starting mutipile threads with the same issue.  It just divides the effort of people trying to help you.
[http://www.ubuntuforums.org/showthread.php?t=176398&highlight=ndiswrapper]("http://www.ubuntuforums.org/showthread.php?t=176398&highlight=ndiswrapper")

---

