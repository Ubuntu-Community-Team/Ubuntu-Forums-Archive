---
title: "change metacity button"
date: 2005-03-11
forum: Art &amp; Design
---

### Post by lizardking on 2005-03-11
I found a tutorial to change **metacity window button position** *(minimize,maximize, colse)*   from the right position to the left position like window of macOSx
```
Question: the buttons for the window border being on the left,
is that a theme thing or can that be configured somewhere?

Answer: ( original tutorial by -fissy. )

using the "run program" action or a terminal, start gconf by typing:

gconf-editor

and hitting enter.

This program is a bit like the registry editor for windows.

In the tree on the left you need to go to /apps/metacity/general/

There is then a key in the right pane called "button_layout"

edit this key so that it reads:

CODE
close,minimize,maximize:menu

or
CODE
close,maximize,minimize:menu
``` 

I hope that it will useful...
 [-o<

---

### Post by bored2k on 2005-03-11
[QUOTE=lizardking]I found a tutorial to change **metacity window button position** *(minimize,maximize, colse)*   from the right position to the left position like window of macOSx
```
Question: the buttons for the window border being on the left,
is that a theme thing or can that be configured somewhere?

Answer: ( original tutorial by -fissy. )

using the "run program" action or a terminal, start gconf by typing:

gconf-editor

and hitting enter.

This program is a bit like the registry editor for windows.

In the tree on the left you need to go to /apps/metacity/general/

There is then a key in the right pane called "button_layout"

edit this key so that it reads:

CODE
close,minimize,maximize:menu

or
CODE
close,maximize,minimize:menu
``` 

I hope that it will useful...
 [-o<[/QUOTE]
 Cool.

Its a little awkward though, but its cool for PowerPC users. Again, I used to think I would never use an upper panel, and thats not the case with g-nome huh?

---

### Post by mtcycler on 2010-03-05
It works in 10.04 alpha 3 too...

---

### Post by Cuppa-Chino on 2010-03-10
Very true, especially note the colon position for the placement wrt to the corners!

---

