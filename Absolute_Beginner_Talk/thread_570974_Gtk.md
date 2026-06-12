---
title: "Gtk"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by wil313 on 2007-10-08
Ok, I'm having horrible luck... Can someone please tell me how to install a GTK theme? *here is the specific gtk theme I'm trying to use*

[http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438](http://www.gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438)

---

### Post by wil313 on 2007-10-08
Anybody?

---

### Post by Faud on 2007-10-08
I copied this from the link you provided

Installation:
--Gtk 2.10+ is required for this engine.
--Includes both the GtkRc themes, and the theme engine.

To install the theme engine extract it to somewhere convenient and in that directory,
run: "./configure --prefix=/usr -enable-animation" then "make".
Then as a root user "make install".

Then install the gtkrc themes by extracting them to your ~/.themes directory (3 themes in total).

What exactly is happening when you try this ?

---

### Post by macogw on 2007-10-08
Um well that says theme engine, not just theme, so I'm not sure.  To install a theme, though, drag the theme's tarball into the choosing area of system > pref > theme (i think that's where it is...sorry, i'm using gutsy so things moved a bit)

---

