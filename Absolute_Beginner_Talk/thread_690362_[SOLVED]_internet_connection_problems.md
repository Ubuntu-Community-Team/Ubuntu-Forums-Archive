---
title: "[SOLVED] internet connection problems"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by chuck88 on 2008-02-07
alright, here's my set up. I have a windows desktop which conects to a cable modem: Motorola SURFboard® Cable Modem SB4200. Then an eithernet cord to the cpu. When I unplug the eithernet cord and plug it into my ubuntu laptop(dell inspiron 2500), I can not get onto the internet. I don't know if it's the kind of modem, or if I need to do something on the laptop to make it work.

thank you kindly

chuck
__________________

---

### Post by ichbinesderelch on 2008-02-07
i assume you need to set the modems ip adresse as your default gateway on your laptop.. this should do the trick!

---

### Post by mkwerner on 2008-02-07
Your cable modem 'keys' itself to the mac address of your ethernet adapter - if you have it plugged into your desktop, then move the cable to your laptop, it won't work because of this feature.

If you want to switch from one to the other (without a router), you need to power down your cable modem for 60sec, move the ethernet cable to the other device, then power the modem back up.

HTH,
M.

---

### Post by chuck88 on 2008-02-08
hey thanks! I just unplugged it, let it sit and plugged it back in with the ethernet connected to my laptop and it works! I am replying from the laptop!

---

### Post by mkwerner on 2008-02-08
Excellent - glad you got it running!  That issue used to drive me nuts until I learned about the cable modem keying itself to the NIC mac address.

Regards,
M.

---

