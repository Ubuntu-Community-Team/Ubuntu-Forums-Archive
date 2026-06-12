---
title: "Theme not applied to scroll bars?"
date: 2006-02-19
forum: Art &amp; Design
---

### Post by chuvisco on 2006-02-19
I've installed several themes from gnome-look, but the scroll bars (and buttons, check boxes, radio buttons, and sliders) are not getting themed.  Everything else is themed as expected.  I have gtk2-engines-pixbuf and gtk-engines-pixmap installed.  What am I missing?

---

### Post by JimmyJazz on 2006-02-20
I am having the same problem.

---

### Post by bvc on 2006-02-20
what themes?

---

### Post by chuvisco on 2006-02-20
[QUOTE=bvc]what themes?[/QUOTE]

For example, 

MacOS-X Aqua Theme
d3a
EdgeGTK
Gno-SX

---

### Post by bvc on 2006-02-20
Strange. From commandline do;
killall nautilus

What version of ubuntu? Have you upgraded? Might need more pkgs. Sounds strange but I just started going dapper and when I upgraded libgnomecanvas2 and depends my engines freaked out. I got more misc pkgs and  they started working again.

---

### Post by chuvisco on 2006-02-20
> **bvc]Strange. From commandline do said:**
> 

This doesn't seem to help--everything just comes back up the way it was before.  

[QUOTE=bvc]What version of ubuntu? Have you upgraded? Might need more pkgs. Sounds strange but I just started going dapper and when I upgraded libgnomecanvas2 and depends my engines freaked out. I got more misc pkgs and  they started working again.

I'm running Breezy with everything up-to-date.  My libgnomecanvas2-0 is ver. 2.12.0-0ubuntu2.

---

### Post by bvc on 2006-02-20
how did you install them and to what directory? Sounds like it could be a permission problem.

Install the themes to .themes, and icons to .icons, in your home directory, and do not use the gnome-theme-manager. Use file-roller to extract them.

---

### Post by chuvisco on 2006-02-20
That doesn't seem to help either.  I had originally installed the themes using gnome-theme-manager, but copying the folders over manually didn't change anything.  Any other ideas?

---

### Post by chuvisco on 2006-02-22
Ok, I've (mostly) figured it out.  I am using Gnome, but I also have KDE (Kubuntu) installed, and at one point I had the gtk2-engines-gtk-qt package installed to manage themes of GTK applications while running KDE.  As it turns out, when this package was installed, I had set GTK applications to use the Human theme.  I later completely removed (or so I thought) the gtk-qt engine, but this setting somehow remained so that I could not change the controls theme.  I could change the window borders and the icon themes, but no matter what I set the controls to, I got Human controls (the sizes of scroll bars and tabs and icons on buttons changed, but that was it).  This was true whether kdm was running or not.  So, what I did was install gtk2-engines-gtk-qt, copy my themes folders over to /usr/share/themes/ (otherwise I didn't have access to them in GTK styles and fonts in Kcontrol), then choose the controls theme I wanted in Kcontrol.  After that, the controls work!

I might try to figure out what is going on if I have time, but for now it's working.

---

### Post by bvc on 2006-02-22
those colors could have been set from a file in yur home dir

usually .gtkrc-2.0 or .gtkrc.mine, or similar

---

### Post by chuvisco on 2006-04-19
[QUOTE=bvc]those colors could have been set from a file in yur home dir

usually .gtkrc-2.0 or .gtkrc.mine, or similar[/QUOTE]

Yes, it looks like gtk2-engines-gtk-qt creates the file .gtkrc-2.0, so deleting it solved the problem.  Thanks!

---

