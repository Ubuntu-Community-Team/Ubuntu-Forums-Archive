---
title: "Install new icons under Gnome"
date: 2005-02-03
forum: Art &amp; Design
---

### Post by mirtux on 2005-02-03
Hi,
    i'm trying to install new sets of icons under Gnome (Warty). However they didn't appear under the "icons" windows in gnome theme manager. I've tried this with some sets of icons, d3a, exquisite etc. but the problem is the same.
 
 Thanks in advance,
 MC

---

### Post by ctt1wbw on 2005-02-03
This way works for me:

Click on Theme Preferrences, and then Theme Details.  Click on Go To Theme Folder.  Now click and drag the new uncompressed icon folder into the theme folder and they should show up.  :)

---

### Post by mirtux on 2005-02-03
Hi,
   thanks, i've resolved it.. [img]http://www.ubuntuforums.org/images/smilies/icon_wink.gif[/img] . The problem was related to the fact that the procedure created the files in .theme while the theme manager searches the icons files in .icons ----> i've created a symbolic link of the directory where icons are located in .icons directory!
 
 Thanks,
 MC

---

### Post by gabbman on 2005-02-12
[QUOTE=ctt1wbw]This way works for me:

Click on Theme Preferrences, and then Theme Details.  Click on Go To Theme Folder.  Now click and drag the new uncompressed icon folder into the theme folder and they should show up.  :)[/QUOTE]
 I've done that and not all the icons change. None of the toolbar or menu icons, only in running apps.

---

### Post by Gary Powers on 2005-02-13
I'm having a problem finding the locations of .themes and .icons under the file structure.  Would someone be so kind as to aim in the right direction?  Thanks.

Gary

---

### Post by gabbman on 2005-02-13
[QUOTE=Gary Powers]I'm having a problem finding the locations of .themes and .icons under the file structure.  Would someone be so kind as to aim in the right direction?  Thanks.

Gary[/QUOTE]

You'll find them in your /home/(yourname) directory,  If your using nautilus, check the view, show hidden files box.

Now to get the icons to work univerally on the desktop, I had to Move all the files in ~/.icons to ~/.themes
-delete the empty folder ~/.icons
-make a symbolic link from ~/.icons to ~/.themes with
$ ln -s .themes/ .icons

Now all Icon themes work for me.

---

### Post by Gary Powers on 2005-02-13
Thanks ..... I will give it try.

Gary

---

### Post by piedamaro on 2005-02-13
Mmh, it seems a bad mix to me. But if it works...
The point is that "toolbar icons" etc., as you called them, are defined in gtk themes (~/.themes folder), while desktop icons thems are under ~/.icons

---

### Post by bvc on 2005-02-13
that's always been irritating to me. A handful of stock-icons work from an icon theme and the rest have to be done from the gtk theme :roll: 

Is it really that hard to fix? 3+ years now (or so) they've been broken! :x

---

### Post by Gary Powers on 2005-02-13
Gabbman:

Found 'em and thanks.  I had forgotten about the hidden files.  I can probably figure out how to get what I want by playing around with them.

Gary

---

### Post by piedamaro on 2005-02-13
[QUOTE=bvc]that's always been irritating to me. A handful of stock-icons work from an icon theme and the rest have to be done from the gtk theme :roll: 

Is it really that hard to fix? 3+ years now (or so) they've been broken![/QUOTE]
I have to agree, and btw nice themes bvc! Actually I use "edge" :)

I remember it was a 'feature' added ad hoc to make icon themes and gtk feel more integrated, when at that time, toolbar icons were part of 'nautilus-icon-theme'. Thus they made icon-themes (which control mime-types icons), and gtk-themes which control "application icons" .
So we need a regression...I suppose :D

---

### Post by kh4nh on 2005-02-21
Hey Gabbman, is there any diffrerent between "ln -s .themes/ .icons" and "ln -s .themes .icons" - thanks

---

