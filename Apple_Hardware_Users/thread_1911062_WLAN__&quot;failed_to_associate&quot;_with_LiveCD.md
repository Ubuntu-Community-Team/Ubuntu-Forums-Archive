---
title: "WLAN  &quot;failed to associate&quot; with LiveCD"
date: 2012-01-18
forum: Apple Hardware Users
---

### Post by klunz on 2012-01-18
Hello Everyone,

First of all, sorry for the length of my post, but i figured it is better to be detailed then to keep everyone guessing.

***PROLOGUE***
We recently moved to a new place, got a new internet access and a new wireless router.
My wife and I both have the same Macbooks, which are from late 2007, the model number is 3,1. They both run OSX 10.5.8 Leopard.

We both didnt have any problems so far with accessing Wireless Networks, no matter the security or other settings.
However,  with our new router (an "Alice IAD WLAN 4421), we both get frequent  drops. Especially if the network-interface is disabled and then  re-enabled (via sleep mode or manually), the Network-Interface has  problems reconnecting or sometimes even finding the Network again.
****************

As  Apple apparently has a history of problems with Airport and failing  connections, I thought that maybe it is a OS related issue. 
Therefore I booted my wives laptop with the newest 11.10 Ubuntu Live-CD.
I  was asked if I wanted to activate the proprietary Broadcom-Drivers for  the WLAN-chip, which I did. After that the network was found, I could  connect to it and the macbook stayed online without any problems.

When  I closed it, it went into suspend mode (I suppose), and when I reopened  it the network was found, but the macbook could no longer connect to  it.
/var/log/syslog told me the mac-address of the router and then 
```
failed to associate
```My  question is: does it make sense to install Ubuntu on the macbook  (thereby of course deleting everything that is on it) in order to play  around with some configuration or alternative drivers or can I do the  same things with a Live-System?
What else could I try within Ubuntu to get the WLAN to run properly?

Am  I correct to assume that, if I dont get this to work using Ubuntu, I  will probably have to buy another router and see if it plays nicer with  the Macbook? I have given up getting it to work in OSX, after trying for  about a week now. 
Is this a real possibility, the Broadcom-Chip not getting along with the router, but working properly with another one?

The  last option would be to assume that the Macbooks are both slowly  failing because of age, bad chip-firmware or something else, which in my  opinion is not so realistic as we both didnt have problems before, but  have them now....

I'm sorry if the last couple of questions are  more or less unrelated to Ubuntu itself, its just such a complex problem  that everything has to be questioned.

Thanks a lot in advance for your help

Greetings
Tobi


************ EDIT *************
I decided to install Ubuntu on the machine, which, at least as far as I can tell did not make any difference in comparison to the live system.
Of course there are more things one can do when Ubuntu is installed, but the drivers are still the same drivers.

It turned out that it was partly an OS issue (Apples Airport System is a little shaky, at least in 10.5), but the main reason for the dropped connections was definetly the absolutly crappy router given to us by the provider.
After attaching a Fritz!Box, all connection issues were gone.

---

