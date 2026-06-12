---
title: "/etc/X11/xorg.conf default settings?"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by rjdsmiths on 2008-04-19
Hey Ubuntuers

I Kind of feel stupi for asking this question but..

I was trying to install an ATI driver (at 2:00 am) and while doing it I didn't Backup my /ect/X11/xorg.conf
and now i need to go bac to the original but can't.

Is there anyway I can go to default of go through a configurator or somthing 

Please help but not too harsh (I alredy feel bad):cry:

---

### Post by aeiah on 2008-04-19
sudo dpkg-reconfigure xserver-xorg

---

### Post by prshah on 2008-04-19
> **rjdsmiths said:**
> 
I was trying to install an ATI driver (at 2:00 am) and while doing it I didn't Backup my /ect/X11/xorg.conf

You should have backup conf files scattered in the /etc/X11/ directory. ```
ls /etc/X11/ | grep xorg
``` Typical backup filename will be xorg.conf~. You can restore that as your main file with ```
sudo cp -f /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```, after which you should restart your Xserver with Ctrl+Alt+BkSpace.

---

