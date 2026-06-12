---
title: "Automatically waking from Sleep Mode"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by bakaeigo on 2007-12-21
Does anyone know of a utility for Gutsy that will automatically wake up my computer from sleep mode at specific times?
Thanks in advance.

---

### Post by puccaso on 2007-12-21
it could be a few reasons.

maybe your bios has been setup to awaken at certain times.
also, it is normal that your system will awaken when the battery is too limited 
in order to shutdown safely and/or hibernate.. 

try this

```
sudo apt-get install powertop
```

this will give u an idea as to what might cause the wake ups prematurly

---

### Post by bakaeigo on 2007-12-21
> **puccaso said:**
> it could be a few reasons.

maybe your bios has been setup to awaken at certain times.
also, it is normal that your system will awaken when the battery is too limited 
in order to shutdown safely and/or hibernate.. 

try this

```
sudo apt-get install powertop
```

this will give u an idea as to what might cause the wake ups prematurly

:) My standby is working perfectly fine. I probably wasn't clear enough, but I was wondering if there was a program that I could download so that I can set my computer to wake up from standby at specific times.

---

### Post by puccaso on 2007-12-21
oh, alright ic

well then you can defo use ur bios wake up if it supports it

have a look here

[http://www.nabble.com/Mythwelcome-and-ACPI-wake-up-td13651749s15552.html](http://www.nabble.com/Mythwelcome-and-ACPI-wake-up-td13651749s15552.html)

---

