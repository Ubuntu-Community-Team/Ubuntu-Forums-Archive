---
title: "Avoid pommed for keyboard backlight control"
date: 2010-02-04
forum: Apple Hardware Users
---

### Post by DizzyTech on 2010-02-04
Is there any documented way to get the keyboard backlight (and keys F5 and F6) working without the use of pommed, preferably using something like gnome-power-manager.  A search hasn't pulled much anything helpful.

---

### Post by dennis123123 on 2010-02-04
xbindkeys

+

```
echo 255 | sudo tee /sys/devices/platform/applesmc.768/leds/smc\:\:kbd_backlight/brightness
```

---

### Post by Appleshare on 2010-02-05
Not the F5/F6 keys as far as I remember, but look here: [https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Keyboard%20backlight%20on%20a%20mbp%205,4%20without%20pommed](https://help.ubuntu.com/community/MacBookPro5-5/Karmic#Keyboard%20backlight%20on%20a%20mbp%205,4%20without%20pommed)

If you have pommed installed and working but just don't want it to control the kb backlight, you can deactivate this in /etc/pommed.conf, then restart pommed with "sudo service pommed restart" (or "sudo /etc/init.d/pommed restart" if you use Ubuntu versions older than 9.10)

---

### Post by DizzyTech on 2010-02-05
The problem is that I want _something_ to control the keyboard backlight just not pommed because it interferes with my other function keys.

---

### Post by dennis123123 on 2010-02-06
did you not read the two replies you have already had?

...

Its controllable through sysfs; the possibilities are endless!

---

### Post by DizzyTech on 2010-02-06
Yes, yes I did.  But I asked for was if anybody knew if it could be done through the DE - as it was in Jaunty, I might add - so that I may take advantage of dimming, power-saving, HUD notifications, etc.  I appreciate the help, but I do not appreciate being talked to as if I were a toddler.  I have worked with both yours and Appleshare's very helpful suggestions, but it did not achieve the effect that I was striving for.  Is there something wrong with that?  The possibilities are indeed endless; I'm looking for a different one!

---

