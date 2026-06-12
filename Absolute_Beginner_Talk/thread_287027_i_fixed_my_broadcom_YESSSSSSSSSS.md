---
title: "i fixed my broadcom YESSSSSSSSSS"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by pregoeater on 2006-10-28
after weeks of trying i got my compaq 2200 with the braodcom 4603to work all i had to do was download the file in the link, and REM all the stuff in your network interfaces file. well everything BUT the first two lines...then i did a reboot and BOOM it worked. IM SO HAPPY i could cry....and i hope that this will help some other people as well. from what i understand it works with all broadcom 43xx. 

internet.[http://ubuntu.cafuego.net/pool/dapper-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu1_all.deb](http://ubuntu.cafuego.net/pool/dapper-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu1_all.deb)


Pre

---

### Post by llamakc on 2006-10-28
We'll see: I'm off to reboot.

(Fingers crossed)

---

### Post by Rackerz on 2006-10-28
> **llamakc said:**
> We'll see: I'm off to reboot.

(Fingers crossed)

Any luck?

---

### Post by llamakc on 2006-10-28
Nope. Same access point: invalid problem I've had with Edgy. I've thrown all of the iwconfig commands for rate, essid, and ap at it as I used to have to do with Dapper. None of them work. I've also tried extracting the firmware from wl_apstat.o with the same non-working results.

If ya'll get it working, congrats. As for me I am going to purchase a card that is known to work out-of-the-box.

---

### Post by pregoeater on 2006-10-28
wow sorry id did not work for you....untill now i had a card i was using because mine did not work. it was a d-link and it work without messing with it...



pre

---

### Post by CCBalla10 on 2006-10-28
I have a Broadcom 4306 14e4:4320 and I used the below link to get my wireless card to work...works like a charm...also, after you blacklist Ubuntu's native bcm43xx driver, you must reboot before continuing the tutorial...(figured this out after about 3 times of going through it) so bookmark the page...hope  this works for you!

P.S. I am running Ubuntu 6.06 dapper 

```
http://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper
```

---

