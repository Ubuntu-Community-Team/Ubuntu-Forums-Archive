---
title: "Help with wireless card"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by TekmonX on 2008-02-04
Hey um, does anyone here know how to use a wireless card on ubuntu, because I'm having trouble getting it online and I really need to update the system and important software.

---

### Post by Blutack on 2008-02-04
Yes, but we need to know what the wireless card is first please.
Could you plug it in, type in 
> lspci
and if it isn't there
> lsusb
and then post the bit that looks like it matches the card.

---

### Post by jan quark on 2008-02-04
what card are you using?

please post the result of the following terminal commands

```
lspci
```

```
lshw -C network
```

---

### Post by TekmonX on 2008-02-04
Broadcom corporation bcm4318 [airforce one 54g] 802 Is the type of wirless card

---

### Post by Blutack on 2008-02-04
Hmm, I used to have one of those nasty things.
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)
Would be my method of dealing with it.

---

### Post by jan quark on 2008-02-04
either this /native driver

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d_%28Native_Driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d_%28Native_Driver%29?highlight=%28WifiDocs%2FDevice%29)

or that  /ndiswrapper windows drivers emulated to linux

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318_%5bAirForce_One_54g%5d?highlight=%28WifiDocs%2FDevice%29)

---

### Post by Blutack on 2008-02-04
Jan, the native driver is not very stable and doesn't like WPA.  Much safer with the ndiswrapper way, I posted someone's very nice howto for his/her card and ndiswrapper.

---

### Post by TekmonX on 2008-02-04
I looked at it and when it prompts me for the password, I can't input it

---

### Post by Blutack on 2008-02-04
By default linux doesn't echo your password.  That means when you type it in you don't get any stars or dots.  It is a security measure to prevent people knowing how long your password is.  Just type it in and hit enter.

---

### Post by TekmonX on 2008-02-04
> **Blutack said:**
> By default linux doesn't echo your password.  That means when you type it in you don't get any stars or dots.  It is a security measure to prevent people knowing how long your password is.  Just type it in and hit enter.

thanks :)

---

### Post by Blutack on 2008-02-04
No worries, that took me about 30 minutes to figure out back 5 or 6 years ago when I tried to install ndiswrapper on Mandriva 9...

---

