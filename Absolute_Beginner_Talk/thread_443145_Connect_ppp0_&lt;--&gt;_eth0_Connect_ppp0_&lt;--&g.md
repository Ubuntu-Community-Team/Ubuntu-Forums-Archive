---
title: "Connect: ppp0 &lt;--&gt; eth0 Connect: ppp0 &lt;--&gt; eth0"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by 7Aaron7 on 2007-05-14
HI, 
been through a ton of pages here on the forums, but still get the Firefox can't find server.

Facts:
ubuntu 7.04
ECI telecom b-focus router 270 being used as an ADSL modem
Connected with a ethernet card via cable to the router (also tried it on the motherboard ethernet port)
I have run the pppoe install process several times.
I have set the disable IPv6 in firefox to true
I have two wired connections in the nework settings window, both have checks by them.  Under DNS, I have input the ip addresses given to me by my ISP (I also tried DCHP, it also didn't work)


here are the most recent results of plog

Exit
Plugin rp-pppoe.so loaded
pppd 2.4.4 started by aaron, uid 1000
PPP session is 3590
Using interface ppp0
Connect: ppp0 <--> eth0
Remote message: Authentication failed
PAP authentication failed
Connection terminated


PLEASE HELP!!!

---

### Post by RedSquirrel on 2007-05-18
This is just off the top of my head...

Depending on your ISP, when you run 'sudo pppoeconf', sometimes you have to enter a username such as

**your_username@yourISP.com**

and not just "your_username".

---

