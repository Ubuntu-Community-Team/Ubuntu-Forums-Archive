---
title: "new awesome release!"
date: 2008-05-02
forum: Arch and derivatives
---

### Post by shearn89 on 2008-05-02
howdy all - new awesome release (2.3-rc3). Once again, they've changed the config file, so you'll have to tinker slightly, however the default config is at least quite pretty. They've changed the widget interface as well...


New .awesomerc:
```

screen 0
{   
    styles
    {   
        normal
        {       
                font = "sans 8"
                fg = "#ffffff"
                bg = "#000000"
                border = "#555555"
        }
        focus
        {       
                fg = "#ffffff"
                bg = "#b4b892"
                border = "#b4b892"
        }
        urgent
        {       
                fg = "#111111"
                bg = "#ff4500"
        }
    }

```
There's that section, which takes over the first few sections.


and the new widget syntax is:
```

echo <screen> widget_tell <statusbar name> <widget> text <your text> | awesome-client

```
You need that "text" in there.

---

### Post by kibbl on 2008-05-07
Is there any Ubuntu repository from which this can be installed, or does it need to be manually compiled?

I tried the latter and discovered that it requires libconfuse 2.6 while Ubuntu has only 2.5. I then modified ./configure to trick it to require only 2.5. But then it gave this error:

common/configopts.c:387: error: ‘CFGF_NO_TITLE_DUPES’ undeclared here (not in a function)

That's all I've been able to do so far. Have you successfully installed it yourself? And if so, what was the trick? Thanks!

---

### Post by chucky chuckaluck on 2008-05-07
looks snazzy.

---

### Post by sujoy on 2008-05-09
how to set opacity_focused and opacity_unfocused? on adding these under general section, i get thrown back to the default config. This also happens on using the fg property in textbox widget.

EDIT: never mind i got it solved :) the man page said float values so i gave 50.0, 87.34 etc. :lolflag: whereas it takes value between 0.0 and 1.0

---

### Post by finferflu on 2008-05-09
> **chucky chuckaluck said:**
> looks snazzy.

Looks always the same to me :P

---

