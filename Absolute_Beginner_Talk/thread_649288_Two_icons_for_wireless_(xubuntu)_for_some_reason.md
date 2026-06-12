---
title: "Two icons for wireless (xubuntu) for some reason"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by alwiap on 2007-12-24
Hi,

I have a xubuntu laptop with wireless (bcm4306), works fine and all, but for some reason when I connected to a wireless network one time, it displayed two connecting signs, and now it looks like it is connected to two networks, even though its not. Look at my attached screenshot.

Any ideas how to get it back to one icon?  I'm not connected to two networks and its annoying me :(

---

### Post by adam.tropics on 2007-12-24
You have two instances of nm-applet running. You should go to system-->preferences-->Sessions then see if it is listed twice in startup programs. While there you can remove the extra instance in the current session tab.

edit:oops....xubuntu...but still two instances of nm-applet!

---

### Post by alwiap on 2007-12-24
> **adam.tropics said:**
> You have two instances of nm-applet running. You should go to system-->preferences-->Sessions then see if it is listed twice in startup programs. While there you can remove the extra instance in the current session tab.

edit:oops....xubuntu...but still two instances of nm-applet!

thanks for the info!  I'm currently looking for the xubuntu equivalent of the Sessions in GNOME, does anyone know how to get to the place where I can see where the 'nm-applet' is listed twice?  I'll keep looking around.

---

### Post by alwiap on 2007-12-24
EDIT:  the only thing I found with the network applet was in System - settings - autostarted applications but it is only checked once under 'Network Manager applet'

---

### Post by overdrank on 2007-12-24
> **alwiap said:**
> EDIT:  the only thing I found with the network applet was in System - settings - autostarted applications but it is only checked once under 'Network Manager applet'

Hi and I know this is not the most technical response but cant you just right click and remove from the panel?

---

### Post by alwiap on 2007-12-24
> **overdrank said:**
> Hi and I know this is not the most technical response but cant you just right click and remove from the panel?

nope, tried that.  hopefully someone with xubuntu expertise can cure me :D

---

### Post by bobotoes on 2007-12-28
```
rm .cache/sessions/*
```
this worked for me.

---

### Post by Thag on 2007-12-29
i had the same problem and the rm /cache/sessions/* solution worked for me as well, however it seems to have hosed my bcm4306 driver or something because when i rebooted nm was no longer working.  I ran an 'lshw' and saw that my wireless net card was DISABLED.  Running bcmxx-fwcutter on bcmwl5.sys and then rebooting took care of the problem.

--- using xubuntu Gutsy gibbon ---

---

### Post by alwiap on 2007-12-30
> **bobotoes said:**
> ```
rm .cache/sessions/*
```
this worked for me.

this worked perfectly for me, thanks a lot!

---

