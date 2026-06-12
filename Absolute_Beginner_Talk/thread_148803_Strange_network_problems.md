---
title: "Strange network problems"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by martyo on 2006-03-22
I dual boot Breezy and Windows XP and the particular network I'm on right now will not work in Ubuntu but it will in XP.  The funny thing is that it was working a few days ago and then just stopped.  I've plugged into another network and Ubuntu has recognized it and worked perfectly, so it seems to be this particular one.   It's not terribly important but I prefer using Ubuntu if I can help it.  Any ideas?

---

### Post by Iowan on 2006-03-22
That's not a lot of information to go on... but its a start.  If Windows works, with the problem network, how is it set up?  Is the problem network set up with a DHCP server - or does it use fixed addresses?  The working net - fixed or DHCP?  Netmask settings for working, nonworking, and Windows?  Can you ping from problem net?

---

### Post by martyo on 2006-03-23
Thanks for the reply.  I don't get it, but I got in this morning and it's working.  I know for a fact that neither I nor the network administrator have changed anything.  FYI both networks were DHCP and were accessed with default settings in both Windows and Ubuntu.  I couldn't Ping when this network wasn't working.  Weird.

---

### Post by frodon on 2006-03-23
Do you use firestarter ?

If yes remove it and reboot to see if firestarter didn't set iptables rules that prevent you to access the network.

---

