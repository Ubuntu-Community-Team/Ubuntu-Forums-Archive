---
title: "Internet connection being timed out?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-03-10
About every hour or so, I find myself unable to connect to the Internet. That does not mean that Firefox or Evolution says that I am not connected to the Internet, just that it seems to keep loading... and loading.... until it times itself out. I have to reboot to be able to use the Internet, and my computer's getting hot.

 Can anyone help?

---

### Post by ZeroWing on 2007-03-10
Guys? Come on. This is sort of urgent. I have to use windows now to avoid losing my internet connection.

---

### Post by piratejim on 2007-03-10
That seems to be a similar problem to what I have.... In my case the IP address of the DNS I want to use keeps getting replaced (about every hour or so) by an IP address within my network (ie 10.1.1.1).
Although I have not got a solution and I don't knmow what is causing it,  I just need to replace the /etc/resolv.conf file with a backup file I have and everythings seems to work again.... 

(PS I installed Ubuntu less than a week ago so I am certainly still learning too)

---

### Post by ZeroWing on 2007-03-10
> **piratejim said:**
> That seems to be a similar problem to what I have.... In my case the IP address of the DNS I want to use keeps getting replaced (about every hour or so) by an IP address within my network (ie 10.1.1.1).
Although I have not got a solution and I don't knmow what is causing it,  I just need to replace the /etc/resolv.conf file with a backup file I have and everythings seems to work again.... 

(PS I installed Ubuntu less than a week ago so I am certainly still learning too)

 Hm... from my experience with Windows, this could be because the DCHP server on Ubuntu is trying to change our I.P.

 I'd like to test this theory out. Does anyone know how to create a static I.P. address in Ubuntu?

---

### Post by ZeroWing on 2007-03-10
Alright... don't try do set a static IP. I just had a fun time trying to fix my Linux...

---

### Post by BKonkle on 2007-03-20
I'm having a similar problem with my system - it loses connectivity overnight.  When I reboot, everything is fine.  My Windows laptop PC wirelessly connects to the same network, and has no problems.  Also, my Linux server computer connects to the same network using a Linksysy WRT54G in client bridge mode, and has no trouble maintaining a continuous connection.

What logs can I look through to try to diagnose this problem?

Thanks!

---

### Post by ZeroWing on 2007-03-20
Wow. I forgot I started this thread.

 How good is your wireless router? How strong is the signal strength?

---

### Post by BKonkle on 2007-03-20
Well, I'm actually hooking up my Ubuntu desktop PC (the computer I posted about) to that same WRT54G in client bridge mode.  The connection is at about 82% signal strength, according to the router's status page.

It has to be something that the Ubuntu desktop is doing that is dropping the connection.  I just have no idea where to start looking.

Thanks for any help you can provide!

---

### Post by Baji on 2007-04-17
I've got the exact same problem, internet connection just drops out, seems something with DHCP/DNS?! Ill have a look if resolv.conf changes can anyone point me to the program that might cause this?

ps. /etc/networking restart doesnt fix it. only a reboot

---

