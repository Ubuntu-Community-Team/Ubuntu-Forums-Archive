---
title: "Fonts"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by richard978 on 2008-03-28
Can someone please explain how I add fonts in Ubuntu and whether there is some software to manage them like fontfolio for windows.

Also what fonts are supported?

---

### Post by stchman on 2008-03-28
> **richard978 said:**
> Can someone please explain how I add fonts in Ubuntu and whether there is some software to manage them like fontfolio for windows.

Also what fonts are supported?

I have a tutorial on font installation in Ubuntu.

[http://www.stchman.com/install_fonts.html](http://www.stchman.com/install_fonts.html)

---

### Post by richard978 on 2008-03-28
I have the core MS fonts installed. What I need is a typeface manager like fontfolio where I can preview and add fonts easily.

---

### Post by nik1979 on 2008-05-19
I tried following the first set of instructions It seems I don't have the fonts, where can i get these msttcorefonts?

---

### Post by m83 on 2008-05-19
For font management under Linux I found [FontyPython]("http://fontypython.webfactional.com"). It's in the Ubuntu repositories and you can install it using Synaptics/aptitude/apt-get/add-remove or whatever your poison is. I find it prety cool and does what I need (preview fonts, install/uninstall them). When it installs a font it does not ma a copy of the font into the ~/.fonts directory but instead it makes a symlink so you'll save space and don't have duplicate fonts.

There is another font manager that looks pretty cool: [FontMatrix]("http://www.fontmatrix.net"), but this one is not in the Ubuntu software repositories (yet) and by the looks of it I'd say that is uses QT4 so therefore it's for KDE and I wouldn't use it - don't want to poison my GNOME with KDE apps.

---

