---
title: "How to get Windows XP fonts in Gutsy"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by nemesis8601 on 2007-11-27
Does anyone know how I can get XP fonts in Gutsy? All my fonts are a bit off. 

I checked in the medibuntu repository using the synaptic package manager but I couldn't find a package for fonts. 

Thanks!

---

### Post by Cable on 2007-11-27
You can get some Microsoft fonts by installing the msttcorefonts package.  Is that what you're looking for?

---

### Post by nemesis8601 on 2007-11-27
Yes, I just installed it. It works great; thanks a lot!

---

### Post by oktapod on 2008-03-24
thank you Cable.

---

### Post by sayakb on 2008-03-24
You might try this also.. Just copy the contents of C:\Windows\Fonts to /usr/share/fonts/truetype/MyFonts (create a folder MyFonts first) -- BUt make sure the extension of the fonts should be ttf (NOT in block letters)

---

