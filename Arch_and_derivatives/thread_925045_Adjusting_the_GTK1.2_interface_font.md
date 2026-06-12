---
title: "Adjusting the GTK1.2 interface font"
date: 2008-09-20
forum: Arch and derivatives
---

### Post by K.Mandla on 2008-09-20
I'm losing sleep over this one. I can't seem to find the setting or file to adjust the interface font and size on GTK1.2 applications. 

The corresponding file in Ubuntu is /etc/gtk/gtkrc.utf-8, but I can't find anything similar for the en_US locale in Arch. There are lots of other files for other xx_XX settings, but nothing I change seems to affect it.

All I want is to make Dillo's buttons look a little less obnoxious. ... :(

---

### Post by chucky chuckaluck on 2008-09-20
> **K.Mandla said:**
> All I want is to make Dillo's buttons look a little less obnoxious. ... :(

can you post a pic? this is ringing a dusty bell for me.

---

### Post by K.Mandla on 2008-09-20
See how enormous the button fonts, etc., are? In Ubuntu the /etc/gtk/gtk.utf-8 file allows you to crank those down a bit; they're not affected by the theme settings as far as I know.

Where's the Arch file for that? :(

---

### Post by mips on 2008-09-20
Is that not something that has to be done inside bon echo?

---

### Post by K.Mandla on 2008-09-20
Nope, it's the same for Dillo or the GTK1.2 Firefox, which is in that screenshot. It's a little frustrating, because everything else is a "normal" size. 

I'll keep trying.

---

### Post by voteforpedro36 on 2008-09-21
pacman -S gtk-theme-switch

It's under "click here for more options".

---

### Post by K.Mandla on 2008-09-22
Sorry, it's not a theming problem. switch doesn't affect it.

---

### Post by chucky chuckaluck on 2008-09-23
that's pretty baffling. the buttons in dillo can be made smaller in the dillorc. looks like this...

[[IMG]http://b.imagehost.org/t/0268/dillo.jpg[/IMG]](http://b.imagehost.org/view/0268/dillo.jpg)

i can't find a way to alter gtk-1 at all. there seems to be an option for font selection in gtk-theme-switch, but i never understood all that *font-*-*-*-whatever* mess. in firefox, the font in the bar that has "file, edit, view, etc." is controlled by the gtk theme, while the font in the navigation and bookmark toolbars are controlled by firefox (and you may need to adjust these in the userChrome.css file). that's all i can figure out.

btw, you can find a samle dillorc at [http://www.dillo.org/dillorc](http://www.dillo.org/dillorc)

---

### Post by K.Mandla on 2008-09-26
> **chucky chuckaluck said:**
> that's pretty baffling. the buttons in dillo can be made smaller in the dillorc. looks like this...

[[IMG]http://b.imagehost.org/t/0268/dillo.jpg[/IMG]](http://b.imagehost.org/view/0268/dillo.jpg)

i can't find a way to alter gtk-1 at all. there seems to be an option for font selection in gtk-theme-switch, but i never understood all that *font-*-*-*-whatever* mess. in firefox, the font in the bar that has "file, edit, view, etc." is controlled by the gtk theme, while the font in the navigation and bookmark toolbars are controlled by firefox (and you may need to adjust these in the userChrome.css file). that's all i can figure out.

btw, you can find a samle dillorc at [http://www.dillo.org/dillorc](http://www.dillo.org/dillorc)
Agreed, this is odd. Just for reference, modifying /etc/gtk/gtkrc.utf-8 makes dillo do this:

[http://xs.to/xs.php?h=xs219&d=07374&f=2007-09-13-075740_1024x768_scrot.png](http://xs.to/xs.php?h=xs219&d=07374&f=2007-09-13-075740_1024x768_scrot.png)

Which is much more palatable.

---

