---
title: "Installation on macbook."
date: 2014-01-26
forum: Apple Hardware Users
---

### Post by Furycd001 on 2014-01-26
HI

I have a late 2009 white macbook which I am looking to install ubuntu on. This will be a full stand alone install and not a dual boot of any sort. The reason I have yet to go ahead with the install is that I have two problems.


Problem 1 -- The trackpad on my macbook is very unresponsive to my touch and it takes a bit of work to navigate from one side of the screen to the other. Is this an easy fix :?

problem 2 -- Wifi does not work out of the box but I get a warning that Broadcom drivers are available. If I connect my macbook to my wifi router via Ethernet can I just select dchp and connect that way to install the drivers :?


Thank you for taking the time to read my post. If you could at all help me it would be great to hear from you. FYI: It is ubuntu 12.04 that I am trying to install and I have the same problems with both USB and cd boot. I have also tried using 12.10 only getting the same problems...

---

### Post by martincannell503g on 2014-01-26
Q 1  :  The trackpad on my macbook is very unresponsive to my touch and it takes a bit of work to navigate from one side of the screen to the other. Is this an easy fix?  

A1  :  Yes, just select SystemSettings-->Hardware-->Mouse/Touchad and slide the accelleration slider right across.

[IMG]https://lh4.googleusercontent.com/-WeUWYLUJTJs/UuXXWGcKv-I/AAAAAAAAAH0/in3tGe_lFz4/s800/Screenshot20140125.png[/IMG]


Q :  Wifi does not work out of the box but I get a warning that Broadcom  drivers are available. If I connect my macbook to my wifi router via  Ethernet can I just select dchp and connect that way to install the  driver

 A:  See  [ https://help.ubuntu.com/community/MacBookAir]("https://help.ubuntu.com/community/MacBookAir")   about what works out of the box.  ALL ethernetwork cards works straight out from the box and installing any wifi drivers needed can e installed by following the aove instructions (depends on which MacBookAir you have).

The wifi "*[driver]"* needs firmware udates see :  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")  :  not an easy process for a novice but still, it is possiale to get working, with persistance.  Its a terminal thing, simular to macs ternminal.

---

### Post by Furycd001 on 2014-01-27
> **martincannell503g said:**
> Q 1  :  The trackpad on my macbook is very unresponsive to my touch and it takes a bit of work to navigate from one side of the screen to the other. Is this an easy fix?  

A1  :  Yes, just select SystemSettings-->Hardware-->Mouse/Touchad and slide the accelleration slider right across.

[IMG]https://lh4.googleusercontent.com/-WeUWYLUJTJs/UuXXWGcKv-I/AAAAAAAAAH0/in3tGe_lFz4/s800/Screenshot20140125.png[/IMG]


Q :  Wifi does not work out of the box but I get a warning that Broadcom  drivers are available. If I connect my macbook to my wifi router via  Ethernet can I just select dchp and connect that way to install the  driver

 A:  See  [ https://help.ubuntu.com/community/MacBookAir]("https://help.ubuntu.com/community/MacBookAir")   about what works out of the box.  ALL ethernetwork cards works straight out from the box and installing any wifi drivers needed can e installed by following the aove instructions (depends on which MacBookAir you have).

The wifi "*[driver]"* needs firmware udates see :  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("http://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")  :  not an easy process for a novice but still, it is possiale to get working, with persistance.  Its a terminal thing, simular to macs ternminal.

Thank you for your reply :-) I will try setting up the wifi & Ethernet once I go ahead and do an install. As for the trackpad I just booted from USB & tried what you suggested. My trackpad is still doing the same thing. Basically the trackpad will not recognise movements most of the time whenever I touch it. It will usually take 3 or 4 different attempts to get the pointer to move. This is a problem will all linux systems on my macbook. I have tried 3 different versions of ubuntu, Debian, crunchbang, elementary, lubuntu & xubuntu. Works perfect in my osx install. Any way to go about fixing this :? I haven't tried a USB mouse yet but will give that a try later on tonight. I'm not open to using a mouse all the time, but I would use one as a temporary fix if I had to...

Ok so I tested using a USB mouse. Pointer moves perfectly now. Just seems to be a problem with the trackpad. I can confirm that my trackpad is fully working as it works perfects when in osx. The problem only occurs whenever I boot to linux. Can anyone please tell me how I could get my trackpad working :? I would rather not have to use a USB mouse...

I have done some extensive searching into my problem & have found that creating a custom xorg.conf with trackpad preferences could solve my problem. Is this true :? If so... If I run X -configure & create an xorg.conf .What code would I put in as my trackpad settings :?

Sorry but I'm completly stumped & would really appreciate any help because I would like to get using ubuntu again...

---

