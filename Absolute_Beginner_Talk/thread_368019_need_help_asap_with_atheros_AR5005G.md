---
title: "need help asap with atheros AR5005G"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by piratedninja06 on 2007-02-22
im a complete noob when it comes to linux  so please try to break everything down for me

im installing (running live for right now) ubuntu 6.10  on my acer aspire 5102wlmi laptop

can someone please tell me exactly what i need to do to be able to connect to my wireless network?

im gona install ubuntu  if i can get the wifi card to work   so i really need to know how to make it connect

---

### Post by aktiwers on 2007-02-22
What wireless card is in it?

If you type this in terminal:
```

 lspci | grep Broadcom\ Corporation
```and it shows up as something like this:
> lspci | grep Broadcom\ Corporation
0000:02:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Its shouldnt be hard to get working.
But what is the name of your card?

---

### Post by piratedninja06 on 2007-02-22
atheros AR5005G  is the card
hope that helps

if not leme know and i'll switch over to ubuntu again for a few min and copy all that info down

---

### Post by aktiwers on 2007-02-22
I think following this howto will do it:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

Dont think its a lot of info..  just copy/paste the commands into the terminal.
Thats all!

But check the command above, it should output something with Broadcom Corporation.

---

