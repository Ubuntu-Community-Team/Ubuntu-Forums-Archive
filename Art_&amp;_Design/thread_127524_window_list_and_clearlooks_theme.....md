---
title: "window list and clearlooks theme...."
date: 2006-02-09
forum: Art &amp; Design
---

### Post by adam.tropics on 2006-02-09
So without posting pictures, I have clearlooks theme running, and my panel text I have set to white (dark desktop, transparent panel). 

Now in the windowlist on my panel, a non-selected window is transparent with my white text. However the selected window illuminates the 'grey box' and text goes to black. Not really a problem, it all works. But, is there a way to 'tweak' the theme so as to not draw the grey box or change the text colour to black, but say, leave the window box transparent, and simply change the text colour to whatever.

I assume there is just a config script, so I assume it can be altered to do this?

No idea if this is strictly posted in the right place, feel free to move if necessary.

---

### Post by bvc on 2006-02-09
dosen't work for clearlooks-cairo but for 6x put```
style "panel"
{
fg[ACTIVE] = "#ff0000"
bg[ACTIVE] = "#000000"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
widget_class "*MenuItem*" style "panel"
class "*MenuItem*" style "panel"
```
in your .gtkrc-2.0 file (create it if it is not there) in your home dir. You can not make the button transparent with an engine, unless you rewrite the engine, but with a pixmap theme you could just specify panel buttons and make them trans.

---

