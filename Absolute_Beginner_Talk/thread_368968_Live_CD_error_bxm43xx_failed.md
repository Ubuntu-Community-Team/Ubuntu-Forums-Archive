---
title: "Live CD error: bxm43xx failed"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by dracomordag on 2007-02-23
when i attempt to run the LiveCD on my laptop, I get errors relating to a bxm43xx driver, which after about 10 seconds disappear, the screen stays on, but its all black. what do i do? i installed Ubuntu on my desktop well enough (some minor ATI-related errors), but at least then i didnt have a 10 second time limit as to what i could type in.

---

### Post by nereid on 2007-02-24
As far as I know the bxm43xx driver is a wifi driver. Maybe you could disable the wifi card manually or from BIOS and try again.

---

### Post by dracomordag on 2007-02-25
i disabled it through XP's Control Panel->System, but that didnt work

im guessing that that only applies to XP, so how do i disable it overall?

---

### Post by nereid on 2007-02-25
There should be a BIOS option to disable any onboard devices, as far as I know.

---

### Post by dracomordag on 2007-02-25
i dont follow

---

### Post by jkeyes0 on 2007-02-25
The BCM43XX error always occurs when using the LiveCD on a system with a Broadcom 43XX wireless card. It's nothing to be concerned about. However, the problem with the black screen is something else. What are the specs on the laptop you're working on? (specifically, the video card)

---

### Post by nereid on 2007-02-26
> **dracomordag said:**
> i dont follow

The BIOS is the small little program which resides on your motherboard which will be started before your OS will be started. You can usually enter it immediately after the first picture appears on your screen and you've just pushed the power button. Just press F2 or DEL to enter the BIOS (depends on the type of BIOS you're using). [Wikipedia: BIOS](http://en.wikipedia.org/wiki/BIOS).

Usually you can disable any onboard device in the BIOS. This means that any OS wouldn't know about it until it is enabled again.

---

### Post by dracomordag on 2007-02-27
> **jkeyes0 said:**
> The BCM43XX error always occurs when using the LiveCD on a system with a Broadcom 43XX wireless card. It's nothing to be concerned about. However, the problem with the black screen is something else. What are the specs on the laptop you're working on? (specifically, the video card)

two pentium 4 3.2 GHz chips
XGI volari-xp5 v2.113.DELL_C

---

### Post by dracomordag on 2007-02-28
does ubuntu not come with XGI drivers? how could i get them when i cant even run the LiveCD?

---

### Post by dracomordag on 2007-03-03
yes? no? maybe?

---

### Post by dracomordag on 2007-03-11
...

---

