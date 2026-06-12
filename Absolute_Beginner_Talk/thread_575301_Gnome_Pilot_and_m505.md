---
title: "Gnome Pilot and m505"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-13
I'm currently trying to sync my Palm m505 with Gnome Pilot but can't
seem to get it to work. I am running Ubuntu 7.04 through Virtual Box
and think that may have a little to do with it.  However, I have set up
a Filter so that it should be seen within Virtual Box..... I've done
this with other USB devices and it has work sucessfully.
Example: iPod, HP Printer, Various Flash Drives.

It's a USB device so maybe I'm just not doing something right within
Gnome Pilot itself.

It states I am running Gnome Pilot for the 1st time.
I click forward.
I fill in the name box with (My Name) m505
Choose type as USB
Under Device, I've tried them all ( nothing seems to work ).
Speed: 57600

Could someone help me out.

[IMG]http://img87.imageshack.us/img87/6226/00screenshotkb4.jpg[/IMG]

---

### Post by Orbital75 on 2007-10-14
I've tried pretty much all the Device Setting and I still can't get it to recognize
my Palm.  It basically times out and states it couldn't be found.

I know there has to be some Palm User out there that use this software.
PDA's are everywhere now days.

---

### Post by milosz.galazka on 2007-10-14
Long time ago I synchronized palm m505 using kpilot. As I remember I needed  *visor* kernel module.

---

### Post by ayenack on 2007-10-14
Shouldn't that be /media/pilot?
Not sure if this is how it works in gnome pilot or not but if you can change it might be worth a try. There's an app in the repo's called autopilot that's meant to help with syncing palm devices. Also make sure you have gnome-pilot-conduits installed it's also in the repo's. If you type pilot in the search function of synaptic there's a load of apps listed for palm.

---

### Post by rafkin on 2007-10-14
Orbital, had the same problem with a M515. Kept trying different settings and nothing would work. Finally I set it to USB and re-booted. Everything worked after that....not sure why.

---

