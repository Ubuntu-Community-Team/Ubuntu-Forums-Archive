---
title: "Trouble with wlan"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by jonttix on 2007-06-26
I have a Acer 5024WLMi Laptop with integrated wlan, in my network settings I can find my wlan card but I cant get it to work. I am running Ubuntu 7.04 I have tried all the HowTOs that I have found. My iwconfig loks like this:

lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:"" Nickname:"Broadcom 4318"
Mode:Managed Access Point: Invalid
RTS thr:off Fragment thr:off
Encryption key:off
Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Any suggestion how I should do next?

---

### Post by JRR883 on 2007-06-26
This tutorial is about a year old, but it should work nonetheless.

[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

---

### Post by jonttix on 2007-06-28
I have tried this but it doesnt work! The "echo ndiswrapper >> /etc/modules" is not working, I havent got such directory! Any suggestion?

---

### Post by aeiah on 2007-06-28
> **jonttix said:**
> I have tried this but it doesnt work! The "echo ndiswrapper >> /etc/modules" is not working, I havent got such directory! Any suggestion?

you could try creating the modules folder i guess

```
sudo mkdir /etc/modules
```

you could try following this howto, since its specifically for your laptop: [http://ubuntuforums.org/showthread.php?t=145701](http://ubuntuforums.org/showthread.php?t=145701)

---

