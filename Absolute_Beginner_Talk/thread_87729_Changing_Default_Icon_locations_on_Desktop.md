---
title: "Changing Default Icon locations on Desktop"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by Third Thoughts on 2005-11-08
Is it possible to change the location where Breezy puts new icons on the desktop? I happen to have my gdesklets RSS feed sitting right on top of the spot. I don't like have to constantly move it whenever I download something to my desktop or mount a new drive.

~Andrew S.

---

### Post by eyebrowman92 on 2005-11-08
well youll have do deal with it. ive tried but i cant figure it out. i thought linux was made for lazy people. guess not.

---

### Post by endersshadow on 2005-11-08
I've looked through the configuration editor, but I can't find anything.  As a note, Nautilus handles drawing icons on the desktop.  Linux itself has nothing to do with it.

I'll keep looking, but in an attempt to narrow your search, you're going to want to figure out how Nautilus draws icons to the desktop...I'll look at some text configuration files...

---

### Post by emarkay on 2006-10-09
One year later - anyone found how to beat Window$ and let you arrange and keep Desktop Icons where you want them?

---

### Post by CatKiller on 2006-10-09
> **emarkay said:**
> One year later - anyone found how to beat Window$ and let you arrange and keep Desktop Icons where you want them?

You can do that easily. You click it and you drag it, just like in Windows.

AFAIK, Nautilus defaults to putting **new** icons in the top left-hand corner of the Desktop. Oh yeah, just like Windows.

---

### Post by tweedledee on 2006-12-29
> **emarkay said:**
> One year later - anyone found how to beat Window$ and let you arrange and keep Desktop Icons where you want them?

Nautilus simply does not have this option - basically, it's a very good desktop manager lacking a couple of key features.  If keeping your icons arranged and organized is more important than some of the other functionality that Nautilus provides, you can change your desktop manager.  To do this, run gconf-editor (may be hidden on your menu, if so run in a terminal), go to apps/Nautilus/preferences, and uncheck "show desktop."  Then install xfdesktop4, which is the XFCE desktop (which I know has better icon behavior, you could also look for other desktop managers).  If you then run xfdesktop (you can add it to your startup programs), it will manage the desktop.  xfdesktop works on a grid system, so everything is always aligned, and keeps icons in the same positions by assigning them to a "cell."

Disadvantages to this technique include the need to tell the desktop manager to use nautilus for browsing folders, and the quirks that come with your new desktop manager.  You can experiment and see which works best for you.  Personally, as much as it irritates me that Nautilus can't arrange icons worth squat, I've still found it to the best desktop manager for my needs - I just keep the desktop mostly clean so not too much gets buried.

---

