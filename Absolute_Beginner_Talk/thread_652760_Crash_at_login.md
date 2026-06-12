---
title: "Crash at login"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by DrakenMagnus on 2007-12-29
I'm building a new computer, and have decided to go ahead and install Ubuntu 6.10 Gusty. Everything has been installed correctly, but the issue occurs whenever I try to load anything graphically, the screen completely freezes and I am unable to do anything but restart.

I can't access the settings tab in options under the login menu, nor can finish logging in. My system specs are:

XFX 680i SLI LT Motherboard
GeForce 7800 GT OC 256mb
Intel Core 2 Duo 3.0MHz (64-bit)
Maxtor 160GB HDD

Any suggestions?

Also as a second question, I am currently running one GeForce 7800, and am curious if Ubuntu Gusty will support SLI  if I decide to add a second card later?

---

### Post by overdrank on 2007-12-29
> **DrakenMagnus said:**
> I'm building a new computer, and have decided to go ahead and install Ubuntu 6.10 Gusty. Everything has been installed correctly, but the issue occurs whenever I try to load anything graphically, the screen completely freezes and I am unable to do anything but restart.

I can't access the settings tab in options under the login menu, nor can finish logging in. My system specs are:

XFX 680i SLI LT Motherboard
GeForce 7800 GT OC 256mb
Intel Core 2 Duo 3.0MHz (64-bit)
Maxtor 160GB HDD

Any suggestions?

Also as a second question, I am currently running one GeForce 7800, and am curious if Ubuntu Gusty will support SLI  if I decide to add a second card later?

HI and welcome, you can try and boot into recovery mode which is usually the second choice in the grub. The reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by DrakenMagnus on 2007-12-29
Still locks up whenever I try to access the desktop.

---

### Post by overdrank on 2007-12-29
> **DrakenMagnus said:**
> Still locks up whenever I try to access the desktop.

Ok lets change it up a bit. Boot back into recovery mode then try the command ```
startx
``` and see if this get you to the GUI.

---

### Post by DrakenMagnus on 2007-12-29
I've tried starting X before, it just loads a blank screen in black and white, with an X as the cursor, and freezes.

=/

---

### Post by overdrank on 2007-12-29
> **DrakenMagnus said:**
> I've tried starting X before, it just loads a blank screen in black and white, with an X as the cursor, and freezes.

=/

Ok have you tried reconfiguring the xorg from recovery mode with this command 
```
sudo dpkg-reconfigure xserver-xorg
``` and choose vesa for the driver.

---

### Post by DrakenMagnus on 2007-12-29
Indeed, currently I'm re-installing Ubuntu to see if I have more luck.

Edit: Just finishing reinstalling, and everything seems to work fine now ^_^

Edit of an edit: Nevermind, more of the desktop loaded (icons, toolbars etc) but it promptly froze yet again. Back to the drawing board.

---

### Post by FakeOutdoorsman on 2007-12-30
Check your x-server log at /var/log/Xorg.0.log or go to System -> Administration -> System Log.  List any lines that are preceded by (EE).

Did you try loading a LiveCD to see if it crashes at Gnome loading?

---

### Post by Dr Small on 2007-12-30
With 256MBs of RAM, that could present to be a problem...

---

### Post by overdrank on 2007-12-30
> **Dr Small said:**
> With 256MBs of RAM, that could present to be a problem...

Hi and I am assuming that is memory for graphics card.

---

### Post by Dr Small on 2007-12-30
> **overdrank said:**
> Hi and I am assuming that is memory for graphics card.
Ooops. Sorry there, my mistake.
Your right overdrank, that is from the graphics card.

---

