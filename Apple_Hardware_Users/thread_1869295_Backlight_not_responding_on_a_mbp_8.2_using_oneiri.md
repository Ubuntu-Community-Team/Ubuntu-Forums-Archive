---
title: "Backlight not responding on a mbp 8.2 using oneiric"
date: 2011-10-25
forum: Apple Hardware Users
---

### Post by yjr on 2011-10-25
Hi all,
My backlight buttons don't work the on screen bar changes but not the backlight of the screen manually tweaking the brightness value in /sys/class/backlight/acpi_video0/brightness does nothing either.

Also the normal unity mode is not working only the 2d one is ok although I did install fglrx driver via synaptics (jockey seems broken)
Any help is welcome !
Cheers

---

### Post by heathman001 on 2012-02-02
Hey, not sure if you're still struggling with this, but I experienced a similar problem on my mbp 8,3. I found that if I booted to Ubuntu through rEFIt, I could not control the backlight brightness. However, if I held the ALT key during boot, and selected the drive containing Ubuntu there, the brightness/contrast keys work. Hope that helps.

---

