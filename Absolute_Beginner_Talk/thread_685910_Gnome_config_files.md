---
title: "Gnome config files"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by caravel on 2008-02-02
Does anyone know where the actual config files for gnome are?  Such as the file that stores your font and appearance preferences?

---

### Post by meborc on 2008-02-02
a good question... i looked around a bit and i think you mean the files under /home/USER/.gconf/desktop/gnome

i might be wrong, but surf around there :)

---

### Post by caravel on 2008-02-02
> **meborc said:**
> a good question... i looked around a bit and i think you mean the files under /home/USER/.gconf/desktop/gnome

i might be wrong, but surf around there :)

Hmmm... there are a lot of xml files in there and one in the fontrendering subdirectory but I'm not sure if that's the one. :confused:

---

### Post by bruce89 on 2008-02-02
> **caravel said:**
> Hmmm... there are a lot of xml files in there and one in the fontrendering subdirectory but I'm not sure if that's the one.

Use *gconftool-2* (cli) or *gconf-editor* (GNOME) to monkey with GConf settings.

---

### Post by caravel on 2008-02-02
Seems more complex than editing in  a text editor... is there no other way to simply open a file and change the font?  A friend of mine has tried installing windows fonts (I'm not sure how he's done this as I've never felt the inclination to try it) and has somehow switched to a corrupted font, now he cannot read anything in gnome in order to change the fonts back and is facing reinstalling.

---

### Post by jan quark on 2008-02-02
to add fonts try this

[http://janquark.fatfreehost.com/gimp8.html](http://janquark.fatfreehost.com/gimp8.html)

---

### Post by bruce89 on 2008-02-02
> **caravel said:**
> Seems more complex than editing in  a text editor... is there no other way to simply open a file and change the font?  A friend of mine has tried installing windows fonts (I'm not sure how he's done this as I've never felt the inclination to try it) and has somehow switched to a corrupted font, now he cannot read anything in gnome in order to change the fonts back and is facing reinstalling.

```
gconftool-2 --recursive-unset /desktop/gnome/font_rendering
``` would change back GNOME's font rendering stuff back to the defaults.

Unfortunately, installing fonts manually is a big mistake, use the *msttcorefonts* package in future. If you want to manually install fonts, go to fonts:/// in Nautilus and drag fonts there.

> **jan quark said:**
> to add fonts try this

[http://janquark.fatfreehost.com/gimp8.html](http://janquark.fatfreehost.com/gimp8.html)

Don't move files to non /home directories without knowing what you're doing.

---

