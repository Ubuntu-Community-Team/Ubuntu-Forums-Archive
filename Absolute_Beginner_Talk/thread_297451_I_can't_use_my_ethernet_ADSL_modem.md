---
title: "I can't use my ethernet ADSL modem"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Iray on 2006-11-11
Hi everyone,
I have a D-Link 302T ADSL modem, connected via ethernet to my PC.
I want to use the modem to go in internet with Ubuntu LiveCD 6.10.
I use "sudo pppoeconf" to configure my modem and it's all ok, but then i cannot navigate the net.
Doing "plog" few seconds after pppoeconf it seems to be ok, but i cannot navigate, then if i try newly plog it says "modem hangup".
I've also tried to use "pon dsl-provider" and "poff dsl-provider" to turn on and off the connection but this doesn't help.
The modem is ok and the ADSL LED is on.

Reading from this forum ethernet modems are so easy to set-up... but I've found this problem with 5 different LiveCD distros beyond Ubuntu!

Is it possible that the modem can't be configured well only because I use a LiveCD? If I'll install Ubuntu is there a higher probability to use internet?

Please HELP!!  ](*,)

---

### Post by Iray on 2006-11-11
I've tried now to do another try:
I've used the same modem but a different PC (a notebook this time).
The problem is exactly the same, so it's not a problem of my pc or of the network card.

---

### Post by Iray on 2006-11-12
Maybe I need a router? I can buy it if it's necessary...
But I have read that also modems connected on ethernet could be used without problems in every linux distributions...

---

### Post by Iray on 2006-11-13
YEEEES!!!
Now It's all ok!
I have solved all converting my modem 302T into a router 502T, following the simple steps i found on this [site]("http://www.dlinkpedia.net/index.php").
I'm writing from ubuntu LiveCD now!! I'm really really happy and in one or two days I will install Ubuntu!!

Thanks everyone, also if I haven't had replyes I hope that my thread will help someone else with this modem, with the same problem. :rolleyes:

---

### Post by rfruth on 2006-11-13
Glad its working, and for those not versed in Italian here is the English version from the wiki [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by Iray on 2006-11-14
Sorry but your link is very different from mine.

I have tried to use *pppoeconf*but without success with that modem.
I found that other people has the same problem with that modem and one solution is to change its firmware with the d-link 502T router's firmware.
With the program I used it's very simple but I know only the italian link. If someone has problems with the italian site, he can contact me here!

Now I'm very ready to become a real linux user!! :-({|=

---

