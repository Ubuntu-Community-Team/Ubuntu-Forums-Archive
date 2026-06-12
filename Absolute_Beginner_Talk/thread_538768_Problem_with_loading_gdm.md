---
title: "Problem with loading gdm"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by malangi on 2007-08-30
Hi all.

Ubuntu was running quiet fine on my dell inspiron6400 laptop, but there was a problem with the ati graphics driver. So i thought its better to uninstall the graphics driver and reinstall it. when i uninstall and restarted, the xserver stop responding and system crashes while loading gdm. I manually configured the xorg.conf but it gives the same error. No screens found or no screen with the suitable configuration found. Then i try to reinstall the ubuntu but it gives the same error. I am using dual boot and i do't want to disturb my windows.


Thanks

---

### Post by Hobo Joe on 2007-08-30
What is your graphics card?


Try running this:
```

sudo dpkg-reconfigure xserver-xorg

```
When it get's to the part for selecting the drivers, pick 'vesa', and then just leave everthing else at default.

Then try booting back up.

---

### Post by malangi on 2007-08-30
Its ATI radeon, i have tried with vesa but it always stucks up .

---

