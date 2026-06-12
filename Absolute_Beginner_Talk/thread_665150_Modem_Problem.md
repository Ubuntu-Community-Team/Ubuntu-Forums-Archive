---
title: "Modem Problem"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by ebon90 on 2008-01-11
I have to send information via my dial-up modem with a program called Winasap 2003. I'm using Wine with it since it's a windows program. I try to send a test transition but I get this weird box. I think the problem is that my dial-up modem isn't activated. How do you activate the modem with out putting phone numbers and stuff?

---

### Post by Shazaam on 2008-01-11
What kind/brand of modem is it? Open terminal and type in 
```
lspci
```

This command will print out your hardware list.

---

### Post by phidia on 2008-01-11
If you have an internal modem chances are pretty god that it's a winmodem (uses the windows OS to function) Software modems were cheaper to make.
Anyway if you go [here]("http://www.linmodems.org/") you can get the scanmodem tool and how tos on getting your modem to work. There are how tos at the unbuntu forums also.

---

### Post by ebon90 on 2008-01-11
I typed in ```
 lspci
``` and got this for the modem Agere Sysyems V.2.956k Winmodem

---

### Post by phidia on 2008-01-12
Dial up modem[ how to]("https://help.ubuntu.com/community/DialupModemHowto").

---

### Post by ebon90 on 2008-01-12
Thank you, I'll try this now.

---

