---
title: "[SOLVED] font question"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by 1scorpio on 2008-03-30
I am working with some dark wall papers and would like to change the font on the panel to white.. can someone please tell me how i cant seem to find any white or very light. 

thanks in advance 1Scorpio  OH never mind found something in styles that helped some

---

### Post by benbelly on 2008-03-30
If you create/edit the file ~/.gtkrc-2.0, you can change many of the panel colors and settings.
```

style "panel"
{
fg[NORMAL] = "#ffffff"
fg[PRELIGHT] = "#ffffff"
fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = "#000000"
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000"
bg[PRELIGHT] = "#112211"
bg[ACTIVE] = "#224422"
bg[SELECTED] = "#112211"
# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0"
# base[SELECTED] = "#222222"
# base[INSENSITIVE] = "#E8E8E8"
# text[NORMAL] = "#161616"
# text[PRELIGHT] = "#000000"
# text[ACTIVE] = "#000000"
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
widget "*fast-user-switch-applet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

```

The # mark at the beginning of a line comments that line out.  Most of this was borrowed from another post that I can't quite find right now.  You probably want to comment out the **bg** items, and only use the **fg**.

Good luck

-Ben

---

