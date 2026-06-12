---
title: "gtk engine??"
date: 2006-06-30
forum: Art &amp; Design
---

### Post by babyboss on 2006-06-30
what is gtk engine?
I saw this term everywhere. It has gtk 1.x, and gtk 2.x, and is there any difference between gtk and gtk engine? Also how do I change gtk under ubuntu.
I have a fresh install of Dapper Drake 6.06 ubuntu. Does it have gtk 1.x or gtk 2.x? Thanks

---

### Post by knn on 2006-06-30
[QUOTE=babyboss]what is gtk engine?
I saw this term everywhere. It has gtk 1.x, and gtk 2.x, and is there any difference between gtk and gtk engine? Also how do I change gtk under ubuntu.
I have a fresh install of Dapper Drake 6.06 ubuntu. Does it have gtk 1.x or gtk 2.x? Thanks[/QUOTE]

Gtk is the toolkit which many apps (mostly Gnome apps) use to draw buttons, checkboxes, etc. (Kde uses a toolkit called QT). A gtk engine is what provides theme makers with ways of drawing on the screen (e.g. by drawing pixmaps), and themes are based on these engines. The default Ubuntu theme uses the Clearlooks engine. 
Both gtk1 and gtk2 are available in Dapper. Most applications use gtk2, but some are still gtk1. They look different, since Clearlooks is not available for gtk1. The only way to make these apps use gtk2 is to recompile them (assuming switching to gtk2 doesn't require code changes, I'm not sure about this). KDE apps will also look different, since they use a different toolkit.
Gtk2 themes can be changed in System/Preferences/Theme/Theme details/Controls. You might want to install a few first using synaptic. Search for gtk. To download even more themes (not just gtk, but window decorations, wallpapers etc.), install the gnome art manager (You'll find it in system/preferences after you've installed it).
gtk1 themes can be changed using the application switch (I don't think it's installed by default, so you'll have to install it too. Also, don't look in the menu for it, Alt-F2 and type switch, then enter)
There's a howto to make qt apps look more gnomeish [here]("http://ubuntuforums.org/showthread.php?t=56630&highlight=gtk1") and a howto to make gtk apps look better [here]("http://ubuntuforums.org/showthread.php?t=107135&highlight=gtk1").

---

### Post by babyboss on 2006-06-30
THank you so much

---

### Post by babyboss on 2006-06-30
I downloaded a gtk theme with art-manager, when I tried to install it under the theme, it says that the format is incorrected

---

### Post by babyboss on 2006-07-02
hihihihi.. no one is helping?

---

### Post by knn on 2006-07-02
[QUOTE=babyboss]hihihihi.. no one is helping?[/QUOTE]

Which theme is it. If it's a clearlooks theme with animations, it won't work, because the clearlooks engine in Ubuntu doesn't support animations

---

### Post by mcduck on 2006-07-03
[QUOTE=babyboss]I downloaded a gtk theme with art-manager, when I tried to install it under the theme, it says that the format is incorrected[/QUOTE]
In that case you can just extract the theme to ~/.themes :)

---

