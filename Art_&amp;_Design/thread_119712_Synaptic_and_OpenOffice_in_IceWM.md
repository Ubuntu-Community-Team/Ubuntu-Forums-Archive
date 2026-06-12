---
title: "Synaptic and OpenOffice in IceWM"
date: 2006-01-20
forum: Art &amp; Design
---

### Post by anton.b on 2006-01-20
Over the last couple of weeks I've managed to get IceWM almost completely themed like the Gnome "Human" theme. Using the nice Human theme for IceWM, GTK2 theme switcher, FBpanel and changing/adding some things on my own the overall result is exactly what I wanted... execpt for the two programs mentioned above. I don't know why, but both Synaptic and OpenOffice use the standard GTK1 theme in stead of the GTK2 theme. Since I use OpenOffice on an almost daily basis throughout the day, I'm immensly bothered by this, particularly given the nice integration of the other GTK2 programs like Firefox, Sylpheed, GQview, XFFM, GVim and others.
So my question is plain and simple: does anyone know how to make Synaptic and OpenOffice use my GTK2 Human theme like they do in Gnome?
Thank you!

---

### Post by Squalor on 2006-01-20
Do you have the openoffice.org(2)-gnome package installed? As for Synaptic, make sure you have the theme you're running installed in /usr/share/themes.

---

### Post by anton.b on 2006-01-20
[QUOTE=Squalor]Do you have the openoffice.org(2)-gnome package installed?[/quote]
The openoffice.org-gnome-integration package is installed, but appearantly pretty useless when you don't have Gnome itself installed. I did however find the solution to my problem. I just had to set an environment variable "OOO_FORCE_DESKTOP=gnome" and now OOo looks just like in Gnome.

[QUOTE=Squalor]As for Synaptic, make sure you have the theme you're running installed in /usr/share/themes.[/QUOTE]
The theme is installed, but Synaptic for some reason prefers to use another theme. I guess this is Raleigh, but I'm not entirely sure. What I don't know, is how to force Synaptic to use the GTK2 Human theme instead of this other GTK2 theme.

---

### Post by anton.b on 2006-01-20
OK, I've just fixed the second problem too. The solution is actually very plain and obvious. Because you issue the synaptic command with sudo or gksudo, you have to run the gtk-theme-switcher for the root user as well. After running "gksudo switch2" and selecting the Human theme, Synaptic now has the same theme as the rest of the desktop.
Thank you for heading me in the right direction Squalor! ;)

---

### Post by billjoie on 2008-08-26
> **anton.b said:**
> The openoffice.org-gnome-integration package is installed, but appearantly pretty useless when you don't have Gnome itself installed. I did however find the solution to my problem. I just had to set an environment variable "OOO_FORCE_DESKTOP=gnome" and now OOo looks just like in Gnome.


The theme is installed, but Synaptic for some reason prefers to use another theme. I guess this is Raleigh, but I'm not entirely sure. What I don't know, is how to force Synaptic to use the GTK2 Human theme instead of this other GTK2 theme.
Hey anton.b, thanks a bunch for the advice on the environment variable for OpenOffice in IceWM.  How did you figure this out in the first place anyway?  Have you used a similar strategy for other IceWM related problems?

---

### Post by smartboyathome on 2008-08-26
Synaptic is using Root's theme. Just run gksu _insertgtkchangingapphere_ (replacing the long line by your favorite gtk changing app, like gtk-chtheme, lxappearance, or gnome-appearance-properties), and then set the theme using that.

---

