---
title: "Dial up - modem"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by kvmusic on 2007-08-29
I've installed gnome ppp for dial up... and my machine can't seem to find the modem.  I ran the auto detect for modem and it noted that it can't be found.

I'm working on a Compaq 500c machine...

Any thoughts, ideas... etc. would be appreciated!

---

### Post by oilchangeguy on 2007-08-29
where are you located? if in the US, have you checked highspeed pricing recently? there are entry level packages available. and pricing is very near dial-up, but with much better speed. say a min. of 300kps. instead of maybe 50kps.

---

### Post by dca on 2007-08-29
If it's an internal Winmodem or softmodem, don't bother.  If it's a serial external modem than it should be listed under ->system ->administration ->network ->modem  make sure the modem port is set to either /dev/modem, modem0, modem1, or ttyS0, or ttyS1 and run the auto-detect to verify proper port...

---

### Post by kvmusic on 2007-08-29
This is for my mother in law... I recommended Linux because all she does is email and do some light surfing on the internet.

I felt Linux would provide her with a stable system...

She's already on dial up so I'm just trying to accommodate her situation.

How can I find the information to determine if the modem is a softmodem or a winmodem?

---

### Post by oilchangeguy on 2007-08-29
> **kvmusic said:**
> This is for my mother in law... I recommended Linux because all she does is email and do some light surfing on the internet.

I felt Linux would provide her with a stable system...

She's already on dial up so I'm just trying to accommodate her situation.

How can I find the information to determine if the modem is a softmodem or a winmodem?

if she's paying, say 24.95 for dial-up. if highspeed is available, (dsl or cable) the lowest package is usually around 19.95. and even at that low level, it blows dial-up away.

---

### Post by dca on 2007-08-29
In the US there's:
 
 [http://www.550access.com](http://www.550access.com)   (cheap dial-up)
 
A winmodem or softmodem is usually an internal PCI card modem...  It requires software (usually Windows and a driver) to work as opposed to a serial port external modem...

---

### Post by dca on 2007-08-29
If it is an internal PCI modem, find out the manf, you may be able to get by using drivers like these:
 
[http://www.linuxant.com/drivers/hsf/index.php](http://www.linuxant.com/drivers/hsf/index.php)

---

