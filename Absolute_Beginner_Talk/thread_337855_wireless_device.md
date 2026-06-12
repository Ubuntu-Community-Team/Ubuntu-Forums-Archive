---
title: "wireless device"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by singetak on 2007-01-13
i have a problem on my dell laptop the wireless isn't recognized by Ubuntu](*,) ](*,) 

Could this be that i need a driver?
If that so How??

---

### Post by oilchangeguy on 2007-01-13
sign in under your admin id, and from system click on administration, then network administration (i didn't see network administration while logged in as user) open this and you should see 3 things listed. your nic card, etho1, your wireless card, wlan0, and maybe a modem (probably not working) the nic and wireless should show active. highlight the wireless connection click properties, and check the box to enable it. then from the 2 screen icon near the clock open this and select wlan0 from the drop down menu, and you should be on your way.

---

### Post by annda on 2007-01-13
unless you can tell us exactly what your wireless card/platform is, there's small chance somebody can help you. so i'd recommend:

step 1) try some googling for your dell model and linux wireless and take a look here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

step 2) post some specs and **maybe** (if you can) some error messages and we'll go from there.

---

### Post by mojoman on 2007-01-13
What type of card are you using? Could you post the outout from ```
ifconfig -a
```
/Mojoman

---

### Post by singetak on 2007-01-14
sorry what do you mean by admin id
cause i don't see the network administration

---

### Post by oilchangeguy on 2007-01-14
when you installed ubuntu you should have been prompted to set up at least two user accounts. the root or admin. id, and a user id. you'll have to sign in under the main id to access many functions, such as network administration.

---

### Post by mojoman on 2007-01-14
> **singetak said:**
> sorry what do you mean by admin id
cause i don't see the network administration

I'm not sure if I remember it correct but try this. In the menu, go to System -> Adminstration -> Login Window. You will be promted for your password. After that, go to the security tab. Click the box "allow local system adminstrator login". Now, this should cause some more option to show in the menu, under administration and preferences, among other thing network adminstration. 

Let me know if I remembered correct...

/Mojoman

---

