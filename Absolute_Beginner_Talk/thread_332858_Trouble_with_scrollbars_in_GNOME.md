---
title: "Trouble with scrollbars in GNOME"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by tophatandy on 2007-01-06
I got a new theme (the t-brushed pack from gnome look) and when i installed it everything worked just fine with the exception of the blue scrollbars that are supposed to appear, and replacing them I have some ugly sharp squarish gray ones..


any help would be greatly appriciated..

---

### Post by jem7v on 2007-01-06
I think you need to install the **gtk2-engines-pixbuf** package, maybe. It sounds similar to a problem I had... Install it and then try setting your theme again and see if it works.

---

### Post by tophatandy on 2007-01-06
nope..

checked synaptic.. I have it..


i think it might have been because i updated from dapper to edgy via the online update..

my old computer (now my brothers) which was a fresh install of edgy runs like a pro..

really don't know..

anyone else had similar problems or another idea for a fix..

any help is greatly appreciated.

---

### Post by jem7v on 2007-01-06
If it's only that theme, it could be something wrong with the theme itself, or it might have a different dependency. You could try opening the theme file (probably in ~/.themes/themename) in a text editor and scroll through it to see if it has any other dependencies listed.

---

