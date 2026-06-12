---
title: "display problem on MacBook Pro 15 inch"
date: 2006-08-21
forum: Apple PPC Users
---

### Post by goneskiing on 2006-08-21
I've dual booted Dapper 6.06.1 on my MacBook 15 inch matte screen.
My current X has a default ati driver "vesa" .  My display mode shows 1440 900 but the resolution is only 12?? x 768 and the text is displayed as stretched to fit the screen - looks bad.

Is there a setting or driver to get the right resolution 1440 x 900 ?

---

### Post by avtolle on 2006-08-22
Have you tried the following: at a command line, type in sudo dpkg-reconfigure xserve-xorg, select defaults for most entries, be sure to select your desired graphics driver, resolutions, then when you are finished, hit Ctrl-Alt-Delete (or Backspace, depending on your keyboard) to kill X. If this doesn't work, you will need to manually edit your /etc/X11/xorg.conf file, and there are plenty of threads dealing with how to do this on the Forum. HTH.

---

### Post by idn on 2006-08-22
I installed the at driver here [http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453) and it automatically got set to the correct resolution.

---

### Post by goneskiing on 2006-08-23
sorry but thread has lots of different explanations on drivers - do you mean the flgrx drivers ?  Isn't that only if you want special glx ?  Could you list which driver ?  thks.

---

