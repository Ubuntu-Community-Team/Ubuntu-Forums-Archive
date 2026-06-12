---
title: "i need help, compiz fusion error and restricted nvidia maneger driver not in use"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by powerfulx100 on 2007-10-07
i think I've been using the slow graphics driver that comes with the Ubuntu feisty and gusty gibbon. when i run ' compiz --replace' i get this error 


root@brent-desktop:~# compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

i deleted my xorg.conf without backup and my nvidia driver is in restricted driver manager is "not in use".please help how can i enable this and run compiz fusion and use a better driver in general? thank you

---

### Post by hollerith on 2007-10-07
You'll need to load the nvidia drivers by ticking the option in 

System --> Adminstration --> Restricted Drivers Manager

for an nvidia card.  

BTW nvidia cards don't need Xgl.  unless it is an older type.  You did install xgl, didn't you?

What do you see if you run glxgears?

---

### Post by powerfulx100 on 2007-10-07
hi, the graphics card is nVidia [Vanta/Vanta LT]. I get this when I run  glxgears : 

root@brent-desktop:~# glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

i installed something called xserver-xgl but don't know what to do with it please help here. and when I click to tick the option in restricted driver (it was already ticked but not in use) it said &#8220;Reconfiguring xorg.conf is not possible: /etc/x11/xorg.conf is invalid or does not exist". so what can I do to fix these? thank you

---

### Post by LowSky on 2007-10-07
boot computer into safe mode then type
```
 sudo dpkg-reconfigure xserver-xorg 
```

follow the step, and pick your corect video card

---

### Post by powerfulx100 on 2007-10-07
ok done, should i download a different driver? it's running legacy driver or something.   but this **** is running very very slow and i see broken boxes sometimes. what could be the reason?

---

