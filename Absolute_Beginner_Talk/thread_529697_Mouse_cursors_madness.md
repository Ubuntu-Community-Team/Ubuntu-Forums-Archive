---
title: "Mouse cursors madness"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Ayle on 2007-08-19
Hi, I've just installed feisty and I'm using compiz-fusion and I have a weird problem: my mouse cursor theme keeps changing... Basically if I chose for example the comix theme it'll show up only in the programs I open, if I'm on the desktop it switch back to the default ubuntu theme.... And when I'm in a program when the cursor go into the "working" mode it switch to the theme I was using just before comix and goes back to comix when whatever the computer was doing is done...... Can somebody help me?

---

### Post by Happy_Man on 2007-08-19
And you are changing the theme using the Ubuntu utility for it?

---

### Post by Ayle on 2007-08-20
Yes but the theme keeps changing by itself depending on where the cursor is: desktop, program window or loading-working....

---

### Post by asmoore82 on 2007-08-20
is it a windows cursor theme that is only installed for WINE?

---

### Post by Ayle on 2007-08-20
No they are just the regular x cursor theme:
_when on the desktop: regular ubuntu cursor theme
_when the cursor is in a program window: comix black slim
_when the cusror is in the hourglass state: comix christmas regular

And I haven't installed wine yet.

---

### Post by corney91 on 2007-08-20
have you tried logging out then in again after making a selection? The comix ones could be previews.

---

### Post by Ayle on 2007-08-20
Yes, I've tried restarting x only then i tried restarting the whole pc but still no changes... If I change the cursor theme, the one I choose only appear in the opened program window and the ubuntu default one still shows up on the desktop......

---

### Post by Ayle on 2007-08-22
Anybody?

---

### Post by Lapeth on 2007-08-27
Well, I'm having the exact same problem - to me it seems that the setting of which cursor theme to use is put in several places:

one for desktop & window manager (try holding cursor over the titlebar of a window)
one for running applications
possibly another one for KDE applications in Gnome (e.g. Kile)

It looks like changing the cursor theme only affects some of the above, leaving the others unchanged. I've tried to revert them all back to the default, but I'm still stuck with Comix cursors in some places.

Does anyone know exactly what happens when one tries to change a cursor theme, and where the data is written?

---

### Post by chrome307 on 2007-08-28
I get the same problem at times my mouse cursor is white and at other times it's black.

I'm using a GTK 2.x theme.

---

### Post by Lapeth on 2007-08-29
I think I got it now...

Following a hint I saw at [http://forum.compiz-fusion.org/showthread.php?t=3447]("http://forum.compiz-fusion.org/showthread.php?t=3447"),  I figured that the cursor themer has one definition, and alternatives has another. So the cursor theme should be set in both System->preferences->mouse, and in alternatives:

start galternatives, found in repos, and go to x-cursor-theme
OR
sudo update-alternatives --config x-cursor-theme

Hope it helps

---

### Post by kindofabuzz on 2008-03-25
Here's the solution.  It is compiz switching to the default them when on desktop and panels.  Go to you compiz settings, then general options, and put the exact name of your theme into the Cursor Theme box.  you may have to relog for it to set in.

---

### Post by dr_psikick on 2008-04-30
> **kindofabuzz said:**
> Here's the solution.  It is compiz switching to the default them when on desktop and panels.  Go to you compiz settings, then general options, and put the exact name of your theme into the Cursor Theme box.  you may have to relog for it to set in.

Thanks for this, this was really buging me...

---

