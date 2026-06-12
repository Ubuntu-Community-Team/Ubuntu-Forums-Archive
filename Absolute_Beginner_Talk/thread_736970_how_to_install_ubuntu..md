---
title: "how to install ubuntu."
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by buxzed on 2008-03-27
i try ed to run the live cd .after loading i can hear the welcome music.but no images.only an blank scree.monitor lights are blinking

---

### Post by MONODA on 2008-03-27
boot off the cd again but this time select safe graphics mode instead at boot prompt.

---

### Post by tylerspaska on 2008-03-27
Hard to say with such little information, but I would guess that there is a problem with your graphics driver. Which version / release of Ubuntu are you using? 7.10? And what hardware are you trying to install on?

Do as Monoda says and use 'safe graphics.' Also, set up your graphics drivers (and several other things in your system) by reconfiguring your xorg.conf file.

Here's how you do it:

If you are at the desktop open a terminal (search for it under the aplications) if you are at the part of the boot where you hear the music but don't see anything on the monitor hit Ctrl+Alt+F1, enter your user name and password (if you are using the live cd you can skip this as there is no user name or password) then enter: 
> sudo dpkg-reconfigure xserver-xorg 
You will be taken through several prompts, most of them will be intuitive. When you are asked for your graphics driver you can enter what you think is right and try it, but if you are having problems then you should probably select 'vesa' When you are done and the configuration is saved you can press Ctrl+Alt+Backspace to reset xserver (the display system and its components)

---

