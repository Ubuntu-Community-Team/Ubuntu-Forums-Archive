---
title: "Getting a higher refresh rate for my monitor"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by Saponification on 2005-08-11
I've just installed *ubuntu* on my desktop. The monitor is an Acer AF715. I went to the screen resolution options and I can only select 60Hz - I'd like it up about 85Hz. I'm running it at 1024x768.

---

### Post by blind0wl on 2005-08-11
You'll need to manually edit your xorg.conf file to do this, open a console window and type:

```
sudo nano /etc/X11/xorg.conf
```

Then find the "Monitor" section and add these two lines to it:

```

Section "Monitor"
        Identifier      "Right Monitor"
        Option          "DPMS"
[B]        HorizSync       30-98
        VertRefresh     50-160[/B]
EndSection

```

Exit and Save, and restart your xserver by Ctrl-Alt Backspace

---

