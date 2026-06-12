---
title: "resolution problem"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by narayanwaraich on 2008-04-12
I installed ubuntu on my windows XP pc using Virtualbox.Its default resolution was set as 800x600 and vitualbox told me that i can change resolution by going into the resolution settings of the OS,but when i went into resolution settings of ubuntu which i was running as live cd (** remember inside virtualbox**)it  only had the option of 800x600 and one other which was lower.My pc can support a resolution of 1200x800 and i am currently using it too.I would like to add here that when i use ubuntu from live cd(**not inside virtualbox**)it displays on normal resolution of 1200x800.help me as i am not able to install ubuntu as i can't see the screen completely(due to resolutiopn problem).

What i want is normal resolution inside(1200x800) but inside **Virtualbox**Anybody for help plz......:confused:

---

### Post by Diabolis on 2008-04-12
the resolutions are stored in this file **xorg.conf**, you can edit it with this command:
```
sudo gedit /etc/X11/xorg.conf
```
note that **X11** uses a uppercase X

you''l find a section called **Screen**. Thats where you add/remove resolutions.

here is mine:
```
DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800" "1024x768" "800x600" "640x480"
        EndSubSection
```

I use only 24 depth, but maybe you have more. You can add/remove different screen resolutions for different depths.

Another way to do it is with this command:
```
sudo dpkg-reconfigure xserver-xorg
```
This will reconfigure X11. At some point it will ask you which resolutions you want to use, so just pick the ones you need.

---

