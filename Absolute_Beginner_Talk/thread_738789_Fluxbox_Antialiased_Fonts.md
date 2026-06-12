---
title: "Fluxbox Antialiased Fonts?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by flux_user on 2008-03-29
Hello,
I have a question about getting antialiased fonts working in Fluxbox.  Here is the crux of the issue:

As of Fluxbox 0.9.14 font handling was modified to use .Xdefaults.  

[I]"Removed "antialias"-option completly, to enable/disable "antialias"
use either  :antialias= in the style or use Xft.antialias:  in your .Xdefaults"
[/I]
[http://fluxbox.org/version-0.9.php](http://fluxbox.org/version-0.9.php)

I have several entries in .Xdefaults; however those  entries are not being read.  I know that .Xdefaults is being read; because other entries have  taken effect.  These are the  entries that I wish to enable.

Xft.dpi: 96
Xft.antialias: true
Xft.hinting: true
Xft.hintstyle: hintfull
Xft.rgba: rgb

Any thoughts; opinions, suggestions would be greatly appreciated.

---

### Post by flux_user on 2008-03-29
Actually I have the  answer with respect to other  fluxbox users; as well as other  users.  I have done two changes:

1) ~/.Xdefaults
[LIST]
[*]xrdb -merge -load: ~/.Xdefaults
[*]Xft.dpi: 96
[*]Xft.antialias: true
[*]Xft.hinting: true
[*]Xft.hintstyle: hintfull
[*]Xft.rgba: rgb
[/LIST]

2) dpkg-reconfigure fontconfig-config
[LIST]
[*]Font tuning method on screen: Autohinter
[*]Enable subpixel rendering for screen: Automatic
[*]Enable bitmapped fonts by default: Yes
[/LIST]

Now your fonts should be working in menus and applications.

---

### Post by kerry_s on 2008-03-29
[http://fluxbox-wiki.org/index.php/Style_overlay](http://fluxbox-wiki.org/index.php/Style_overlay)

---

