---
title: "Compiz-fusion installed nothing happens"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Nigmah on 2007-08-17
[COLOR=DarkOrange][B]Hi I've installed compiz-fusion about 4 times now and only during the first installation did it kinda worked, i only got the unfold box, wobbly windows and transparent menus.

I've used compiz --replace and emerald --replace.
running off a 8800 gts so theres no problem with the card.

Much thanks for help.[/B][/COLOR]

---

### Post by njknight on 2007-08-17
that should be
compiz --replace -c emerald &

use Alt + F2 and paste the above into the window then hit enter.......that might get things started

I presume that the emerald theme manager is installed ?

---

### Post by Venerence on 2007-08-17
Failing that, you might want to try ```
compiz --indirect-rendering --replace -c emerald
``` to try an alternate rendering of compiz, instead of compiz --replace and emerald --replace. This worked for me on my radeon x1700 for compiz fusion.

---

### Post by Nigmah on 2007-08-18
[COLOR=DarkOrange]**tried **[/COLOR]
compiz --indirect-rendering --replace -c emerald

[COLOR=DarkOrange]**this was the error i got**[/COLOR]

compiz (core) - Warn: Unknown option '-c'

compiz (core) - Fatal: No composite extension

[COLOR=DarkOrange][B]when i try it without -c i get just the latter

anyways while i'm here i'd like to get something else fixed. Sometime when i start up ubuntu i just can't get internet working, no matter how many time i restart. Eventually i'll just boot in and it'll work.
[/B][/COLOR]

---

### Post by Nigmah on 2007-08-26
**[COLOR=darkorange]BUMP![/COLOR]**

---

