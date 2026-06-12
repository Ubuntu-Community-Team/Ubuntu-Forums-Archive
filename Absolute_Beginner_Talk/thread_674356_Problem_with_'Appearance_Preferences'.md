---
title: "Problem with 'Appearance Preferences'"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by django0909 on 2008-01-21
When I try to run 'Appearance Settings', it won't let me change it to anything other than 'None', i.e. a simple environment with no effects. Running gnome-appearance-properties gives the following:
```
esys@esys-desktop:~$ gnome-appearance-properties
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
No nvidia hardware available
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
esys@esys-desktop:~$ 

```

Assuming I have no nvidia hardware available, I must have something, otherwise nothing would work? And whatever I do have should enable me to alter the appearance settings beyond 'none', surely? There is probably a really simple answer to this, however, I am well stuck.

Anyone? Any help would be great!

EDIT: I am running 7.10!

---

### Post by PeterJS on 2008-01-21
Well, if you don't have a nvidia card, the first thing to do is figure out what card you do have and get the right drivers for it. To find out what card you have open a terminal and run:
```

lspci | grep VGA

```

---

### Post by django0909 on 2008-01-21
Thanks for the speedy reply :) 

This is what comes back....

```
esys@esys-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```

---

### Post by Tenken on 2008-01-21
Find out what video card your running by typing this command

```
lspci | grep VGA
```

and do a google search to see if Compiz supports your card, or alternatively go to System->Administration->Restricted Drivers Manager and that should tell you what card you have. Try installing the restricted drivers, and if that doesn't do anything it is likely your card doesn't support compiz effects.

---

### Post by django0909 on 2008-01-21
It did the same before I started messing with Compiz....

---

### Post by PeterJS on 2008-01-21
The ubuntu wiki is down so i can't confirm this is the case for your card or provide better instructions, but you might try installing xserver-xgl.

---

### Post by django0909 on 2008-01-21
I'll give that a whirl. Cheers :)

---

### Post by django0909 on 2008-01-21
Nope, I still can't change the appearance to anything other than 'none' :(

---

### Post by django0909 on 2008-01-21
Anyone?

---

### Post by Tenken on 2008-01-21
I found this in a post about Ubuntu 7.04, but hopefully it's still applicable.

```
sudo aptitude install xserver-xorg-video-unichrome

sudo dpkg-reconfigure xserver-xorg

```

Then hit Ctl+Alt+Backspace to restart your X server

---

### Post by PeterJS on 2008-01-21
The wiki is back now. This is the page I was thinking of:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
Your card doesn't appear to be on the supported list. If you've got time to burn you might try running through the intel instructions any way, it might work.

---

### Post by spiderbatdad on 2008-01-21
after installing xserver-xgl you must reboot. then try to select "custom"

---

### Post by django0909 on 2008-01-22
Tenken: I tried your method, during reconfiguration I managed to use the wrong 2 letter code for the keyboard, which kept causing it to crash. Worked out what I'd done, and got it sorted. (what is the 2 letter keyboard code for a uk keyboard?)

Anyhow, installing xserver-xgl hasn't worked. Any other ideas, or should I just get a better graphics card?

Cheers to those who have helped so far :)

---

