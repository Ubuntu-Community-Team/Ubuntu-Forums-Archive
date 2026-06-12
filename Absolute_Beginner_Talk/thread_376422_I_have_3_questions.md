---
title: "I have 3 questions"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Einherjer on 2007-03-04
Hello,

I just installed ubuntu ultimate edition. Since i first used the live cd, everytime i boot my computer i get an error. NTRDL is missing. My workaround is to have the windows CD in the tray. How can i fix this?

I need ATI drivers, where can i get them and i haven't used linux for 2 years so i might need some directions as of how to install them.

and finaly, i need drivers for my x-fi fatal1ty cards...where could i get them? thanks!

---

### Post by igknighted on 2007-03-04
1) Is this a windows error?  If so I can't help, haven't used it in forever.

2) Part of me believes that Ubuntu Ultimate might have installed them already (it's not an offically supported Ubuntu distribution so I have no idea what they include).  If they are definitely not installed, try this:
```
sudo aptitude update
sudo aptitude install xorg-driver-fglrx fglrx-control
sudo aticonfig --initial
```
then restart.

3) Drivers should be included with the kernel.  SB does not make linux drivers to my knowledge.  Most basic SB cards work, but many of the nicer ones have issues.  Do an extensive forum search to find info on your specific card.

---

### Post by Einherjer on 2007-03-04
Thansk for the fast response. I don't know if it's a windows error. It's just there unless i have a windows cd in the tray and then grub starts and everything else is fine.

omg i don't even know where is the console on gnome, i'm used to KDE lol how can i access the hdd? whats the equivalent of konqueror on gnome?

i just installed the ati drivers using the add/remove tool, everything is smoother now!

i'll search forums for x-fi fatality drivers thanks

---

### Post by igknighted on 2007-03-04
> **Einherjer said:**
> Thansk for the fast response. I don't know if it's a windows error. It's just there unless i have a windows cd in the tray and then grub starts and everything else is fine.

omg i don't even know where is the console on gnome, i'm used to KDE lol how can i access the hdd? whats the equivalent of konqueror on gnome?

i just installed the ati drivers using the add/remove tool, everything is smoother now!

i'll search forums for x-fi fatality drivers thanks

Terminal is in applications->accessories->terminal
Nautilus is the default file browser (and compared to konqueror it sucks)
Firefox is the default web browser (and aside from plugins like mouse gestures, it sucks too when compared to konqueror)

EDIT: if you want KDE, try "sudo aptitude install kubuntu-desktop" to install everything the ubuntu KDE release comes with, or "sudo aptitude install kdebase" to get just the stock KDE stuff.

---

### Post by Einherjer on 2007-03-04
Well i seem to be screwed, no sound is not cool. back to windows i guess, too bad i loved this...so much better than mandriva 2 years ago. Beryl is awesome!

Thanks for the help.

---

### Post by igknighted on 2007-03-04
NP.  No Mobo sound?  My mobo sound is hi-def and everything so I ditched my SB card (sold it actually ;-)).  You might wanna look into the same.

---

### Post by Einherjer on 2007-03-04
I paid almost 400$ for that card and loved the crystalizer so...i'll have to wait until it is supported. Damn i was about to ditch windows for good tonight lol

---

