---
title: "color application bar"
date: 2005-04-14
forum: Art &amp; Design
---

### Post by SilvioTO on 2005-04-14
How to change only color of the application bar?
thanks.

Silvio.

---

### Post by Stormy Eyes on 2005-04-14
[QUOTE=SilvioTO]How to change only color of the application bar?
thanks.

Silvio.[/QUOTE]

What do you mean by the "application bar"? Are you talking about the panels at the top and bottom of the screen in GNOME?

---

### Post by bvc on 2005-04-14
also need to know what theme or type...engine? pixmap?

---

### Post by SilvioTO on 2005-04-15
excuse me... my english...  :-? 
title bar of the windows.
thanks.  :smile:

---

### Post by lao_V on 2005-04-15
goto System -> Preferences -> Theme / Windows

---

### Post by bvc on 2005-04-15
If it's a pure metacity theme you have to edit the metacity-theme-1.xml file or put the following in the gtkrc of the gtk theme and edit with your colors.
```
style "metacity-frame"
{
  # Normal base color
  bg[NORMAL]  = "#bbbbbb"

  # Unfocused title background color
  bg[INSENSITIVE]  = { 0.8, 0.8, 0.8 }

  # Unfocused title text color
  fg[INSENSITIVE]  = { 1.55, 1.55, 1.55 }

  # Focused icon color
  fg[NORMAL]  = { 0.2, 0.2, 0.2 }

  # Focused title background color
  bg[SELECTED]  = { 0.5, 0.8, 0.5 }

  # Focused title text color
  fg[SELECTED]  = "white"
}
class "MetaFrames" style "metacity-frame"
```

If it's a pixmap then recolor the images with the gimp.

---

### Post by SilvioTO on 2005-04-15
Thanks a lot!  :)

---

