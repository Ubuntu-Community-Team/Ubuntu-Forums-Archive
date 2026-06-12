---
title: "[SOLVED] HELP . . . Desktop Effects Problem with Xubuntu"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by asbarbenator on 2008-03-19
I am running an old Dell Latitude LS, Pentium III 500mhz, 256 k, with xubuntu Gutsy. I enabled the "Desktop Effects" and now I cannot get access to my desktop. Each time I begin a new session the computer freezes with a blank brown desktop and I cannot access ANYTHING. Is there a way i can disable Desktop Effects from the terminal? If so, how? Please walk me through it, I'm fairly new to Linux. Thanks.

---

### Post by overdrank on 2008-03-19
> **asbarbenator said:**
> I am running an old Dell Latitude LS, Pentium III 500mhz, 256 k, with xubuntu Gutsy. I enabled the "Desktop Effects" and now I cannot get access to my desktop. Each time I begin a new session the computer freezes with a blank brown desktop and I cannot access ANYTHING. Is there a way i can disable Desktop Effects from the terminal? If so, how? Please walk me through it, I'm fairly new to Linux. Thanks.

HI and welcome, you can try and boot into recovery mode which is usually the second choice in the grub. Then reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by asbarbenator on 2008-03-19
I tried that but the computer still freezes on the same brown screen on startup.

---

### Post by jan quark on 2008-03-19
> I tried that but the computer still freezes on the same brown screen on startup.

so you do not get to the display where you can change the sessions? I mean the login screen?

---

### Post by Captainm on 2008-03-19
What about adding
```
 
Section "Extensions"
Option "Composite" "Disable"
EndSection
```
to xorg.conf?

---

### Post by asbarbenator on 2008-03-19
> **jan quark said:**
> so you do not get to the display where you can change the sessions? I mean the login screen?

I did get to the session login screen, but when I logged in the computer froze on the brown screen.

---

### Post by asbarbenator on 2008-03-19
> **Captainm said:**
> What about adding
```
 
Section "Extensions"
Option "Composite" "Disable"
EndSection
```
to xorg.conf?

How do I access xorg.conf from the terminal without relying on mousepad or another GUI text editor?

---

### Post by Captainm on 2008-03-19
Boot in recovery mode. That's the second option in the grub menu. If you don't have a dual boot setup you'll have to pres Esc when you see a countdown timer during boot. Then type ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
``` to backup xorg. Then type ```
sudo nano /etc/X11/xorg.conf
``` to make the changes described in my above post. After that Ctrl+o to save, Ctrl+x to exit, reboot and cross your fingers.

---

### Post by bro on 2008-03-19
I had this problem and solved from commandline with
```
sudo mv /home/$USER/.config/compiz/compiz-manager /home/$USER/.config/compiz/xxxcompiz-manager 
```

replace $USER with your username. This renames compiz-manager file so it cannot be found therefore not executed therefore not start therefore not create problems. :D

You might also try to login with Gnome Failsafe. 
You could try to mess with your xorg.conf though it never made me happy to do stuff like that. It did make me nervous, but you might be nervous already :) Also I don't know how xorg.conf works at all so I was just following instructions that made no sense to me... soo... whatever..:rolleyes:

---

### Post by asbarbenator on 2008-03-20
> **Captainm said:**
> Boot in recovery mode. That's the second option in the grub menu. If you don't have a dual boot setup you'll have to pres Esc when you see a countdown timer during boot. Then type ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back
``` to backup xorg. Then type ```
sudo nano /etc/X11/xorg.conf
``` to make the changes described in my above post. After that Ctrl+o to save, Ctrl+x to exit, reboot and cross your fingers.

This worked.  Well, sort of.  I followed this advice, and added the text mentioned in the previous post at the end of my xorg.conf file.  I don't know if this was the right place to do that, but upon my next startup, xubuntu launched into what it called "low graphics mode" which disabled the compositor (desktop effects).  I was able to login normally, switched the compositor off under the window tweaks menu, removed what I had added from my xorg.conf, and rebooted.  Everything is back to normal, I didn't even lose my desktop configuration.  Thanks to everyone for all of your help and suggestions.

---

