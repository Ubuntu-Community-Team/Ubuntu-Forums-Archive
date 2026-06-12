---
title: "[SOLVED] how to change xterm fonts?"
date: 2008-03-10
forum: Arch and derivatives
---

### Post by sujoy on 2008-03-10
i dont really like the default xterm font and would love to use this one instead.
[http://gnome-look.org/content/show.php/Matrix+font?content=66302]("http://gnome-look.org/content/show.php/Matrix+font?content=66302")
so how can i change the default xterm font to this one?

---

### Post by finferflu on 2008-03-10
The link you provided is broken...
Anyway, you can change the font for xterm using the -fn flag:

```
xterm -fn <fontname>
```
Where <fontname> is an entry like this (example with Dejavu Sans):
```
-*-dejavu sans-medium-r-*-*-11-*-*-*-*-*-*-*
```

You can find out the exact entry using xfontsel.

---

### Post by Gigamo on 2008-03-10
Or set this in your ~/.Xdefaults:

```
xterm*font: DejaVu Sans Mono:pixelsize=10
```

---

### Post by kerry_s on 2008-03-10
just remember in terminal, you want to use a fixed-width or monospace font. if not the text may appear squished together.

---

### Post by sujoy on 2008-03-10
sorry for the broken link.

yes i tried the -fn option but cant seem to use TTF fonts with it. 
also
 XTerm*font:  matrix 

gives me a "cannot find font,using fixed" error message

EDIT: 

found the solution ..

xterm -fa "fontname"
or
XTerm*faceName:        <fontname>

---

