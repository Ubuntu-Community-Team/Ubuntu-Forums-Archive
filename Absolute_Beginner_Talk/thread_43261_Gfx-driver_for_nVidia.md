---
title: "Gfx-driver for nVidia"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-21
Hey, I'm using a GForce 4 Ti4200. And I wanted the drivers for that card. Using [http://ubuntuguide.org/](http://ubuntuguide.org/) I tried to install the drivers. But now X won't load because of soem weird config. How do I restore my backup and how do I fix the drivers (preferebly using nvidias own filez0rs)?

---

### Post by Zelut on 2005-06-21
If these are the instructions you used from ubuntuguide.org...
> sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

You should be able to reverse the update like this:
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf (replace new .conf with _backup)
sudo nvidia-glx-config disable (not 100% on this command but worth a shot)

You should now have disabled nvidia-glx-config (if you need) and replaced the new .conf file with your backup.  Hope that helps.

---

### Post by Trojan1313 on 2005-06-21
[QUOTE=Trojan1313]Hey, I'm using a GForce 4 Ti4200. And I wanted the drivers for that card. Using [http://ubuntuguide.org/](http://ubuntuguide.org/) I tried to install the drivers. But now X won't load because of soem weird config. How do I restore my backup and how do I fix the drivers (preferebly using nvidias own filez0rs)?[/QUOTE]
 Now this does NOT make sense to me. Now when I was about too boot and try to fix this thing the nVidia logo displayed and X booted as normal. What the...?

And how come I still can't change to more than 1024x768 resolution? I want 1280x1024, like I use in Windows. :(

---

### Post by Zelut on 2005-06-21
I hate phantom issues like that.  Work one minute & dont the next or visa versa.  Just be glad it works now...? :)

As far as the resolution goes you may need to manually edit your X86Config file... take a look in /etc/X11/ for X86Config (or similar) and see whats listed there.

---

### Post by Trojan1313 on 2005-06-21
[QUOTE=kuyaedz]I hate phantom issues like that.  Work one minute & dont the next or visa versa.  Just be glad it works now...? :)

As far as the resolution goes you may need to manually edit your X86Config file... take a look in /etc/X11/ for X86Config (or similar) and see whats listed there.[/QUOTE]
 Thx, I'll try that.
And I'll make sure to backup the file. :p

---

