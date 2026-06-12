---
title: "logitech web cam help"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by ljpm on 2006-12-14
Hi All,

I just installed gyachi on Dapper. I would like to use a logitech cam (its an old one and not sure what model). I plugged in the cam and started gyachi and then Actions/Start Web Cam. The window starts up but there is not image (just grey screen).

Do I need to install anything for the web cam, and if so, what and how?

Any help appreciated.

Thank,
Jim

---

### Post by loell on 2006-12-14
you can do 

```
lsusb
```

and paste the output here, to see the cam model.

---

### Post by charles.g.moore on 2006-12-14
I happened across this post and thought I would jump in heres my lsusb

charles@charles-laptop:~$ lsusb
Bus 005 Device 003: ID 0c45:62c0 Microdia
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 003: ID 04d9:048e Holtek Semiconductor, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard
Bus 003 Device 001: ID 0000:0000

Its a new laptop HP with a built in 1.3mp webcam, I dont think that ubuntu is even seeing it...

---

### Post by ljpm on 2006-12-14
Thanks for the fast reply.


Bus 003 Device 003: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 001: ID 0000:0000

---

### Post by loell on 2006-12-14
> I happened across this post and thought I would jump in heres my lsusb

charles@charles-laptop:~$ lsusb
Bus 005 Device 003: ID 0c45:62c0 Microdia
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 003: ID 04d9:048e Holtek Semiconductor, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard
Bus 003 Device 001: ID 0000:0000

Its a new laptop HP with a built in 1.3mp webcam, I dont think that ubuntu is even seeing it...


ubuntu should detect your webcam , have you tried any webcam app?

Sonix 	6 	0x0c45 	0x62c0 	Sonix ?? 	Microdia 	sn9c211 	  	Yes 	yuyv 	linux-UVC 	*****

you can also follow this instructions

[http://dollarunderscore.wordpress.com/2006/10/18/how-to-get-the-webcam-on-the-hp-dv2000-working/]("http://dollarunderscore.wordpress.com/2006/10/18/how-to-get-the-webcam-on-the-hp-dv2000-working/")

---

### Post by charles.g.moore on 2006-12-14
loell,
I havent tried any apps yet because I cant figure out who makes the darn thing, I sent an e-mail to HP inquiring but they seem to not want to tell me.

I figured that the webcam apps were no good since its not showing up in my lsusb

any ideas???

---

### Post by charles.g.moore on 2006-12-14
is the microdia entry in my lsusb a webcam???

---

### Post by loell on 2006-12-14
> **ljpm said:**
> Thanks for the fast reply.


Bus 003 Device 003: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 001: ID 0000:0000

im not sure how this works but you can follow this instructions

[http://www.sslug.dk/~chlor/webcam/]("http://www.sslug.dk/~chlor/webcam/")

---

### Post by loell on 2006-12-14
> **charles.g.moore said:**
> is the microdia entry in my lsusb a webcam???


yes, its the webcam, according to spca5xx driver list found [Here]("http://mxhaard.free.fr/spca5xx.html")

---

### Post by loell on 2006-12-14
> **charles.g.moore said:**
> loell,
I havent tried any apps yet because I cant figure out who makes the darn thing, I sent an e-mail to HP inquiring but they seem to not want to tell me.

I figured that the webcam apps were no good since its not showing up in my lsusb

any ideas???

you can try xawtv, 

or just ekiga, which is pretty in the default install on ubuntu, and press the webcam icon, to see if there is any images coming the webcam

---

### Post by ljpm on 2006-12-14
Thanks loell,

Looks a little advance for me. I will have to play for a while.

---

### Post by charles.g.moore on 2006-12-15
> **loell said:**
> you can try xawtv, 

or just ekiga, which is pretty in the default install on ubuntu, and press the webcam icon, to see if there is any images coming the webcam
hey loell good news I followed the instructions here and it worked perfectly, had to reboot though before ekiga would see the usb webcam...

[http://www.ubuntuforums.org/showthread.php?t=280121](http://www.ubuntuforums.org/showthread.php?t=280121)

---

