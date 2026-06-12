---
title: "total system freeze with 11.04 on ASUS U46S"
date: 2011-08-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Argos8 on 2011-08-16
Hi 
this is my first post, and I encountered problems with Ubuntu 11.04 on my ASUS U46S.

After installing I set up bumblebee because the notebook works with Optimus Hybrid inside.
Right after that I updated the system by simply choosing the 'Mark all availiable upgrades' option in the synaptic package manager.
And here the problems start: when I try to boot everything works but as soon I want to login after entering my username and password the system freezes in a way I can only get out with a hardbreak.

Using a backup copy made with rsync before the update works, but only if the home folder was part of the backup. (Restoring backup and trying to login with the 'updated'-home folder causes the same freeze though the rest of the system was restored)

Any ideas what could cause such a 'freeze'-crash?
Thanks for your answers.

EDIT:
Seems like I could get things working by removing xorg packages for ati/radeon (don't know why they where installed), reinstalling nvidia-current and reconfiguring bumblebee.

Though I'm interested which particular constellations could (likely) cause such a 'total-death-freeze' on ubuntu 11.04, any ideas would be very helpful ;)

---

