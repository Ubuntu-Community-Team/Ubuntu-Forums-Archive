---
title: "Cups Error"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Sq322 on 2006-07-18
Couldnt get anything to print from my printer, so i read a few soultions in here and tried to work it out. Finally i got to where i recieved "Got a couldnt contact cups server error"
After reading another post in the forums i deleted all my cups entries via synaptic and then went to reinstall them
upon doing so i get the following error
> E: cupsys: subprocess post-installation script returned error exit status 1
any ideas

---

### Post by Arisna on 2006-07-18
I would guess that you have some configuration files leftover from the previous installation that are causing problems when you re-install.  I suggest clicking the "Status" button at the bottom of the left-hand pane in Synaptic and seeing if some CUPS stuff is there.  If so, mark it for complete removal, apply changes, and then try to re-install.

---

### Post by Sq322 on 2006-07-18
still getting that error after marking for complete removal

---

