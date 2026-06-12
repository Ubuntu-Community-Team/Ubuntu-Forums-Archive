---
title: "Beryl (Emerald) Theme, Metacity Controls, but no bubble scroll bar?"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by mrdeeno on 2007-01-24
I have had my beryl running on Edgy for the past week now and everything works great.  I started playing around with themes and found that the window controls (buttons, scrollbars, etc) are still controlled through the Gnome theme manager.

I downloaded some themes, and some with "bubble" scroll bars.  But when I install them, the buttons and menus change, but the scroll bars are still rectangular.  I tried doing the same after switching to Metacity in the Beryl manager, but still does not work.

I know I had bubbles for scroll bars at one point when I was on Dapper.  Anyone know how I can get those bubble scroll bars with Beryl under Edgy?

---

### Post by kobewan on 2007-02-17
Try deleting these files:

[http://ubuntuforums.org/showpost.php?p=938126&postcount=11](http://ubuntuforums.org/showpost.php?p=938126&postcount=11)

---

### Post by mcduck on 2007-02-17
GTK2-themes have nothing to do with the window manager. Do you have 'gtk2-engines-pixbuf' installed? Themes using image files need it to work correctly (it's in the Universe repository)

---

