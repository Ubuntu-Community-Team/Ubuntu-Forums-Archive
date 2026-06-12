---
title: "firefox sigh"
date: 2009-06-10
forum: Art &amp; Design
---

### Post by Hairy_Palms on 2009-06-10
not sure whether this is the best place to ask this or not, but here goes, why is firefox the only browser that doesnt use the GTK icon themes new tab icon?, from what i can find through google it should use tab_new.png from an icon theme, however it never does, always using the default tango one, 

when entering moz-icon://stock/tab_new?size=toolbar into the address bar the correct icon is shown, however it isnt used by the toolbar

anyone know if im missing something or should i file a bug report

---

### Post by Fzang on 2009-06-11
Unfortunately Firefox is not native GTK and does not always follow the global theme style... I hope it'll be truly integrated one day

---

### Post by AKK9 on 2009-06-11
But FZang, if the icon is there, why isn't it being used?

---

### Post by hessiess on 2009-06-11
Firefox's interface is written in [XUL]("http://en.wikipedia.org/wiki/XUL") and just ``emulates'' the GTK theme.if you want to change the icon you will need to change the theme.

---

### Post by Hairy_Palms on 2009-06-11
yes, i know firefox isnt a  "native" gtk app, but the new tab icon doesnt successfully use the GTK icon that its MEANT to use, alll the other icons do, back/forward/home/reload/etc and as you can see with the command in the first post firefox is recognizing it as a moz-stock icon, just isnt using it on the toolbar.

---

