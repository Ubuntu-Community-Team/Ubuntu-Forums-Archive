---
title: "Frequently net is not working"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Tamil on 2006-11-16
Frequently net is not working. :mad: I have to reboot (sometimes twice) Ubuntu again to make it work. Net works fine in Windows. :confused:

---

### Post by adwait on 2006-11-16
Which ISP are you using? Its possible that your resolv.conf is getting owerwritten. Whenever your net is working, try running this command:
[code]sudo chattr +i /etc/resolv.conf[code]

Perhaps your net will start working consistently after that?

If not, how do you connect to the net?

---

### Post by Tamil on 2006-11-16
Thanks. I will post if it happens again.

---

### Post by Tamil on 2006-11-17
It happened again. :cry:

---

### Post by adwait on 2006-11-17
Alright, so lets have some more info. Which ISP are you using? How do you connect to the internet?

---

### Post by Tamil on 2006-11-18
> **adwait said:**
> Which ISP are you using? How do you connect to the internet? [BSNL](http://www.bsnl.co.in/) & through proxy.

---

### Post by adwait on 2006-11-18
BSNL, so you are using Dataone right? When the net disconnects, do the lights on the router remain on? The ADSL, Ethernet/USB lights?

Also, when the net is disconnected, can you "see" the router? ie: Can you ping the router from your computer?

---

### Post by wieman01 on 2006-11-19
What network device & chipset are you using? Have you got any kind of encryption (e.g. WPA) enabled? What router have you got?

Been through similar staff...

---

