---
title: "how do i save / autoload the nvidia tv-out hue and saturation?"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by NESFreak on 2006-10-06
after changing the tv-out hue and saturation in the nvidia x server settings it works, but after an xorg restart i can start all over again. How do i save these settings?

NESFreak

---

### Post by NESFreak on 2006-11-12
so in the end i found it out myself.
setting the hue form the command line goes```
nvidia-settings -a tvhue[tv-0]=35
```

to do this at startup
```
sudo gedit /etc/X11/gdm/Init/Default
``` and add ```
nvidia-settings -a tvhue[tv-0]=35
``` just above ```
exit 0
```

hope it also helps anybody else then me

NESFreak

---

### Post by aparigraha on 2007-10-23
EDIT: Actually this doesnt work !!

To help anybody else using Xubuntu Gutsy... I edited 

sudo nano/etc/gdm/Init/Default
**not** sudo nano /etc/X11/gdm/Init/Default (which doesnt exist... gdm-folder moved)

putting 
nvidia-settings -a tvhue[tv-0]=YOUR OWN VALUE

just above the last line... exit 0

hope it helps someone.

---

### Post by aparigraha on 2007-10-24
If someone has any input on how to make the Hue and Saturation settings work in Gutsy (Xubuntu)... I would very much appreciate it. Worked perfect in Feisty. I'm going crazy having to set the TV Saturation and/or TV Hue, manually every time I reboot in nvidia-settings.

Please

---

### Post by aparigraha on 2007-11-07
> **aparigraha said:**
> EDIT: Actually this doesnt work !!

To help anybody else using Xubuntu Gutsy... I edited 

sudo nano/etc/gdm/Init/Default
**not** sudo nano /etc/X11/gdm/Init/Default (which doesnt exist... gdm-folder moved)

putting 
nvidia-settings -a tvhue[tv-0]=YOUR OWN VALUE

just above the last line... exit 0

hope it helps someone.

please I really need this. I turn my machine on and off very often. having to adjust nvidia-settings manually is really annoying. 

/etc/X11/gdm/Init/Default   doesn't exist in Gutsy... at least not on my machine.
nano/etc/gdm/Init/Default  exists but nothing happens when i edit it, saturation and hue always reset to default values on reboot.

Anyone?

---

### Post by aparigraha on 2008-01-14
one more bump! 
anyone?

---

### Post by artard on 2008-04-11
im new to ubuntu and also using hardy beta so sorry if this doesn't make sense...

i entered the following into the terminal and got the exact feedback from my TV that i wanted:
nvidia-settings -a tvsaturation[tv-0]=120
nvidia-settings -a tvoverscan[tv-0]=10

i couldn't find /etc/X11/gdm/Init/Default, but i did find /etc/gdm/Init/Default, so i added those two lines just above "exit 0", logged out/in and it used those settings!

now whenever i reboot my TV is configured just the way i want it.  hope that helps

---

