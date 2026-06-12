---
title: "Broadcomm 812.11n and my asus 1015PED"
date: 2012-08-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Cilon on 2012-08-19
[FONT=&quot] Hello[/FONT]
  [FONT=&quot]I’m novice with Ubuntu and I have a problem with my ASUS EeePC 1015PED Netbook.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]When I run Ubuntu-like distributions like backtrack, wifislax, wifiway, the wifi controller seem not work at all. I am not even able to find out (airmon-ng) card’s chipset.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]The wifi controller is a Broadcomm 812.11n.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]I like you to tell me what kind of problem I have, whether it’s a driver one, if Ubuntu  supports this hardware or not, and of course the most important: how to solve it.[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Thank you[/FONT]

---

### Post by Bucky Ball on 2012-08-19
Broadcom cards are generally well supported. Please provide the output of this from a terminal:

```
sudo lshw -C network
```

Have you plugged in an ethernet cable, gotten updates, checked 'Additional Drivers'?

---

### Post by wildmanne39 on 2012-08-19
Hi Cilon please read forum code of code.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
Thanks

---

### Post by Cilon on 2012-08-29
> **Bucky Ball said:**
> Broadcom cards are generally well supported. Please provide the output of this from a terminal:

```
sudo lshw -C network
```Have you plugged in an ethernet cable, gotten updates, checked 'Additional Drivers'?

sudo doesn't wok on Wifiway 3.4 , Wifislax, Backtrack 5R2??
My card is   BCM4313 14e4:4727 rev 01

---

