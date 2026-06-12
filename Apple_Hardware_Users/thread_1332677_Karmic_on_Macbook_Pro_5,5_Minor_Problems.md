---
title: "Karmic on Macbook Pro 5,5: Minor Problems"
date: 2009-11-20
forum: Apple Hardware Users
---

### Post by ringo999 on 2009-11-20
Hi,

I'm running Ubuntu 9.10 on a Macbook Pro 5,5 works great except:

- from the indicator applet in the gnome panel choosing suspend/hibernate will result in activation of screensaver instead of s2ram/s2disk. However, triggering s2ram manually form bash works. I followed some scripts to extend my battery running time (latop-mode, 99-savings), maybe something there went wrong with the mapping?

- pressing F1 for dimming the screen brings up "Shut Down the Computer screen". I can use the Power Manager Bright Applet in the gnome panel to dim down, but only after maxing the brightness using F2. Where to correct this mapping?

Thanks for your help

// Ringo

---

### Post by Who on 2009-11-20
> **ringo999 said:**
> Hi,

I'm running Ubuntu 9.10 on a Macbook Pro 5,5 works great except:

- from the indicator applet in the gnome panel choosing suspend/hibernate will result in activation of screensaver instead of s2ram/s2disk. However, triggering s2ram manually form bash works. I followed some scripts to extend my battery running time (latop-mode, 99-savings), maybe something there went wrong with the mapping?

- pressing F1 for dimming the screen brings up "Shut Down the Computer screen". I can use the Power Manager Bright Applet in the gnome panel to dim down, but only after maxing the brightness using F2. Where to correct this mapping?

Thanks for your help

// Ringo

How did you install things? Are you dual booting? I ask because I just couldn't get the grub bit to work installing Karmic directly (I also have a MBP5,5). I had to install 9.04 first and then upgrade.

The other curiosity is that I don't have the same problem with the dimming :S I can use the F keys as they are intended. What does it do if you hold down Fn first? If that works properly than you can change the mode of the F keys

Oh - did you set your keyboard layout to 'Macintosh'? I have selected gb - Macintosh as my kb type.

---

### Post by ringo999 on 2009-11-21
That's right, I upgraded from 9.04.

The keyboard is set to "USA Macintosh" with keyboard model "Apple".

When I try to change the keyboard model to i.e. Macbook/Macbook Pro (Intl) I get the following error message:

[I][FONT=System]Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10604000[/FONT][/I]

---

### Post by DizzyTech on 2009-11-22
The 99-savings script is causing your standby screwups.  Believe me, I reinstalled to find out.  Remove it and you'll be fine.

For the FN keys, look in the Wiki guide (just Google MacBookPro5,5 Karmic) for the pommed details, just tweaking a config file.

---

### Post by ringo999 on 2009-11-22
you were right about 99-savings. trying to fix that issue now at 

[http://ubuntuforums.org/showthread.php?t=1215928](http://ubuntuforums.org/showthread.php?t=1215928)

in my keyboard shortcut preferences i found had found mapping for "log out -> XF86MonBrightnessDown", no idea how it got there.

I erased the mapping and restarted pommed, but still dimming brightness down won't work. 

I looked in pommed.conf, but I couldnt really see where/how keys are mapped...

:-(

---

### Post by DizzyTech on 2009-11-22
Have you installed nvidia-bl-dkms and NOT nvidia-bl-mbp-dkms?  Make sure the latter is not installed, it doesn't work well on MacBookPro5,5 w/ Karmic.

---

### Post by ringo999 on 2009-11-22
thanks for the hint, i do have the correct one installed though.

---

