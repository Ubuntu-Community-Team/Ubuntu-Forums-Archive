---
title: "text too light in epiphany web browser"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2007-12-31
hi, i have a problem in epiphany where on some pages the text is too light compared to the background. where can i tweak here?  i know how to fix this in firefox, but i have problems with it freezing on youtube and other flash video sites. epiphany doesnt freeze up on me, but has the problem with the text on some sites shown in the picture.

---

### Post by kefurd06 on 2008-01-01
have you tried turning off hinting? (System > Prefs > Appearance > Fonts Tab > Details). the font will still be light, but there will be more font there to read. hope this helps.

---

### Post by jayde6 on 2008-01-01
It is most likely because you are using a dark theme, in epiphany go to preferences and select use custom stylesheet. Click edit stylesheet and paste this
```
html {
color: black;
background: white;
}
```
 into the box that comes up and save it. You may have to restart the browser for it to take effect.
Hope this helps,
~Jennifer

---

### Post by thebestofall007 on 2008-01-01
thanx, it worked.

---

