---
title: "Enterprise Wlan - Ubiquiti UniFi - connection issues"
date: 2014-03-07
forum: Any Other OS
---

### Post by rick16 on 2014-03-07
Hi Community!


Our company has several issues with the Ubiquiti UniFi enterprise W-Lan solution.
We´re using these acess points for our whole building(2 floors – 3000 m2).  Every strategically postion is equipped with a UniFi 3.1.4(upgraded from 2.x.x) access point.
We have  up to 40 active users/access point.

For example, if a user who is connected with AP1 walks down the floor and reaches the range of AP1 the notebooks connects with a different AP like it should but it wont choose the „best“ one.


Same issue for workplace employees, you can sit in front of your desk and the client connects to different AP´s without a reason, this results in connection errors and broken voice calls.


Any ideas?


Best Rick


Additional Information:


- We tested several firmware versions without effect
- We set the transmit power of each AP to maximum
- we have unstable pings to each AP
- sometimes there is a connection but no packets were transmitted
- we tested different channels to prevent signal overlaying

---

### Post by Toz on 2014-03-07
Hello rick16 and welcome to the forums.

Since your question doesn't seem to have anything to do with Ubuntu, I've moved it to **Other OS/Distro Support**.

---

### Post by mccalleyt on 2014-03-11
Well First how many access point are you using and how far apart are they from each other and are the APs having overlapping channels? Second are you using a VLAN that is exclusively used for voice/VOIP only? It is a must that you have a VLAN that is only for your phones. Also as far as connection issues if you don't have your APs spaced far enough apart and they have overlapping channels you will have "dead" zones. Typically any routers that are close to each other need to be on channel 1,6, or 11 for 2.4Ghz 802.11.


PS. Also are your APs working in autonomous mode or are they being managed. If they are not in managed mode that could also be a cause of your computer not connecting to the best connection.

---

