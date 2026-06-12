---
title: "LightDM Won't Start, Can't Start Budgie"
date: 2018-04-26
forum: Apple Hardware Users
---

### Post by jennyfrancis49 on 2018-04-26
I was doing some stuff on my Macbook running Budgie and I was doing some too-heavy multitasking and the computer was running super slow even after closing most programs. So I rebooted, and then I couldn't use the computer. 

When it boots, I get the normal splash screen, then the screen goes blank, then starts flashing repeatedly. I can see the tty1 login prompt between flashes, it eventually stops flashing but I cannot login--nor can I change to a different tty, ctl+alt+Fx does nothing. 

If I add nomodeset drm.modeset=0 nouveau.modeset=0 to my kernel options then it still boots, blanks, and flashes, but after a minute I can log into the shell. 

Once in the shell, I've done apt install --reinstall lightdm lightdm-gtk-greeter xorg xserver-xorg as well as dpkg-reconfigure lightdm xorg xserver-xorg. 

I've tried replacing my xorg.conf with the default values from the Nouveau project webpage. 

When booting nomodeset I can run startxfce4 and xfce will start up. 

When I run sudo lightdm the screen flashes a few times then goes back to the shell. Only error in the log file is:

CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

Without lightdm I can't start budgie. I'm pretty much entirely out of ideas on how to fix this. I'd really, really prefer not to have to back up my data and do a clean install. The only thing I can think of that might have broken it was that I had installed Deepin Desktop from a PPA to test out, I have since purged all Deepin packages

---

### Post by QIII on 2018-04-26
Moved to Apple Hardware Users for a better fit.

---

### Post by Frogs Hair on 2018-04-26
> [COLOR=#000000]I've done apt install --reinstall lightdm lightdm-gtk-greeter xorg xserver-xorg as well as dpkg-reconfigure lightdm xorg xserver-xorg. [/COLOR]


FYI , Budgie uses slick-greeter as of 17.10. I don't know about the 16.04 remix version though.

---

### Post by jennyfrancis49 on 2018-04-27
Reinstalled slick-greeter too, no luck. gdm3 has the same results--flashing screen, no interface. 

Apparently one of my hard power cycles when I couldn't do a proper reboot borked something else, even recovery mode isn't booting anymore. Hm. Probably best for a reinstall, painful as it is.

---

