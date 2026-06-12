---
title: "preformance tweaks?"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Riffer on 2008-01-28
[SIZE="2"] At school I'm experimenting with 2 older machines, (1.6ghz intel. 256 RAM).  And while Ubuntu runs fairly well on them, I would like to  optimize their performance without losing the ease of the Gnome desktop.   

I know I can go to another window manager like enlightenment which I've tried .  Is there any others that could help?                                                                     [/SIZE]

---

### Post by Perfect Storm on 2008-01-28
Well, one of the tings is to install **bum** and remove all the laptop stuff if you're on a stationary computer.

Change firefox out with epiphany browser

Remove some of the stuff in panels.

---

### Post by Riffer on 2008-01-28
> **Artificial Intelligence said:**
> Well, one of the tings is to install **bum** and remove all the laptop stuff if you're on a stationary computer.

Change firefox out with epiphany browser

Remove some of the stuff in panels.

I looked in the repos for burn and it says its a command line cd burner, what am I missing.  And removing laptop stuff, would I use synaptic do a search and remove anything related to laptops?

---

### Post by igknighted on 2008-01-28
> **Riffer said:**
> I looked in the repos for burn and it says its a command line cd burner, what am I missing.  And removing laptop stuff, would I use synaptic do a search and remove anything related to laptops?

BUM, not BURN (caps added to distinguish letters).  It stands for "boot up manager" IIRC.  This lets you turn of all sorts of stuff that you don't need.  Search the forum, as I am not sure it is in the repo's, but last I checked the project had its own subforum here.

---

### Post by Perfect Storm on 2008-01-28
It's in the universe last I checked.

---

### Post by igknighted on 2008-01-28
> **Artificial Intelligence said:**
> It's in the universe last I checked.

Thanks, AI... No Ubuntu at work, couldn't check from here ;)

---

### Post by Riffer on 2008-01-28
LOL sorry the eyes ain't what they used to be.

---

### Post by JoshuaRL on 2008-01-28
I just tried that.  Nice.

---

### Post by mcduck on 2008-01-28
Press Alt-F2 and run gconf-editor. Then do the following changes:

1. Enable apps/metacity/general/reduced_resources
2. Turn off apps/panel/global/enable_animations
3. Turn off desktop/gnome/interface/enable_animations

These changes will disable many animations in Gnome, and hide window contents when moving windows. You'll probably find the desktop to be more responsive this way.

Apart from those tweaks, use only those panel applets you _really_ need (no deskbar!), and try to find lightweight replacements for the programs you use. Abiword & Gnumeric instead of OpenOffice, Epiphany instead of Firefox, MPD and Sonata/ncmpc instead of Rhythmbox/Amarok and so on..

The system should be quite usable with those specs, I'm actually running Gnome on a machine with 500MHz K6-2 and 128MB of memory..

---

### Post by Riffer on 2008-01-28
[SIZE="2"]Great tweaks, I've just tried BUM and what a cool app, I'll post my output  for the 2 machines later, perhaps someone can give me an idea of which processes I can turn off.                                                         [/SIZE]

---

