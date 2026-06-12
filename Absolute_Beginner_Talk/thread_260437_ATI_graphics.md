---
title: "ATI graphics"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Devile on 2006-09-18
Well... i installed my ati graphics driver and stuff... how am i sure it's running on that driver... and how do i change my resolution to the way it should be... shouldn't it be an option now that the driver is in....

---

### Post by Nrvnqsr on 2006-09-18
ok to check if you have installed your ati drivers correctly type this in the terminal

> 
fglrxinfo


you get a mention of ATI, if you do you installed correctly

if you get a "Mesa" message you got to redo it again

to change resolution go to System>Preference>Screen Resolution

---

### Post by madmetal on 2006-09-18
run  glxinfo | grep direct  
and if the answer is yes then you got 3d accelaration on so driver works fine!
about resolution try to edit /etc/X11/xorg.conf
with  sudo gedit /etc/X11/xorg.conf
but first try to find out which resolution is supported by your monitor and vga card..

---

