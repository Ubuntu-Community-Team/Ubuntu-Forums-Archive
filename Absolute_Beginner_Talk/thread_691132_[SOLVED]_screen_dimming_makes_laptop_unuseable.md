---
title: "[SOLVED] screen dimming makes laptop unuseable"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by jonnywombat on 2008-02-08
I have just brought a new HP G6000, and installed ubuntu 64bit onto it (AMD 64 dual core, nvidia geforce go7000 2gb ram).

On the whole this has been easy enough. I had some issues with the screen saver previews causing the whole system to freeze, so last night I fired up synaptic, searched for the term screen saver uninstalled all installed packages then only installed gnome screensaver and electric sheep.

This cured my freezing issue and I fiddled with the power management settings. I unchecked the boxes for dimming when idle and set both sliders to 100%

I then used the system fine (on battery) then went to bed, leaving the laptop to charge.

I fired up the lap top this morning on battery power, and as my desktop finished loading the whole lot dimmed and was so dim it was unusable..I restarted on mains power and all was ok for a few moments when the desktop loaded, but again while looking at the power settings and trying to work out what is happening it all went dim..

Once it goes dim I am unable to make it light again, either by moving the mouse or use of the shortcut keys on my laptop (although the box with the brightness level meter is appearing on screen (although it is too dark to make out if the bar is moving!))

If i restart the machine without powering off in the middle (remove battery and power leave for 30secs and then reboot) the the screen even remains dimmed during the boot process, if it has been powered down then on batery it goes dim during boot and on mains it dims during the loading of the desktop. 

However live CD works just fine and I am typing this from the same machine running on the live CD!!!

Any ideas on how to fix this (I guess removing Gnome screensaver would ba a work around for now), but remember that once off the live cd I will not be able to see what I am doing!!!

I really want to aviod a full reinstall, coz that would be 3 in 3 days (once to get rid of vista and once coz I made a noob error when altering partition sizes!!)

Pls Help as I am in the dark here in more ways than one

Jonny

---

### Post by rufius on 2008-02-08
Setting the power management settings to dim 100% will dim your screen... 100%. You need to modify that setting so that it its something like 60% or whatever you choose. Either way, its what you did to power management thats causing this,

 I don't really like the feature and like to control my own dimming/brightening so I just disable the dimming altogether.

Hope that helps :)

---

### Post by jonnywombat on 2008-02-08
Thanks mate..
  
I have. found there is definitely a bug with the dimming feature and my hardware. On the live cd i can manually dim the screen but it will not brighten again, although the slide goes up and down!!

I have managed to fix my main install but adopting the settings you suggested. to do this I had to use a bright torch in a darkened room to illuminate my screen enough to see what i was doing. I have all brightness settings at 100% with no turn off of screen etc..

So far so good running on mains.. will have to see what happens when I run on batery..

Thanks again

Jonny

---

