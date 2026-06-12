---
title: "gutsy server edition automatic network config fails on install?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by vamp4life666 on 2008-01-19
I am installing gutsy server edition and it is unable to automatically configure the network connection. 
The box is an older dell, 1.6ghz p4, 768mb...
The network port is fine, in that, if I plug in my laptop it easily pulls an ip address.

I can continue install without any other problems, but I can't even run sudo apt-get updates or upgrades.

I just realized i have another question...

The install disc I have that coincides with the above problem doesn't give me the option to chose how I would like to set up the server... (web server, samba file server,etc.), is this a result of the first problem?

Any ideas or suggestions would be great, thanks, MG.

---

### Post by jeffus_il on 2008-01-19
If by automatic network config you mean the NetworkManager application, it is not recommended for a server, right click on the icon and do a manual configuration.

---

### Post by vamp4life666 on 2008-01-19
icon....?
I'm in the bash shell, so i really don't know what icon your reffering to...

To be more specific I am refering to the inital install of Gutsy onto the machine, whne I refer to automaticly configuring with the DHCP. 

Sorry if I missworded that orginally.

MG

---

### Post by vamp4life666 on 2008-01-19
it was a bad disc.
I made a new one and things went much smmother.
Samba, webmin, updates, upgrades all cam with no problem.


no i just to get webmin configured so i can acctully connect my xp machines to the samba server, wish me luck

---

