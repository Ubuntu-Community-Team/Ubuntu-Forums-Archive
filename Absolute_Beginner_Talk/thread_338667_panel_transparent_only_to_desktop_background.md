---
title: "panel transparent only to desktop background?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by manutdfan2850 on 2007-01-14
im running ubuntu dapper and i have this issue with my custom panel:

my question: how can I make it so my autohide-transparent panel will be transparent to whatever window is open rather than just the desktop background?  this is just a regular panel that I customized for transparency and autohide.  plz see attachments for an example of what I am saying.

in the first image, I have my firefox window open and i have recalled the autohidden panel. However, its bugging me that this panel isn't really transparent to the firefox window, but rather to the desktop wallpaper.  Is there anyting I can do to achive the effect I am looking for? is this a bug in ubuntu dapper? 

also I do not want to install beryl for hardware reasons (my graphics card sucks balls) 

thanks in advance

---

### Post by po0f on 2007-01-14
manutdfan2850,

AFAIK, you cannot achieve what you want without using Beryl/Compiz.  GNOME's window decorator (Metacity) doesn't include real transparency, only pseudo-transparency.  And even if you wanted to use Beryl/Compiz, for Dapper it means installing the hack that is Xgl (I really don't recommend it).

---

### Post by marx2k on 2007-01-14
I agree with the previous poster.  I think what you're seeing is not 'true transparency' but instead, the bitmap image of your panel is a copy of the slice of background image that the panel occupies, with x% of your normal panel bitmap blended in (in your case, 0%)  So when you move a window over (under) the panel, you'll still just see the background image on the part of the panel.  The same "problem" exists when you set any degree of transparency on the terminal window.  Try setting the terminal window with 100% transparency and then moving another window under it.  You will see your background instead.

---

### Post by MkfIbK7a on 2007-01-14
yes this is normal the panel isnt really transparent as in see through its just a copy of your background.

same thing with a transparent terminal.

wert:D

---

### Post by manutdfan2850 on 2007-01-15
how lame :(

any chance this will be fixed in future versions of ubuntu?

---

### Post by _simon_ on 2007-01-15
That would be a GNOME feature, not an Ubuntu one so it would be up to the GNOME devs I guess.

[http://www.gnome.org/](http://www.gnome.org/)

---

### Post by Zaffe on 2007-01-15
BTW, the "fake-transparency" u can make it in gconf-editor: apps->panel->toplevels->panel_X->background->opacity

---

