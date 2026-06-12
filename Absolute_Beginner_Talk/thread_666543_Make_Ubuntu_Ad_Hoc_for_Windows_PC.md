---
title: "Make Ubuntu Ad Hoc for Windows PC?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2008-01-13
I am not very familiar with networking, but

I did this,

> Creating an ad hoc network

CLick on the tray icon and select "Create a new network", now enter the name (ssid) you want to use and select an encryption method. Click ok and the ad hoc network will be created. If no other network users are found within approx 30 secs, Network Manager will search for other networks. This means you may have to make multiple attempts to connect at first. 

and the windows lappy with wfi did not see my newly created Ad Hoc network...

whats next? 

Just trying this for fun.

sv

---

### Post by edm1 on 2008-01-13
I'm trying to do the same in order to share my internet connection without a wireless router. I'm part way there. I can set up an ad-hoc network but havent managed to bridge the connection between eth0 and eth1. To get the network working do

```
sudo ifconfig eth1 up

sudo iwconfig eth1 essid NETWORK_NAME channel 11 key off mode ad-hoc
```

Where eth1 is your wireless interface. To get encryption just replace 'off' with an 8 digit code.

Read more about it by typing

```
man iwconfig
```

---

