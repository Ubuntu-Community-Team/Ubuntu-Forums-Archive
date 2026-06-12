---
title: "Urgent - conflict between beryl and titlebar"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Siddharthancha on 2007-09-01
I am in a problem! I had installed beryl(sudo aptitude install beryl) and its working well. However, whenever beryl is running, the title bar of windows dissapear. Also, alt+F2 doesnt work. but wen beryl is not running, the  two work fine. Is there a solution to this?

        - I will be very greatful if you solve this.

---

### Post by forestpixie on 2007-09-01
I'm sure that it is to do with this, had to add it to my xorg.conf to enable the title bars to work

Option "AddARGBGLXVisuals" "True"

try a search on the forum for it - if you get lost come back here, but I don't know a great deal about the eyecandy - I set it up just to see what was going on and then got rid of it all :)

---

### Post by Gone fishing on 2007-09-01
I've had this with beryl and compiz fusion when some components have been incompatible with others. I'd uninstall all your beryl, compiz and emerald components and add only the right repository's  and follow the instructions you find on desktop,  effects forum [http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)

---

### Post by BobCFC on 2007-09-01
> I'm sure that it is to do with this, had to add it to my xorg.conf to enable the title bars to work

Option "AddARGBGLXVisuals" "True"

I think that goes in the Device section near the bottom ( must be root to save such as:  gksu gedit /etc/X11/xorg.conf  )


```
Section "Device"
    Identifier     "nVidia something something"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    .....
EndSection
```

---

