---
title: "VPN Connection Help"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by BeingThere on 2007-01-16
Hello everybody!

First of all, I start recently to work with Ubuntu, my interest for computers was declining during the last two years, but now, I feel really appassionate again because this system makes you feel sooo good! Thank you all!

I need to setup a VPN Connection between and XP Office machine and my Linux Desktop Dapper Drake...

Absolute Beginner, first terms to complete, links to HowTo, Wiki...

Thanks a lot to everybody!

Being there...for a while.

---

### Post by Ecthelion on 2007-01-16
To set up a vpn connection:

1. Install vpnc
```
sudo apt-get vpnc
```
(in terminal)

2. Make a file /etc/vpnc.conf
> sudo nano /etc/vpnc.conf
With this content:
Interface name vpnlink
IPSec gateway  #1
IPSec ID #2
IPSec secret #3
Xauth username   #4
Xauth password   #5

#1: enter here the ipsec gateway
#2 idem for ipsec ID
#3: idem for the IPSec secret
#4: enter here your username
#5: enter here your pasword.
Only use the last line if you are confortable with the fact that anyone who can acces your pc manually can read it by opening this file.
If you don't use "Xauth password" then you will be promted to enter it each time you connect

3. Start vpn: sudo vpnc-connect
4. Stop vpn: sudo vpnc-disconnect

In fact, if you don't make the vpnc.conf file you will be prompted each time to enter all that data

---

### Post by Blippe on 2007-01-17
> **Ecthelion said:**
> To set up a vpn connection:

1. Install vpnc


So, how do i install and setup a vpn-server?

---

### Post by Ecthelion on 2007-01-18
> So, how do i install and setup a vpn-server?
Well I've never done that so I don't know.
Searching "vpnserver" on the wiki gave m this link:

[https://help.ubuntu.com/community/VPNServer](https://help.ubuntu.com/community/VPNServer)

Maybe it helps :-)

Also, searching the forum for "vpn server" gave me these

[http://ubuntuforums.org/showthread.php?t=245581&highlight=vpn+server](http://ubuntuforums.org/showthread.php?t=245581&highlight=vpn+server)
[http://www.ubuntuforums.org/showthread.php?t=239219&highlight=openvpn](http://www.ubuntuforums.org/showthread.php?t=239219&highlight=openvpn)

---

