---
title: "[SOLVED] Need help fast, screwed up video..."
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Shadows_Fall on 2007-08-09
I tried setting my color depth to 32, and it screwed up my video, so I need someone to help me restore my xorg.conf to 24.

I have a live cd in my drive, but I can't figure out how to get into my HDD...
So could someone please explain to me how I can give myself permissions to edit my xorg.conf?

I tried su and sudo me:me /etc/X11/xorg.conf but both just gave me errors...

Thank you for your time.

---

### Post by AlexenderReez on 2007-08-09
just enter terminal

> gksudo gedit /etc/X11/xorg.conf

incase it is in critical situation just reconfigure it....


> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Dedoimedo on 2007-08-09
Hello,

You don't need a live CD. Boot without graphics (failsafe mode).
Login, then try:

sudo dpkg-reconfigure xserver-xorg.

This will present you with a step-by-step wizard. Choose your settings, save, restart the X server using

sudo /etc/init.d/gdm restart (gdm for gnome, kdm for kde).

The biggest problem you might have are the settings, but they are fairly simple. Choose mouse, keyboard, resolution etc - all these should remain the same, just go through until you reach color depth.

Regards,
Dedoimedo

---

### Post by Phosphoric on 2007-08-09
Re-boot with your live CD and select safe mode.

Then you should be able to get in to the terminal and reconfigure xorg.

Code:  sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Shadows_Fall on 2007-08-09
Hmm... No luck... I reset it back to 24 bit, but now it says my video driver is wrong...
So I guess I have to waste another 2 hours installing it again.

Thank you for the help.

---

