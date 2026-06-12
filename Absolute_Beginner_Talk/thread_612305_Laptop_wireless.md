---
title: "Laptop wireless ?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by mx_racer84 on 2007-11-13
I have an hp pavillion dv5000 with a built in wireless card and im wondering how to get the wireless working the system doesnt seem to detect the card and im am using unbuntu 7.10?

---

### Post by rudeboyskunk on 2007-11-13
Is it the dv5000ea or the dv5000 CTO?

---

### Post by mx_racer84 on 2007-11-13
how do u tell the diffrence ?

---

### Post by rudeboyskunk on 2007-11-13
I have no idea, unless it is printed somewhere on the computer itself.  The reason I ask is because I tried to look up the specs of your computer on HP's website to see what kind of wireless card it is, and there were those two options for the model number you gave.

Once you find out what kind of wireless card it is, post that.  You can also try a google search with the name of your wireless card and "linux support" to see if it's been solved elsewhere.

---

### Post by mx_racer84 on 2007-11-13
Its the dv5000z not sure of the wireless card yet still looking

---

### Post by mx_racer84 on 2007-11-13
this is the name of the wireless

BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

any idea where to start in getting this thing working ?

---

### Post by rudeboyskunk on 2007-11-13
Ok, that's the problem.  BCM means Broadcom.  Broadcom does not release info about their chipsets so it is very difficult (and sometimes illegal) to make a driver for the hardware in Linux.

However, [this thread]("http://ubuntuforums.org/showthread.php?t=190177") has a howto for you.

---

### Post by buccaneere on 2007-11-13
> **rudeboyskunk said:**
> Ok, that's the problem.  BCM means Broadcom.  Broadcom does not release info about their chipsets so it is very difficult (and sometimes **[COLOR="Red"]illegal[/COLOR]**) to make a driver for the hardware in Linux.

However, [this thread]("http://ubuntuforums.org/showthread.php?t=190177") has a howto for you.

Illegal for *[COLOR="red"]non[/COLOR]*-commercial application???

Can't be...

---

### Post by rudeboyskunk on 2007-11-13
> **buccaneere said:**
> Illegal for *[COLOR="red"]non[/COLOR]*-commercial application???

Can't be...

Perhaps I was a bit too hasty. . . ;)  But even if it's legal, it's still mean of them to not release open-source drivers like HP.

---

### Post by mx_racer84 on 2007-11-14
that how to didnt seem to work 

where to start next ?

---

