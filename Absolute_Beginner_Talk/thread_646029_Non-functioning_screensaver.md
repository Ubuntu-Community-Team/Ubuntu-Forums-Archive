---
title: "Non-functioning screensaver?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Mikjoba on 2007-12-20
A small problem, I am unable to get the screensaver function working on my latest installation of Xubuntu (7.10 Gutsy Gibbon on a HP Omnibook 6000), I can start Screensaver settings ok and can preview a whole list of screensavers that all work in preview mode (even full screen) but when I choose one and close nothing happens even when time is set to one minute!
I have checked the forum and also googled this problem, I installed xscreensaver which was discussed in one thread as being the solution but this has not helped, I cannot see any reference to this under applications (Appfinder), although if I do a "locate xscreensaver" i get a long list of files.
I have also seen some reference to problems with screensaver and ATI graphics card, this laptop uses an ATI Mobility M6 but this has not given me any other problems and works well on this laptop.
It is obviously not the end of the world if I don't get this functioning but it would be nice because I would like to use the screensaver lock function once this is running.

Mike

---

### Post by spiderbatdad on 2007-12-20
not sure but i've been having the same problem I just looked at some settings in gconf-editor Apps--Gnome-screensaver  and saw one called lock delay. It was set to 0. Says number of minutes after screensaver is activated to lock the screen. I set it to 10 to see if anything changes.

---

### Post by spiderbatdad on 2007-12-20
> **spiderbatdad said:**
> not sure but i've been having the same problem I just looked at some settings in gconf-editor Apps--Gnome-screensaver  and saw one called lock delay. It was set to 0. Says number of minutes after screensaver is activated to lock the screen. I set it to 10 to see if anything changes.

seems to have had an effect. screensaver came on...first time i've seen it since last upgrade. I've tried to get it working several times with no luck... opps was trying to edit last post...didnt mean to quote myself

---

### Post by Epic Plecostomus on 2007-12-20
HA!  This was the very problem I signed up to discuss!  Thanks!

---

### Post by Mikjoba on 2007-12-21
Did what you recommended "spiderbatdad" but no change it still will not start, doesn't even blink! weird ! got everything else working including wireless network but can't get a simple screensaver function to work!
Any more thoughts?

Mike
PS. Just tested a live cd with Mint Linux and screensaver works perfectly!

---

