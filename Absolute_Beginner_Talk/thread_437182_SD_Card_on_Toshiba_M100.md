---
title: "SD Card on Toshiba M100"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by w1zer on 2007-05-08
Hi

I have just installed kubuntu for the first time on my Toshiba M100 laptop.  I want to use the onboard SD Card reader to view my pictures.  When I insert the card, nothing happens?

Can anyone offer any advice?

Thanks

---

### Post by mthakur2006 on 2007-05-08
what kind of card reader have you got? if you could post the result of ```
 lspci -vv 
``` we might be able to help.
Thanks,

---

### Post by cotcot on 2007-05-08
Put the card in and type "dmesg" in terminal. Look at the end of the text if you see something about your card. If yes than at least the device is recognised and maybe not automatic mounted. You can mount it manually.
If no then maybe some kernel option is missing. Instead of searching for this it might be easier to buy some card reader to be plugged in a usb connector (I bought one for 12 euro).

---

