---
title: "gtkrc vs a theme with a file of .png files?"
date: 2007-07-04
forum: Art &amp; Design
---

### Post by xl_cheese on 2007-07-04
I've tried to edit a gtkrc file to alter a theme.  I copied the theme and played with the copy.  However, My changes do not do anything.  Do I need to compile it somehow?  I see there's a index.theme file.  Do I need to do anything with that?

I am just dragging a dropping my theme folder into the theme selector window.  Even tho I changed the folder name the theme still shows the original name in the theme gui.

Another question.  I found a theme on gnome-themes and downloaded it.  This this is different from the default themes already installed.  It is just a file full of pngs.  When I alter those images I do see changes to the theme.

I'd like to figure out how to make my gtkrc edits take place.  Can anyone point me in the right direction?

---

### Post by Hairy_Palms on 2007-07-04
it all depends on the engine that the theme uses, the default gnome engine is clearlooks, which uses colours and calculations to draw windows, whereas a lot of home-made themes use the pixmap engine which just uses pictures for its theming, i must confess though i have no idea how to edit non-pixmap based themes.

---

### Post by bvc on 2007-07-04
DO NOT delete an index file from an icon theme!

DO delete (or edit, or recreate) an index file when creating a new theme from a copy. The theme manager sees two itentical index files, regardless of which one it sees it is going to use the gtk theme written in that file, not your new modified theme.

Oh...
-you don't need to compile
-dropping a directory onto the theme manager does nothing.

[http://art.gnome.org/faq.php](http://art.gnome.org/faq.php)
[http://live.gnome.org/GnomeArt/Tutorials](http://live.gnome.org/GnomeArt/Tutorials)

---

