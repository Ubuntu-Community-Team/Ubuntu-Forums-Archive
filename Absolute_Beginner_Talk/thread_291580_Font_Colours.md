---
title: "Font Colours"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-11-02
Hello,

I was just sprucing my desktop up and I was wondering. How would I change the font colours of the icons on the desktop and of the things written on the panel? is there any way of doing that?

---

### Post by po0f on 2006-11-02
PPAAUULL,

I'm guessing somewhere in your current theme's gtkrc.

---

### Post by jordanmthomas on 2006-11-02
Check out this:
[http://www.gnome-look.org/content/show.php?content=47349](http://www.gnome-look.org/content/show.php?content=47349)

wokrs like a charm!
```

style "gnome-color-chooser-desktop-icon" = "gnome-color-chooser-default"
{
  NautilusIconContainer::frame_text = 1
  text[NORMAL] = "#FFFFFF"
  base[NORMAL] = "#0C0C0C"
  NautilusIconContainer::normal_alpha = 166
}
widget_class "*DesktopIcon*" style "gnome-color-chooser-desktop-icon"
```
Is what it put in .gtkrc-2.0 when I wanted to play with my icons

---

