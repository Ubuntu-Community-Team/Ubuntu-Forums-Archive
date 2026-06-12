---
title: "23 inch cinema display and Mac Mini"
date: 2007-07-21
forum: Apple Intel Users
---

### Post by Durden on 2007-07-21
When I load ubuntu I can't get the 1900x1200 resolution I should be getting. I installed 915resolution and ran it with the -l to check for possible resolutions and it supports 1900x1440 (I believe this is right, posting on my OSX partition right now). Has anyone gotten 1900x1200 working? 

Also, I would like to add OSX to my GRUB, how can I go about this?

---

### Post by parry on 2007-07-21
You have to actually set the resolution to 1920x1200 for the 23" model using

** 915resolution *mode 1920 1200 bpp*  ** 

Where mode is the one listed when you ran the 915resolution -l - choose a mode number listing the 1900x1440 x 32. Keep bpp as 24.

And you need to run the command above on every reboot - The BIOS forgets it each time you reboot. You can edit the /etc/default/915resolution (I think so) file and achieve the same. 

HTH.
Parry

---

### Post by Durden on 2007-07-22
Well that worked, sorta. GDM now displays correctly but when I login it goes back to 1600x1200. Any ideas?

---

### Post by Durden on 2007-07-22
Nevermind, I had to go to prefs->screen resolution and set it :) Thanks a ton man, HUGE help.

Anyone have some advice on my GRUB issue?

---

