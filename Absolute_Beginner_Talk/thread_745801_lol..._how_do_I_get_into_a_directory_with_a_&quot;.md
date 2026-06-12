---
title: "lol... how do I get into a directory with a &quot;space&quot; in it?!?!?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by klokwyze on 2008-04-04
I'm in BASH & the name od the directory I wanna get into is "External HDD". It's an external harddrive with NTFS format. How do I get into it?!? No matter what I type "cd.... etc.", BASH says doesn't exist.

Thanks!!!

---

### Post by joshrobinson on 2008-04-04
say its called Josh Robinson
i would do

cd Josh then hit the tab button
it should auto fill the rest

---

### Post by tamoneya on 2008-04-04
cd Directory\ with\ a\ space

---

### Post by klokwyze on 2008-04-04
> **joshrobinson said:**
> say its called Josh Robinson
i would do

cd Josh then hit the tab button
it should auto fill the rest

ahhh thanks! Very useful tool right there. :beer:

---

### Post by I_R_LEENUCKS_MAN on 2008-04-04
Have you tried an underscore?

---

### Post by spiderbatdad on 2008-04-04
File called Joe Cool in Music folder of home directory.```
cd Music/"Joe Cool"
```didn't need /home/myName/Music/"Joe Cool"  because when I open the terminal from the desktop, I am already in the /home/user directory.

---

### Post by 3rdalbum on 2008-04-04
You can either put a backslash before the space, use the tab key to autocomplete, or put quotes around the path.

```
cd Rolling\ Stones
```
cd Roll <tab> (autocompletes to *Rolling\ Stones*)
```
cd "Rolling Stones"
```

---

### Post by bodhi.zazen on 2008-04-04
1. escape the space with \ -> like\ this

2. Use quotes -> "like this"

3. Use tab completion -> like<tab> becomes like\ this

---

