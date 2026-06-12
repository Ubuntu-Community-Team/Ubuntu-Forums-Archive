---
title: "The most elegant Metacity theme offering square corners..."
date: 2006-05-23
forum: Art &amp; Design
---

### Post by Dralt on 2006-05-23
I am looking for it... :) Sorry, if you expected a revelation...

What's your favorite?

---

### Post by 23meg on 2006-05-23
It's called [Unity]("http://www.gnome-look.org/content/show.php?content=32167").

---

### Post by Dralt on 2006-05-23
[QUOTE=23meg]It's called [Unity]("http://www.gnome-look.org/content/show.php?content=32167").[/QUOTE]

Thanks for the tip. I'll try it out.

---

### Post by 23meg on 2006-05-23
You're welcome; it's made by bvc who also posts here with the same nickname. It integrates very well with all GTK themes I've tried, especially Clearlooks based ones. It's the thing I'm missing the most with XGL.

---

### Post by bvc on 2006-05-23
woot!
thx!
there's also SystemGX
[http://www.gnome-look.org/content/show.php?content=32169](http://www.gnome-look.org/content/show.php?content=32169)
SystemG
[http://www.gnome-look.org/content/show.php?content=19800](http://www.gnome-look.org/content/show.php?content=19800)
SystemG centered title
[http://www.gnome-look.org/content/show.php?content=32215](http://www.gnome-look.org/content/show.php?content=32215)

---

### Post by bored2k on 2006-05-23
It's not metacity, but I really like Windows' Classic theme :D.

---

### Post by Dralt on 2006-05-24
[QUOTE=bvc]woot!
thx!
there's also SystemGX
[http://www.gnome-look.org/content/show.php?content=32169](http://www.gnome-look.org/content/show.php?content=32169)
SystemG
[http://www.gnome-look.org/content/show.php?content=19800](http://www.gnome-look.org/content/show.php?content=19800)
SystemG centered title
[http://www.gnome-look.org/content/show.php?content=32215](http://www.gnome-look.org/content/show.php?content=32215)[/QUOTE]

You do a great job, bvc. I really like your themes.

Do you know why a lot of themes don't seem to work on Synaptic?

Also, I have come the conclusion that 16x16-pixels icons are a lost cause. Whether your icon is based on a set of bitmaps or a vectorial source, when scaled down to 16x16 pixels, they are likely to look bad.
Reaching this conclusion led me to prefer window title bars that do not display application icons.
I also removed icons in menus.
I am still looking for a way to remove icons from the window list panel component.

Keep up the good work!

---

### Post by Prefader on 2006-05-24
[QUOTE=Dralt]Do you know why a lot of themes don't seem to work on Synaptic?[/QUOTE]

This is because synaptic is run as root, and your themes are most likely stored in your home directory.  You can remedy the situation by copying the theme folder (usually found in ~/.themes/) to /usr/share/themes/

The same works for icon sets (~/.icons/ to /usr/share/icons/).

---

### Post by bvc on 2006-05-24
If you mean 'look bad' in synaptic, no I don't know why. I don't know if it's gdk>gtk (like firefox and oo) or if it is just bad gtk coding.

for the panel icons, I thought this worked (in .gtkrc-2.0 in your home dir)
```
gtk-icon-sizes = "panel-menu=1,1:panel=1,1:gtk-menu=1,1:gtk-large-toolbar=16,16:gtk-button=1,1"
```
and I've done it before but it doesn't seen to be working now. I don't know if its freedesktop naming, Gion icon theme or what...

---

