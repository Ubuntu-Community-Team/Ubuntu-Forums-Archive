---
title: "Broadcom Wireless help"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by c0d4041292 on 2007-04-20
i have an Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) and i do not know how to get it to work

---

### Post by oilchangeguy on 2007-04-20
quote: it sayed windows XP or better so i installed ubuntu =P
do you mean said?  because sayed is not a word.
now, about the wireless issue. please go to system, admin, networking. what's listed?

---

### Post by c0d4041292 on 2007-04-20
wireless connection
wired connection
modem connection

sry, im not good at spelling hate english

---

### Post by srt4play on 2007-04-20
I'd like to make a comment on his signature also.  

:shock:  holy cow that's an insane setup for a desktop

---

### Post by oilchangeguy on 2007-04-20
does the wireless connection show as active?

---

### Post by zPacKRat on 2007-04-20
I'm using a card based on the same chipset, you need the "bcm43xx-fwcutter" installed, during installation it will extract what it needs from you wireless card (so leave it in). the one issue is that you will only get an 11MB connection.

---

### Post by c0d4041292 on 2007-04-20
mines internal, and yes its shoows as on

---

### Post by oilchangeguy on 2007-04-20
in the search box at the upper right of the page. i typed in broadcom bcm 4306, and found 74 posts on the subject. one of them should contain your answer.

---

### Post by 1501 on 2007-04-20
I have a Broadcom card too, I did the following:

go to the terminal and type  

```
sudo apt-get install bcm43xx-fwcutter
```

a screen will appear, click on yes. You'll return to the terminal then type:


```
sudo modprobe bcm43xx
```

Let me know if it worked out for you :)

---

