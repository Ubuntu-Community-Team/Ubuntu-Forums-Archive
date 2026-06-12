---
title: "Lan With Windows XP under xubuntu 7.04"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by vagX69 on 2007-05-13
Hello everybody.

First post, totally newbie (and Linux noob) here.

I'm trying to set up a Lan with a machine using WinXP so that I can share Internet from the Win pc. I have found some info how to, but it concerns Ubuntu 
[I]
Goto "Places" -> "Network"
select "Connect to Server..."
under "Service type" select "Windows Share"
under "Server", write <windows computer name>/<share name>[/I]

Can somebody please help me? Note that the Xubuntu machine is not on the net so I can't download Samba or anything. Also I must mention that I use a modem and not a router :S

Thanx in advance

---

### Post by Martin on 2007-05-14
I don't think you're going to be able to do anything more than telnet or ftp to a windows machines without samba being installed on the linux box. Even telnet and ftp will need to be installed and setup on both. Can you not connect the linux pc to the modem just for the purpose of connecting to the net to install samba etc.? I gake it you've wired both of them up and have sorted out IP addresses (or DHCP) and stuff?

---

### Post by vanadium on 2007-05-14
It is a matter of setting up internet connection sharing on the Windows XP computer. See for example this link

[http://www.practicallynetworked.com/sharing/xp_ics/](http://www.practicallynetworked.com/sharing/xp_ics/)

Then, you should be able to use standard internet configuration on the client. On the link posted above, there is info on how to do this for Windows 2000. This will give you some idea of the kind of settings you need, but you will need to "translate" the instructions to the Ubuntu System - Administration - Network gui.

---

