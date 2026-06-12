---
title: "How to make ADSL work?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Sterbik on 2007-06-10
I have an ADSL (USB) modem -SAGEM F@ST 800/840. The installation manual says that it is compatible with Linux, but as i know Ubuntu it is not just a "click & run" like windows. How can i install it and surf on the internet?

---

### Post by meborc on 2007-06-10
do you use login and password for your adsl? if so then read this [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

if you should have automatic dhcp connection, then post your "ifconfig" output and we take it from there :)

---

### Post by mudguts on 2007-06-10
It should be like most ADSL modems where you enter the designated URL into the browser and set all of the PPPoE or whatever settings you are using in there.  
i.e. 192.168.123.254
log into the modem, enter your username and password and whatever settings.

hopefully that should work.

---

### Post by Eric_Jardas on 2007-06-10
Open terminal and run:
```
sudo pppoeconf
```

---

