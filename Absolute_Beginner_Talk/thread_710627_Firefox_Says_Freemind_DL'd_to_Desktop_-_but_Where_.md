---
title: "Firefox Says Freemind D/L'd to Desktop - but Where is It???"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by GregA on 2008-02-28
Am having a heck of a time with Gnome's way of viewing and managing files (compared to Konqueror).   I just downloaded Freemind .9-14b from Sourceforge, using Firefox. The file was downloaded to the "desktop" - - but I can't find it anywhere . . . . although I have a "standalone" window showing the contents of the zip file.   

But this window seems detached or not a part of the normal file tree.   Why does Nautilus do this?  It seems I can probably unzip or extract this file, and specify the exact location - - but why can't I just find the zipped file on the desktop, move it first to where I want it, and then do to it what I want (unzip and chmod)???

Does anyone run an alternate file manager in gnome besides nautilus?  Any recommendations?

Just a "dazed and confused' KDE user - - - please guide me . . . . .:confused:

---

### Post by Crooksey on 2008-02-28
In nautauils prefences, you can select an option "always open in same window", this will keep the file manager from opening sevral windows.

---

### Post by GregA on 2008-02-28
Thanks Crooksey,

I finally figured out it was just me, operator error.  I left the check-box selected in Firefox download that put the file to a temp archive.  On the next download, for the programs icons, I changed that selection, and the files were then download to the desktop.   Just a new learning curve for me, but I'm in no hurry, it's interesting to learn new things.

---

### Post by Oldsoldier2003 on 2008-02-28
> **GregA said:**
> Thanks Crooksey,

I finally figured out it was just me, operator error.  I left the check-box selected in Firefox download that put the file to a temp archive.  On the next download, for the programs icons, I changed that selection, and the files were then download to the desktop.   Just a new learning curve for me, but I'm in no hurry, it's interesting to learn new things.
if you ever "lose a file you can always open a terminal and type```
 locate <filename>
``` and you don't need to know the full filename. If locate grumbles at you about the database being too olds you can fix that by typing```
 sudo slocate -u 
``` in a terminal window.

---

