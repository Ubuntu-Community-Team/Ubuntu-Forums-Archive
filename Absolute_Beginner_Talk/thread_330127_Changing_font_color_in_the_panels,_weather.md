---
title: "Changing font color in the panels, weather"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Good Ol' Ramos on 2007-01-02
I recently learned how to make my panels transparent, and I have this awesome dark desktop wallpaper, but now all the text is still black. How do I change it say, white? Also, I'm trying to get that weather program to show me the, well, weather in the "tray" by the time. How do I do that? THANK YOU!!!!

---

### Post by ingo on 2007-01-04
not in ubuntu, but in kde you go to the control centre, select appearance, click on fonts and there you are!

---

### Post by pross on 2007-01-04
ahh this i can help with :)
took me AGES to find this little gem:
nano ~/.gtkrc-2.0 (it may or may not already exist)

add the following...

```

style "my_color"
{
fg[NORMAL] = "#ffffff"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"

```
thats it!

---

### Post by Lord Illidan on 2007-01-04
As for the Weather applet next to the clock, you can do it , by rightclicking on the adjacent widgets like system tray, etc, and make sure that they are **not** locked to panel.

---

### Post by Good Ol' Ramos on 2007-01-04
Well actually, I got the little weather program on the panel, that wasn't the problem. I apologize for my vagueness. I remember at the time when I was posting this, my fiance was giving my a hard time about being on this computer so much. Anywho, what I want to know is why it won't update, and something about current availability in my area. As for the font color in the panels, pross, I put in that code, hit enter, and nothing happened... :(

---

### Post by macogw on 2007-01-04
put it in that file and save it, then restart X by ctrl alt backspace

---

### Post by Lord Illidan on 2007-01-05
This code might work better.

style "panel"
{
  fg[NORMAL] = "#ffffff"
# fg[PRELIGHT] = "#000000"
# fg[ACTIVE] = "#ffffff"
# fg[SELECTED] = "#000000"
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000"
# bg[PRELIGHT] = "#dfdfdf"
# bg[ACTIVE] = "#D0D0D0"
# bg[SELECTED] = "#D8BB75"
# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0"
# base[SELECTED] = "#DAB566"
# base[INSENSITIVE] = "#E8E8E8"
# text[NORMAL] = "#161616"
# text[PRELIGHT] = "#000000"
# text[ACTIVE] = "#000000"
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

---

