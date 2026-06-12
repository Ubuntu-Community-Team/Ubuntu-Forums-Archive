---
title: "wifi card in laptop.."
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by mechel on 2007-01-31
Hi, I've been using Linux for about 2 weeks now on my own computer and I'm trying to get my family into it. I have booted up our laptop with a live cd, but it wont recognize the wifi card, because the card wont turn on (there is a button on the laptop that turns the card on and the button wont work when Ubuntu is loaded). Any help would be greatly appreciated, because I really want to show my parents how good Linux is.

P.S The distro is 6.10

---

### Post by jimrz on 2007-01-31
> **mechel said:**
> Hi, I've been using Linux for about 2 weeks now on my own computer and I'm trying to get my family into it. I have booted up our laptop with a live cd, but it wont recognize the wifi card, because the card wont turn on (there is a button on the laptop that turns the card on and the button wont work when Ubuntu is loaded). Any help would be greatly appreciated, because I really want to show my parents how good Linux is.

P.S The distro is 6.10

please post specific information on your wifi card, make/model, etc...this will allow people to assit you in getting it working.

also, it is possible that while the indicator lite for your wifi button is not working the wifi itself may be. in the panel go to System to Administration to Networking and see if your card is listed.

---

### Post by pissedoffdude on 2007-01-31
Chances are you got a broadcom wireless card, open up a terminal and type in this command ```
 lspci | grep Broadcom\ Corporation
``` if you see an output similar to this ```
lspci | grep Broadcom\ Corporation
0000:02:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
``` then this howto can help with that [http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom").  If not then your gonna need to use ndiswrapper which lets you use a windows driver for your wifi card

---

