---
title: "macbook pro 4.1 - airport is active but doesn't hook to network"
date: 2010-11-15
forum: Apple Hardware Users
---

### Post by tp21 on 2010-11-15
hi,
i have macbook pro 4.1, and i just installed ubuntu 10.10 (64 bit) as dual boot. 
my problem is that airport card is activated and can identify my network but it can not hook into it, it keep asking me about password.
the airport card works perfectly under os x.
my router is Netgear MR814 v3, 802.11b.
so i am wondering if the router is not compatible any more, or if the problem is driver problem? 
thanks for any help

---

### Post by conundrumx on 2010-11-15
Is the wireless network secured?  Is Ubuntu asking you for the SSID password, or your user account's password?

---

### Post by tp21 on 2010-11-15
the network is secured with WEP 40 bit Key, and Ubuntu keeps bringing the wireless authentication window which usually comes after choosing the SSID of a network, and asks again and again about the key. 
Ubuntu even doesn't say that the key is wrong, but says encryption keys are required to access the network.
thanks

---

### Post by conundrumx on 2010-11-15
Are you entering your WEP key?

---

### Post by tp21 on 2010-11-15
yes sure, it is a 10 digits key, and i am sure it is correct. it works fine with osx. Ubuntu sees the network but can not hook into it for some reasons. 
i will try with another router and see what will happen.
thanks

---

### Post by tp21 on 2010-11-16
i just tested a new router, n router, with no success. it was also not possible to hook into completely open network.
so i guess it is the airport it self. maybe it is the firmware! 
how can i found out which firmware i have? i checked on apple site if they have airport update but they don't.

---

### Post by conundrumx on 2010-11-16
It's not hardware/firmware, it's the drivers your drivers (or lack thereof).  The Mactel PPA might be of help.  [http://ubuntuforums.org/showthread.php?t=1046568](http://ubuntuforums.org/showthread.php?t=1046568)

---

### Post by tp21 on 2010-11-16
thanks conundrumx.
strangely my problem was solved after i changed the security of my router to WEB 128 bit. which means in my case airport doesn't hook up neither if the network is open nor if it is encrypted with WEB 64 bit (10 digits key), but it will work fine if the network is encrypted with 128 bit (26 digits key). strange, isn' it? i don't know if it is a bug or a special problem in my case.
do you think i should nevertheless install mactel PPA? it says it is for Intrepid and Harry, is it also useful for Maverick?
thanks

---

