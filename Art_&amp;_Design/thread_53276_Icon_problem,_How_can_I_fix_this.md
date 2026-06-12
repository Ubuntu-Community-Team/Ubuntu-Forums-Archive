---
title: "Icon problem, How can I fix this?"
date: 2005-07-30
forum: Art &amp; Design
---

### Post by PrimoTurbo on 2005-07-30
[http://img325.imageshack.us/img325/2647/screenshot3ex.jpg](http://img325.imageshack.us/img325/2647/screenshot3ex.jpg)

I installed this icon theme but for some reason this theme and many others miss this icon. I think it's some bug or something. Here is how it should look.

[http://www.gnome-look.org/content/preview....ion2+Icon+Theme](http://www.gnome-look.org/content/preview....ion2+Icon+Theme)

Any idea what I can do? Thanks

---

### Post by varunus on 2005-07-30
This looks like graphite/gperfection2 by lokheed.  There's a bug with his themes for some reason; you need to use gedit or sudo gedit to open up the index.theme file, make a change, save, undo the change, and save.  Its a weird quirk that happens for some reason.

---

### Post by PrimoTurbo on 2005-07-30
[QUOTE=varunus]This looks like graphite/gperfection2 by lokheed.  There's a bug with his themes for some reason; you need to use gedit or sudo gedit to open up the index.theme file, make a change, save, undo the change, and save.  Its a weird quirk that happens for some reason.[/QUOTE]

I know I read his comment and have done this before I used the theme, I even tried sudo gedit just now, reloaded the theme and still nothing. I'll try to reboot but I doubt that will help. Any more ideas? Most themes work poorly on that toolbar and ussually miss the forward backward and computer button. The only one that didn't miss anything was the gant based one. Anyway, more help would be appricated. Thanks for trying. :)

---

### Post by varunus on 2005-07-31
Some icons actually are in the gtkrc file, not the icon's theme.  This may be the case with this icon.  Does the graphite clearlooks theme (or gperfection2, not sure which one you're using) fix the icon problem for you?  If it does, you can modify the theme you're using to use graphite/gperfection stock icons pretty easily.

---

### Post by bvc on 2005-07-31
killall nautilus

---

### Post by PrimoTurbo on 2005-07-31
Works now, thanks guys. :)

---

