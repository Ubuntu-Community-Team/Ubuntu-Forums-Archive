---
title: "Total Noob hp dv8000 3945abg wireless"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by ndworecki on 2007-01-10
Hey guys i need complete help im pretty good with windows but ive always wanted ubuntu, I have installed ubuntu 6.10 but i cant get wireless i dont know what to start with i downloaded the driver files and the 80211 files but the install info doesnt help. Could someone PLEASE give me a walkthrough?

Hp dv8000 3945abg wireless card (internal)


Thanx in advance

                    -Nathaniel

---

### Post by Bachstelze on 2007-01-10
Firstly, you most certainly won't need to install the drivers yourself. Open up a terminal, run

```
sudo iwconfig
```

and copy/paste what you get.

---

### Post by ndworecki on 2007-01-10
ok i did that eth1 has my wireless but what do i do now?

---

### Post by Bachstelze on 2007-01-10
You can configure it with :

```
sudo iwconfig eth1 essid YOUR_ESSID key YOUR_WEP_KEY
```

then, if your network uses DHCP, you can just do

```
sudo dhclient eth1
```

voilà :) I can't tell you how to configure it in the GUI since I haven't done that in GNOME.

---

### Post by ndworecki on 2007-01-10
thanx but its saying

Error for wireless request "Set Encode" (8B2A) :
    invalid argument "password_here".


i use a wpa key

---

### Post by r4ik on 2007-01-10
Please read,

[http://www.ubuntuforums.org/showthread.php?t=334553](http://www.ubuntuforums.org/showthread.php?t=334553)

Good luck.

---

### Post by ndworecki on 2007-01-10
thanx im gonna give this a try

---

