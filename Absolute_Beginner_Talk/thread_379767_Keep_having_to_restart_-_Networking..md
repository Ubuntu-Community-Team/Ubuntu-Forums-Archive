---
title: "Keep having to restart - Networking."
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-03-08
I have WiFi and it runs great, but every so often, randomly it will stop working on Ubuntu, firefox wont load anything, neither will gaim, or anything that requires internet. disabling and enabling the network wont fix this, neither will completely logging out/in. I need to reboot my entire system. Any idea why?

---

### Post by skale on 2007-03-08
do this:
sudo /etc/rc.d/network restart

Then turn on the network as you normally would (sudo ifup ethwhatever && dhclient)

Post what happens.

---

### Post by auraithx on 2007-03-09
sudo: /etc/rc.d/network: command not found

---

### Post by mozkaynak on 2007-03-09
> sudo: /etc/rc.d/network: command not found

there is no column after sudo

---

### Post by oilchangeguy on 2007-03-09
are you sure it's the computer? have you noticed what the lights on your modem are doing when this happens?

---

### Post by auraithx on 2007-03-10
^ Yes, my internet still works fine on my other computers that are connecting to the WiFi

---

### Post by fasoulas on 2007-03-10
Maybe your pc is far from the WIFi access-point and the signal is low...Have u checked that

---

### Post by auraithx on 2007-03-10
The signal is fine, it's nothing external.

---

### Post by miggols99 on 2007-03-10
I have had the exact same problem. Very weird.

---

