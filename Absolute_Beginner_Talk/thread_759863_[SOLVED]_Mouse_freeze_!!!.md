---
title: "[SOLVED] Mouse freeze !!!"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Biggy on 2008-04-19
hi . i change my memory RAM from 1 gb to 1.25 gb, 

my problem is : in startup gutsy 7.10 ,  freeze my usb mouse !!!!

any idea ?

---

### Post by mgranet on 2008-04-19
Hrm. That is an odd one. Tell me, what was your memory layout before the upgrade? 1x 1GB stick, or was the 1GB spread out over multiple sticks? Also, what type/speed are they?

Also, have you tried un-plugging then re-plugging in the mouse (perhaps in a different port?)

---

### Post by Biggy on 2008-04-19
is 1 x 1gb + 256mb DDR 400

i remove 256mb chip and problem still !!!

---

### Post by mgranet on 2008-04-19
Wow. That's screwed up. Can you post the output of ```
lsusb
```

---

### Post by Biggy on 2008-04-19
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 1110:9041 Analog Devices Canada, Ltd (Allied Telesyn) 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0084 Microsoft Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 059f:1010 LaCie, Ltd 
Bus 001 Device 005: ID 0ace:1215 ZyDAS 
Bus 001 Device 001: ID 0000:0000

---

### Post by mgranet on 2008-04-19
Who makes your mouse?

---

### Post by Biggy on 2008-04-19
how to find that ??

basic optical mouse usb  microsoft

---

### Post by mgranet on 2008-04-19
Well, the kernel is recognising the mouse. I would try unplugging then replugging the mouse back in (to a different port, if available) while Ubuntu is running. Other than that, I'm out of ideas. If it's a wireless mouse, try the reconnect sequence.

---

### Post by Biggy on 2008-04-19
thank you mgranet for your help !

ok.. i unplug and replug the mouse and work now but on the next restart Ubuntu,mouse freeze again...!!!!

sorry for my bad english ..

---

### Post by mgranet on 2008-04-19
Your English is great for a non-native speaker/writer.

Ok, that's good progress. Give me a few minutes to boot Ubuntu up and experiment. I remember a similar situation, and I believe there is a command to force the USB to refresh on boot.

---

### Post by mgranet on 2008-04-19
Also, did you reinstall the 256MB RAM stick? If so, did the unplug trick work again?

---

### Post by Biggy on 2008-04-19
i remove 256mb ram & unplug plug again usb mouse..

restart Ubuntu and work fine now ..

:)

thank you **mgranet**

---

### Post by mgranet on 2008-04-19
Hrm. If I read that correctly, you can reboot and the mouse works fine, without the 256MB stick in. But with the stick installed, you have to unplug the mouse, plug it back in and it works; but not after a reboot? If that's the case, then you might have a bad 256MB stick.

---

### Post by mgranet on 2008-04-19
And honestly, unless you are doing hardcore computing (gaming, VM, major multi-tasking), you will probably not notice the missing 256MB.

---

