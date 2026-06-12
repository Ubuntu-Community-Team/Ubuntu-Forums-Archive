---
title: "I really need help getting started"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by sloshman9 on 2007-02-11
Okay, I just today got the newest version of ubuntu, this is my first time ever using ubuntu. I got it all installed and everything, but when I attempt to go to sites on firefox it says the site cannot be found (even google). when i attempt to connect to gaim it says host cannot be found.. i assume this is because of internet connection. I have a wireless netgear wg121 box. When i look up on google how to fix this all i see is stuff about commands, i don't understand how to use commands (like on windows you'd go to start -> run -> cmd) but idk on ubuntu

can somebody PLEASE Help me. sorry if this is in the wrong forum.

P.S i am typing on my moms laptop. the computer with ubuntu is on, right in front of me

thanks in advance for all your help.

---

### Post by meng on 2007-02-11
Do you know if your wireless card is recognized by Ubuntu to start with? (Look in System > Admin > Networking) Has it been configured yet? Is your wireless network WEP or WPA encrypted?

---

### Post by kidders on 2007-02-11
Hi there and welcome,

To enter sequences of commands, the handiest thing to do is open a terminal application. Having said that, please, *please* don't type anything you don't understand ... particularly if you have to "sudo" it.

---

### Post by sloshman9 on 2007-02-11
i do not believe my netgear configured, how can I configure it??

---

### Post by meng on 2007-02-11
Look in System > Admin > Networking

---

### Post by sloshman9 on 2007-02-11
under networking I see

Wireless Connection
The interface eth2 is active

Ethernet Connection
THe interface eth0 is active

Modern Connection
the interface ppp0 is not configured

---

### Post by meng on 2007-02-11
Great. Are you using the wireless connection to connect to the internet? If so, check that the default device/interface is eth2 (that's an option under System > Admin > Networking).

---

### Post by sloshman9 on 2007-02-11
I am attempting to get my Netgear 54 mbps wireless USB 2.0 adapter 

(Netgear wg121)

But im not getting anywhere when I open firefox I see something about ubuntu and I go to say google.com and get firefox cant find server at [www.google.com](www.google.com)

another problem i am having is everything is huge, this is because of screen resolution, but i cannot seem to change it but i am worried about that after I get internet connection up.

---

### Post by meng on 2007-02-11
Can you use System > Admin > Networking to unselect the ethernet connection, thereby forcing it to use the wireless connection? Then close down firefox and restart it and try again.

---

### Post by sloshman9 on 2007-02-11
The only active connection is "Wireless Connection (eth2)" and it still won't connect to the internet.

---

### Post by meng on 2007-02-11
Ok then open a terminal and type:
sudo iwconfig eth2
and check that the ESSID and encryption key are correct.

then type
sudo dhclient eth2

---

### Post by sloshman9 on 2007-02-11
when I do the first command i see ESSID: off/any (with a bunch of other things)

---

### Post by meng on 2007-02-11
Use the command:
sudo iwconfig eth2 essid **NameofNetworkSSID**

to set the ESSID

---

### Post by sloshman9 on 2007-02-11
How do I know what my network SSID is?

---

### Post by meng on 2007-02-11
I can't help you with that. If it's a Netgear router, I suppose it could be "Netgear". What about the encryption - is that correct, you never answered my initial question? Unfortunately I don't have time to stick around and get information in single drips like this. Good luck with everything.

---

### Post by sloshman9 on 2007-02-11
thought i did answer that, but appearantly not. I don't know how it's encrypted.

---

### Post by Maestro23 on 2007-02-11
> **sloshman9 said:**
> How do I know what my network SSID is?

Don't know your particular hardware,(jumpig in on tale end of your thread), but here is an FYI thread on SSID and wireless routers. Quick google:

[http://compnetworking.about.com/cs/wirelessproducts/qt/changessid.htm](http://compnetworking.about.com/cs/wirelessproducts/qt/changessid.htm)

Might lead you in a right direction.

---

