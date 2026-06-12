---
title: "Network not working"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2008-02-08
I am using gutsy on HP business Series 6720s and the network is not working.
i am try to connect it using Ethernet. eth0 is up, but it doesn't detect when i plugin a cable or plug it out. even tried disabling wireless networking but no use.
i manual config, i tried using static and dynamic,  in case of dynamic i see two interface, eth0 has no ip, while a new interface called eth0:avh comes with a dynamic ip from dhcp. what do i do?

---

### Post by zvacet on 2008-02-08
If you use wired connection then go to the network manager>manual config>select your modem(don´t chek it,just click on it)>properties>select your type of connection(dhcp or static)>close>DNS tab>you will see one address there and if you don´t use router delete it and put your nameservers there>close>general tab>chek your modem>you should see window with **changing network interfaces** message.When it stops go to the terminal and type 

```
pppoeconf
```

---

### Post by shoaibi on 2008-02-08
i did atleaqst this much:
> 
If you use wired connection then go to the network manager>manual config>select your modem(don´t chek it,just click on it)>properties>select your type of connection(dhcp or static)>close>DNS tab>you will see one address there and if you don´t use router delete it and put your nameservers there>close>general tab>chek your modem>you should see window with changing network interfaces message.


and it was all sucessfull, any method to check if there is a problem with the eth0?

---

### Post by zvacet on 2008-02-08
In programs>accessories>terminal run

```
pppoeconf
```

take all defaults and you have to type your username and password there.After that if all goes well you will have your internet connection working.

---

### Post by shoaibi on 2008-02-08
i tried pppoeconf
and i get an error message like "
Sorry, two interface were detected but none of them was idenified with access concentrator. please verify that you have cable pluggedin...."

while i had my cable plugged in.

Has anyone else tried to install Ubuntu gutsy on HP Bussiness Series 6720S

---

### Post by BLTicklemonster on 2008-02-08
Try the link in my sig. I've used ubuntu for over 2 years, and never could get my box from an XP machine til recently when I found that site, now my networking works fine.

---

### Post by shoaibi on 2008-02-08
my problem isnt networking with XP, my problem is that my machine doesnt even get ip from dhcp, and if i assign static, it doesnt show up anything, just like as if it wasnt connected to LAN, cant even ping local servers...

---

