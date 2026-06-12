---
title: "wireless network problem"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by michael_xu19 on 2008-02-11
Hi, folks.
I got a problem about my wireless network connection. 
I installed Ubuntu 7.10 in my laptop (IBM T42). After installed, I found my laptop can connect with wireless network at home and succeed to log on the configuration page of Router; however, I can not browser any website site???
As the matter of fact, in the Windows, I can surf internet to any website through wireless, also I can do the exactly same thing by cable in Linux environment successfully. 
Then I modified the entire configuration in Network Manager to let it match as it in windows. In fact, I still can not link website outside. 
I have no idea where is the problem. 
Can u help me please? :confused:

---

### Post by spiderbatdad on 2008-02-11
is your home network secured? You may need a package called wpa-supplicant from synaptic.
You might also try your essid in quotes.

---

### Post by mrsteveman1 on 2008-02-11
When your system appears to be connected in linux, can you ping your router?

Also post the results of the following commands 


```
sudo iwconfig eth0/ath0/wifi0 (depending on which it is)

sudo ifconfig -a

sudo cat /etc/resolv.conf

sudo route
```

---

### Post by dca on 2008-02-11
Hmmm, his problem is obtaining an IP address from the router in his Ubuntu install especially if he's able to connect to the router config web-app...  What security is router using and if it's WEP is it using the key 1 - 4 dealie.  If so, put the key in #1...  I'm trying to remember, I had this problem like two years ago if it's the same thing...

---

### Post by jimofadel on 2008-02-11
I'm no expert, but can offer my experience -- My Ubuntu 7.10 Gnu desktop  laptop always defaults to the wrong wireless network, and I have to manually tell it (click on the little bar-graph icon) which network to use.  If I don't do this, I am unable to get to the internet, because the other wireless networks present are secure.  Also, if I remember correctly, my wireless router has a menu option to not allow connection to the internet at all, and even after  it is allowed there is a WAP key required by the router, and also my Laptop has an ADDITIONAL key or password that allows access to a "vault" or something like that where it keeps the WAP key.  I eventually did get everything set up without using any console commands, just working with the GUI.  It only works when the network manager is told to "allow roaming mode" -- I never could get the manual settings to work.

---

### Post by Michl on 2008-02-11
Check the wireless configuration/settings on your router/modem and then make
sure you've configured your network-manager appropriately, especially with
the right key/password settings.  I bet you are not logged into your network.

---

