---
title: "Asus 1001HA problem"
date: 2011-06-19
forum: Asus Ubuntu Support (CLOSED)
---

### Post by thoruntur_6969 on 2011-06-19
i've installed my netbook with ubuntu 11.04. later, i am unable to shut down my netbook. when it click on shut down it freezes the computer. i've tried re-installing the system and still encountered the same problem.:confused:

---

### Post by kiddfroster on 2011-06-20
Try installing the Asus acpi scripts using:

```
sudo apt-get install eeepc-acpi-scripts
```

When I did this my Eee PC had better power management, so this may be the option for you.

---

### Post by kyteflyer on 2011-06-22
> **kiddfroster said:**
> Try installing the Asus acpi scripts using:

```
sudo apt-get install eeepc-acpi-scripts
```

When I did this my Eee PC had better power management, so this may be the option for you.

I dont have shutdown issues, but I do have a power saving system which refuses to acknowledge my instruction to NOT dim the screen and not go idle after 3 minutes when on mains power.  

Tried your code but all I got was unable to locate package.  Will it be somewhere in the canonical repository?

---

### Post by toor58 on 2011-06-24
@thoruntur_6969: have you tried setting the power switch to shutdown. right click on the shutdown symbol upper right corner of screen> system settings> Groups> Hardware> Power Management> general tab. choose shutdown. see if that works.

@kyteflyer: believe those scripts are old school and not needed in 11.04. Could be wrong but my 1001px has everything working, including Fn shortcuts, no major hitches or glitches.
I have noticed the probs you mentioned. I have been very busy of late so if you have never done it before, now is a good time to file a bug report. Come back with the details and I will add to it after you.

---

