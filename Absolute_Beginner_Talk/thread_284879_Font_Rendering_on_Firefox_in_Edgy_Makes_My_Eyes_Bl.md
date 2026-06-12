---
title: "Font Rendering on Firefox in Edgy Makes My Eyes Bleed!"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-10-26
Ouch. After upgrading to Edgy/FF2 this morning, the font rendering in FF seems to have gone a bit funny. It's all fuzzy and hurts my eyes :(

Anyone else having this problem?

Oh yeah, another font issue is that (if possible!) the rendering in aMSN is even WORSE!!!

Loving Edgy otherwise :)

---

### Post by altonbr on 2006-10-26
It appears they've changed a lot of their fonts around (to make them have less of a kerning?), but I'm not sure if they've changed their anti-aliasing methods.

Go to System > Preferences > Font and choose 'Subpixel Smoothing (LCDs)'. That's always worked best for me.

---

### Post by happy-and-lost on 2006-10-26
*d'oh!*

Genius! Cheers :D

---

### Post by BHunsaker on 2006-12-21
For us beginners those trying to figure out why fonts look bad, the problem may also be caused by bad pixel timing values in the xorg.conf file.  Check out the "ModeLine" line option of the "Monitor" section in xorg.conf.

In my case, I searched the /var/log/Xorg.0.log to find the "h_active" and "v_active" lines as shown:

(II) I810(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) I810(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0

which resulted in me adding the following to /etc/X11/xorg.conf (Section "Monitor"):

ModeLine "1280x1024" 108.00  1280 1328 1440 1688  1024 1025 1028 1066

Without this, the system was selecting to run my screen at 75Hz instead of the 60Hz recommended  by the LCD.  (And I always thought higher refresh frequencies were better :-)).

---

