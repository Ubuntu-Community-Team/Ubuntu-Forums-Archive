---
title: "Wireless internet access problems"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by malayka on 2007-08-18
Hi All,

I've just installed Ubuntu 6.06.1 for the first time but am having trouble accessing the internet. I have a 3com wireless access point which I can see in networking, but I am unable to pick up a dhcp address. I can add a static address but still can't ping the gateway. I have authenticated access using a hexidecimal key and the system confirms that it is enabled. Please could someone give me some advice on resolving the problem. Any help appreciated.

Regards

Chris Gonzalez.

---

### Post by nitro_n2o on 2007-08-18
what is the output of **iwconfig** ?
what is inside **/etc/network/interfaces** ?
is your machine a laptop or a desktop?

---

### Post by malayka on 2007-08-18
Hi Nitro_n2o

I have a desktop pc dell sx270, with a 3com wireless 802.11g office connect usb dongle.
I have attached the interfaces config and some config info from the terminal command.
I can see the 3 com wireless AP in the drop down menu and it allows me to choose it. I have also disabled the Ethernet card, however I can't ping the router. I have even set a static ip address but this hasn't helped. When I run ifconfig it doesn't come back with an ip address unless I ahve set a static one and I am unable to ping the router.
Could it be anything to do with the fact that the wireless card is a 3 com usb dongle?
Any help would be much appreciated as I've run out of ideas.

Cheers 

Chris

---

### Post by malayka on 2007-08-23
Hi Nitro_n2o

Just wondering if you managed to look at the config files I attached to my last post. I still don't seem to be able to pick up an IP address even though I can see the 3 com access point. I have tried the access point with and without encryption but this doesn't seem to resolve the problem either.

Any help would be appreciated.

Regards

Chris

---

### Post by malayka on 2007-09-10
Hi,

Just so you know I managed to resolve the problem by reseting my AP completely and re configuring it from scratch without WEP encryption. It is working fine now.......just hope noone is stealing my bandwith!

chris

---

