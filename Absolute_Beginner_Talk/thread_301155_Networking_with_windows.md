---
title: "Networking with windows"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by dizzylizard on 2006-11-16
Ok, before the flames start, I tried to search for this information, but all the how-to's out there apparently assume a greater degree of familiarity with Linux/networking than I have.  Here's the setup:  Box 1 Is a POS frankenbox built from spare parts (actually, recycled parts), running Ubunto 6.06 (Dapper).  Box 2 is an off-the-shelf running XP Mediacenter.  Both are plugged into a Linksys Wireless broadband router, which is plugged into a cable modem.  Both boxes have 100% internet functionality, but now I want to be able to share files between the two, print from the XP to the Linux box, etc, etc.
 I KNOW!!!  It's really simple, so easy a caveman could do it, just a matter of f-stab this and ping that and blah, blah, blah.  Unfortunately, I'm really new to Linux...and have no clue what I'm doing!!!  Is there an ultra-basic, easy-to-understand, step-by-step procedure I can follow posted somewhere?  I'm pretty good at following the directions, just need to know where to find them!

---

### Post by echo $USER on 2006-11-16
You need to install samba...

[http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server](http://easylinux.info/wiki/Ubuntu_dapper#Samba_Server)

You can connect to the windows box from linux by default just go to Places > Connect to Server > Choose windows share > Then punch in the ip address of the windows box.  But to connect from the windows box you need to install samba (it tricks the windows box into thinking its talking to another windows box.

---

### Post by dizzylizard on 2006-11-17
And how do I get the IP address of the windows box?  I can see it in the nautilus browser, but don't know what to do with the desktop.ini files there...

---

### Post by mep on 2006-11-17
To get the ip address of your win xp box:

Start ==> Control Panel ==> Network Connections ==> Right Click on Local Area Connections and choose Status.  Then click on Support tab and should say your local ip address behind your firewall..  Hopefully... :)

For Samba I went here and followed it to a t.....  Had it going in minutes..

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

-mep

---

