---
title: "[moved to another forum ]iwlwifi drops connections?"
date: 2013-05-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by ulugeyik on 2013-05-11
Hello,

I am using a ASUS Zenbook UX31A  with Ubuntu 12.10 installed. I have no wireless problems at work or at home but I have been at a hospital with a wireless connection (WPA & WPA2 Personal) for the last week and I lose connection every few minutes and I have to disconnect/reconnect multiple times. First, I was blaming the hospital itself but then I tried my other Asus netbook (12.04 installed) which does not have this problem. Neither do any of the android tablets I use.

The only  thing I see in the logs is this transition:
[ 1800.409328] iwlwifi 0000:02:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1800.409387] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]

Issuing  'sudo iwconfig wlan0 power off' seemed to have helped once but it is not persistent. It lasted a bit longer may be accidentally.

A lot of discussions on internet has suggested that I do this:
sudo rmmod iwldvm
sudo rmmod iwlwifi
sudo modprobe iwlwifi 11n_disable=1 swcrypto=1

But that is also not useful. "11n_disable=1" allowed me to have significantly higher upload/download rates at home.


I do not know how to diagnose this problem and it is bugging me a lot since I am trying to work during a lenghy hospital stay. Any advice, pointers is greatly appreciated.

thanks,

---

