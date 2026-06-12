---
title: "Removing VMplayer corrupted environment"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by ericmarceau on 2007-04-29
I installed, tried, then removed VMplayer.

Afterwards, all the "*.desktop" files are not being interpreted properly.
Double-cliking them simply opens for editing, not initiating the actions or,
in this case, showing the root file system icon on the desktop or allowing
me to righ-click and select browse folders.

Can anyone tell me what needs to be "reset"?

Thank you,


Eric

---

### Post by ericmarceau on 2007-04-29
Another indication of how far this might go, when I choose
   System / Help / System Documentation,
if I click on one of the links, it only pulls up an xml file
in text editor, it does not initiate the action of retrieving
and displaying help, as before.

---

### Post by ericmarceau on 2007-05-01
PROBLEM: 
  - *.destop files not being interpreted correctly
  - actions or URI not properly initiated

SOLUTION:
After looking at many things (including re-install of Gnome, GnomeVFS, mime), the problem was resolved by re-installing Nautilus-related packages then re-booting.

STATUS: closed


Eric

---

