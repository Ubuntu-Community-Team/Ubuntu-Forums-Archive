---
title: "Installed Feisty, then Beryl, then removed Beryl, now cube w/ desktop effects no work"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by naked on 2007-04-21
So I installed Beryl to check it out, didn't like it much, and wanted to go back to the regular desktop effects.  But now the cube effects won't work.  I can't rotate anything, but I can scale windows.

Any thoughts?  I completely removed everything I Installed with Beryl, and I restart X a few times.

?

L

---

### Post by desheikh on 2007-04-22
Other than installing beryl did you make any configuration changes anywhere.. ?
check if compiz is installed or try reinstalling it..

---

### Post by naked on 2007-04-22
Compiz is still installed.  I reinstalled it.  All the other effects work, just not anything related to the cube.

Is there some settings I should check in the configuration editor?

Luke

---

### Post by superdexter on 2007-04-22
I'll be watching closely.  Exact same thing for me. 
WORKING:
wobble windows
3d effect of shading.
annotate (super+alt+button1)

NOT WORKING:
cube rotation (ctrl+Alt+Button1)
unfold (ctrl+Alt+down)
window carry on rotation (shift+ctrl+alt+left/right)

I've been looking in the gconf-editor and the hotkeys are set correctly.  They just dont work. 

I enabled the ati drivers, then turned them off when the effects didn't work.  Any suggestions, I'll be watching closely.

Cheers,
superdexter

---

### Post by naked on 2007-04-22
The only other thing that works for me is scaling (Ctrl + Alt +Up)

As a side note, how do you clear the annoting?

I have red scribbles that won't go away!

L

---

### Post by superdexter on 2007-04-22
super+ctrl+k  = clear red lines ;)

---

### Post by superdexter on 2007-04-22
Agreed, scaling works.

On a side note.  When everything was happy (before ati drivers) when I used Alt+Tab it looked normal.  Now the desktop scales down a little bit when it shows the preview windows.  Just in case it gives anyone a clue where to look for this beastly problem.

---

### Post by superdexter on 2007-04-22
Additionally, dragging window onto next workspace is broken.

---

### Post by Stickymaddness on 2007-04-23
I have had the same problem on both my pc and my laptop. 

Installed Feisty, window effects 3D cube works, log on again later, window effects work but not the 3D cube.

As far as I've seen there have been allot of posts from people having problems with Feisty + Beryl/Desktop Effetcs.

---

### Post by Tikhon on 2007-04-23
I've had same problem, but when I've customized compiz with gnome-compiz-preferences (gnome-compiz-manager package) all has falled into place.

---

### Post by superdexter on 2007-04-23
YES....gnome-compiz-manaager package fixed it all.   Awesome Tikhon!!!!  Thanks.

btw...your english is fine.

Cheers,

---

### Post by Stickymaddness on 2007-04-23
The gnome-compiz-manager has fixed my 3D cube problem - Thanks for that info! However, I still have no window borders, for both compiz and Beryl, no matter what window decorator or window manager I use :confused:

Edit: I fixed my problem with the post at [http://ubuntuforums.org/showpost.php?p=2513943&postcount=4]("http://ubuntuforums.org/showpost.php?p=2513943&postcount=4")

---

