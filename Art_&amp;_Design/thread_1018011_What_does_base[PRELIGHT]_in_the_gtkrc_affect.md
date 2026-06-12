---
title: "What does base[PRELIGHT] in the gtkrc affect?"
date: 2008-12-21
forum: Art &amp; Design
---

### Post by dabugas on 2008-12-21
What the title says. I'm working on a theme and out of curiosity I've put, in the default style, base[PRELIGHT] = "#ff00ff". I've been waiting for a couple of days for some garish pink widget to pop up with no success. So, what *does* it affect? Oh, and the theme is based on clearlooks.

---

### Post by jorgecs10 on 2008-12-22
As the [gnome art's tutorial]("http://live.gnome.org/GnomeArt/Tutorials/GtkThemes/#head-dd0f80dd8d35a7282d6d739af825c923f71abdb4") says is the background color of text widgets and lists

---

### Post by dabugas on 2008-12-22
Thanks for the reply but I'm not asking about base in general. I'm asking about base[PRELIGHT] specifically. From the same tutorial: "Prelight means mouse over effects. Usually the background will be slightly lighter." I have never seen prelighting effects in lists, hence my original question.

I know that sometimes GTK+ engines sometimes use values for weird things. (Aurora is infamous for this because of the way the arrows are colourised.) I'm wondering if base[PRELIGHT] is used for something really rare. Otherwise, it seems to be a redundant value, at least in clearlooks.

---

### Post by OrangeVixen on 2009-10-12
It all depends on how the GtkWidget in question was programed to draw based on the GtkStyle's PRELIGHT GtkStateType.

The base color is typically used for the GtkCList, GtkEntry, GtkText editable area backgrounds (not it's "surface background" in which case bg[NORMAL] would have an affect).

Most such GtkWidgets, as mentioned above, simply do not draw any details that use the GtkStyle's base color with the PRELIGHT GtkStateType.

If you want to see an affect with the PRELIGHT state, only bg[PRELIGHT] and fg[PRELIGHT] for the GtkButton would produce a result when you move the pointer over the GtkButton. Most other GtkWidgets just don't have anything that responds to base[PRELIGHT].

---

