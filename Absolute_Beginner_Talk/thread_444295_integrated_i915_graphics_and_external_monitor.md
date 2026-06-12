---
title: "integrated i915 graphics and external monitor"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by Anders J on 2007-05-15
I have a laptop with dual head i915 graphics, internal 1280x800 LCD and would like to use this also with a SyncMaster 225BW LCD 1680x1050 60 Hz VGA or other generic projector pixel formats.

The laptop came preinstalled with ubuntu working correctly with the built-in screen and as default the same format is present also on the VGA (however useless for this LCD monitor).

The long term goal would be to ge for dual head, but as a first step I would like to see a proper VGA output for my monitor.

I have read so many posts about how to configure xorg.conf, but they are all different and the sad outcome is that so far every single modification I have done all result in a tty only boot because of invalid data in the conf file. I have tried making small changes (like adding "1680x1050") and I have pasted carefully examined and edited files found here and in various locations, but all failed miserably.

I cannot believe that performing such a simple task can be so enormously complex.

And yes, I do have "915resolution" installed. 

I am now typing my "cd /etc/X11, ls -la, sudo cp xorg.conf xorg.conf_b ..." etc without looking at the note, so at least I am gaining some little linux confidence!

---

### Post by Biochem on 2007-05-17
I have an intel graphic chipset and found that little handy howto to use dual monitor. 

[http://ubuntuforums.org/showthread.php?t=361124](http://ubuntuforums.org/showthread.php?t=361124)

The second screen section in the dual monitor xorg.conf is for the VGA output so if you change that resolution I think you will get what you want.

good luck

---

### Post by ramjet_1953 on 2007-05-17
There is a new Intel driver available in the repositories.

You may want to do a little research on whether it will handle the external monitor, however, as I have never tried it.

To load the new driver, just copy and paste this into a terminal:

[COLOR="Red"]sudo apt-get install xserer-xorg-video-intel[/COLOR]

When it has finished loading, just re-boot.

All available resolutions should now be visible in the resolution selection menu.

Regards,
Roger :cool:

---

### Post by nazgul77 on 2007-06-30
I want to clone my laptop screen to a secondary analog (legacy) display but **with a different refresh rate** of at least 90Hz. I really can't bear the 60Hz flicker any more.

As suggested I did
 [COLOR="Red"]sudo apt-get install xserer-xorg-video-intel[/COLOR]

which instantly puts the secondary (external) display port in clone mode. I don't mind the second screen using the first one's resolution, but I do mind doing it at the same low refresh rate. In Gnome I can select different rates in System->Settings->Screen resolution but they won't work. I guess the internal graphics port (LCD) is locked to 60Hz and hence locking 60Hz for the cloned second port.

Anders J,  I think for different resolutions you will have to go the xinerama way.
perhaps I will have to do the same.

---

### Post by Anders J on 2007-06-30
I haven't looked for this thread for a long time, but through a lot of saerching I found a guy who eventually got it right.

You have to run 915resolution at startup and there is some advanced setup with xorg.conf, but esentially, if you don't make any errors it works!

I am running 1280 x 800 on the internal screen and 1680 x 1050 on the external and I can move the cursor (but not applications) between the two!

---

