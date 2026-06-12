---
title: "GTK2 Window Border Color"
date: 2009-07-27
forum: Art &amp; Design
---

### Post by K. Hendrik on 2009-07-27
Hi,
I'm trying to change the standart Human theme and I've got a little question, I'am trying to change the color of the Window Borders it works if I set a style to the metacity-frame in the gtkrc-file like this:
```
class "MetaFrames" style "metacity-frame"
```
The problem is this only works if i turn the effects off(compiz)
what do I have to use if I want it to work with the effects.

---

### Post by K. Hendrik on 2009-07-27
bump

EDIT:
OK I solved it just needed to theme GtkWindow

---

### Post by t1010011 on 2010-05-06
Actually, just for the sake of completeness, I was with the same issue and solved using the match:

```
widget "GtkWindow" style "Your-Metacity-Color-Style" 
```

may be obvious, but that I had to use the widget match and not class or widget_class matches took me a while to realize...

---

