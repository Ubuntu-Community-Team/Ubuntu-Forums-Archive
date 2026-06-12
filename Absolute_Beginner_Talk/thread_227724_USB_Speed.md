---
title: "USB Speed"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by yanewby on 2006-08-02
I am considering installing Ubuntu on another (old) PC.  How do I determine what speed the USB ports are in the other PC from Ubuntu?

I don't have the motherboard manuals and I am reluctant to open the case of the PC in case I damage something and it is a non-branded (home-built) PC.

---

### Post by timmy666 on 2006-08-02
if the computer is older than 5 years it probably has a USB 1.0 (1.5Mbps) or USB 1.1 (12Mbps)

if not, it has a USB 2.0 (480Mbps)

---

### Post by yanewby on 2006-08-02
Is there not a way of determining this rather than guessing?

The computer is approximately 3-5 years old and wasn't top of the range even back then.  From my reckoning (and your advice) it could be either USB1.1 or USB2.0 and I thought there might be a simple way to determine which...

---

### Post by talkingwires on 2007-07-12
This is about a year too late, but this is the second page Google returned when I was looking for a way to do this, and now I'm posting the answer for posterity. Use:```
grep Ver /proc/bus/usb/devices
```

---

### Post by dgrafix on 2008-02-25
doesnt seem to work, it says invalid file or dir

---

