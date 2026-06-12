---
title: "USB device, iPod, CD/DVD weren't automounting - now they are"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by jcconnor on 2007-06-14
I've been having a problem for the last few weeks with my USB devices, my iPod, and my DVD writer not automounting when I plugged something in or inserted a disc.  These had been working fine for about 6 months - no problems.  I did some searching on the forums and saw that other users were having a similar problem.  It sounded like a recent update may have borked something for some folks (myself included).  

I did a work-around for the iPod (mostly to get my son off my butt about not being able to add tracks to his Pod) and kinda poked around some more to see if somebody had a fix or knew what was going on.

To make a short story longer, a thread (don't remember which one now) mentioned using usbmount from the repositories to fix a similar issue.  When I checked that out the description mentioned hal and pmount.  So, I searched the Package Manager and looked through the description of some of those to see which ones looked relevant.  

I checked these for reinstall:

gnome-volume manager
hal
hal-device-manager
kdebase-kio-plugins
libhal1
libhal-dev
libhal-storage1
pmount

Rebooted my machine after those had finished and plugged in a USB device.  Fixed!!  Plugged in the iPod.  Fixed!!  Dropped an audio cd and blank DVD into the drive.  Both automounted and worked the way I was expecting.

Not sure if I needed to reinstall all of them but it fixed the problem for me.  Of course you're mileage may vary.

John

---

### Post by abburdlen on 2007-06-14
Sound like exactly my problems as well, can you walk complete newbie through the fix?
Do I need to uninstall and reinstall the packages you mentioned or is there a way reinstall other than through add/remove applications?

---

### Post by jcconnor on 2007-06-15
Click on System, Administration, Synaptic Package Manager.

Enter your password, then click on Search.

Type hal and then hit enter.

All of the packages (plus a bunch more) will be listed that are related to your search.

On my system all the packages I had listed already were installed and had the box greened in.  Yours may be different but that's ok, we'll install them new if they aren't already.  I did not have to uninstall them, in fact I would not uninstall them first as they are critical system components and your system will likely crash and you will have a bad day.  Or day and night depending on how long it takes you to recover.  Plus you will hate me and cuss me out and all my good karma will go away.  Do not uninstall them.

Highlight each of the package names that I have listed and then right mouse click on them.  Select Mark for Reinstallation.  Go to the next one on the list.  If for some reason they are not currently installed (little box is blank - not green) select Mark for Installation.

When you have selected them for either installation or reinstallation click Apply.

They will be downloaded and will install.  After the installation a pop-up will pop-up saying that the system requires a reboot.  Remember the critical system part from above? - that's why the reboot is required.

After the reboot, it fixed my problems.  Hope it does the same for yours.

John

---

