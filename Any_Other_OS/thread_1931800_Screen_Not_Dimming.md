---
title: "Screen Not Dimming?"
date: 2012-02-26
forum: Any Other OS
---

### Post by smc170 on 2012-02-26
Okay, so i hope i dont get alot of flak for this, but here it goes;

I'm on Linux Mint 12, and all the sudden, my screen cant dim or be brightened via the dedicated buttons or the settings manager.

My setup: Lenovo ThinkPad T420, Nvidia NVS 4200M

I think maybe the Nvidia drivers i installed may have messed up the brightness somehow? My best guess is that i need to edit either the xorg.conf or the xorg.conf.nvidia

Once again, sorry for posting here, as i know it's Ubuntu forums, but I didnt get any support from the Mint forums, and i said, "Hey, we're all family! We all come from debian! Ubuntu is like Mints brother!"

So thanks for any support!

---

### Post by smc170 on 2012-02-26
Solved my own n00b question!

So you just need to insert a small line of code under the *Devices* section of either the xorg.conf or the xorg.conf.nvidia. I didnt know which one to edit, so i edited both, and all works good now! Credit thinkwiki.org/wiki/LCD_Brightness

> A bug cropped up for some with recent nvidia driver causing brightness controls not to work (For example, on my W520 using the nvidia binary driver). The solution seems to be adding a flag to enable brightness control by the nvidia driver
 
 ```
# Add to your "Device" section in /etc/X11/xorg.conf and restart X
 Option "RegistryDwords" "EnableBrightnessControl=1"
```

---

### Post by Perfect Storm on 2012-02-27
Moved to Other OS/Distro Talk.

---

### Post by loomes8 on 2012-12-16
Never mind

---

