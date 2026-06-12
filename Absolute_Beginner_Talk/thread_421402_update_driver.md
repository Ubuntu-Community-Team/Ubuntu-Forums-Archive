---
title: "update driver"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by fisher_mos on 2007-04-24
Hi
I installed today the ubuntu os
It dosn't recocnise my PCI lan card , I have a  cd  with drives for this card.
 How can I update the driver ?

---

### Post by mikeyphi on 2007-04-24
What Lan card is that?
Is it recognized under System - Preferences - Hardware Information?
Does your CD have Linux drivers?

---

### Post by fisher_mos on 2007-04-24
Silan SC92031  PCI Fast Ethernet Adapter
I have a CD with linux drivers , but i don't know how to install the driver
And it is **not**  recognized under System - Preferences - Hardware Information

---

### Post by Bachstelze on 2007-04-24
Does it appear when you do this ?

```
sudo ifconfig -a
```

---

### Post by fisher_mos on 2007-04-24
where I have type "sudo ifconfig -a" ?

---

### Post by Bachstelze on 2007-04-24
[Where's the terminal ?](http://psychocats.net/ubuntu/terminal)

---

### Post by fisher_mos on 2007-04-24
When I typed : sudo ifconfig -a
it wrote me:
LINK ENCAP: LOCA; LOOPBACK
INTER ADDR: 127.0.0.1  MASK 255.0.0.0
INTER 6ADDR: : :1/128 SCOPE HOST
UP LOOPBACK RUNNING MTU:16436 MRTRIC 1
RX..... (0) FOR ALL OPTION

---

### Post by mikeyphi on 2007-04-24
You might find some answers here:  [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

