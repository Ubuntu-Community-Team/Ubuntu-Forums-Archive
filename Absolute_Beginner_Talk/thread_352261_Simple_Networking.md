---
title: "Simple Networking"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Hathaanna on 2007-02-03
I have always used Windows and only recently moved to Ubuntu. I have installed Ubuntu 6.10 on my new network 4 computers. All went fine.
I have these computer connected to a switch and from there to a modem router and then the Internet. All the machines connect to the Internet with no problem. In addition I have a network ready HP printer with its own Network card that was also connected and works fine from the four units.
The problem is that I have been trying to share files between the for units but it does not seem to be possible. I have tried to get information on how to do that but sadly I am getting no where. I need hepl and I hope I can get it form you guys.

I am looking for something simillar to Windows work group with no server attached since I do not have one and do not plan to have one in the future.

Many Thanks

---

### Post by pseudonym on 2007-02-03
Hi, Ubuntu is very network ready but you need to set things up specially. Also, AFAIK all the different options revolve around the client/server model but this certainly doesn't mean you have to have a special server machine to set up a home network. It's just that, in the software, you will have a server program which accepts requests from the clients.

For sharing between Linux and Windows machines there is [SAMBA]("http://us4.samba.org/samba/"), but if you have an all-Linux network you might want to try [NFS]("http://nfs.sourceforge.net/nfs-howto/") (Network File System). There is an Ubuntu howto for it [here]("http://www.ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto").

HTH :)

---

