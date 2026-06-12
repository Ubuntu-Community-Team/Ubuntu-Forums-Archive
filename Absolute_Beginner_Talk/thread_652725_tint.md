---
title: "tint"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-12-29
Okay every has been talking about ttm also called tint which is a taskmanager and i was wondering how i customize it and also if someone could help me customizing tint

---

### Post by rjmdomingo2003 on 2007-12-29
> **fedex1993 said:**
> Okay every has been talking about ttm also called tint which is a taskmanager and i was wondering how i customize it and also if someone could help me customizing tint
I'll share my tintrc, then save it in ~/.config/tint:

```
font = your_font font_size 
font_color = #cbcbcb
font_alpha = 60
font_active_color = #cbcbcb
font_active_alpha = 100
font_shadow = 0
task_text_centered = 1
task_width = 100
task_margin = 3
task_padding = 5
panel_width = 0
panel_height = 30
panel_tasks_centered = 1
panel_background = 0
panel_background_color = #081f3a
panel_background_alpha = 20
task_background = 1
task_background_color = #ffffff
task_background_alpha = 0
task_active_background_color = #ffffff
task_active_background_alpha = 12
task_background_as_border = 1
```

You can start customizing from here.

To start tint, from the terminal:

```
tint &
```

Then,
```

exit
```

---

### Post by fedex1993 on 2007-12-29
Okay i installed from the .deb file and there was a problem i cant find where to copy my config_sample file to

---

### Post by rjmdomingo2003 on 2007-12-29
> **fedex1993 said:**
> Okay i installed from the .deb file and there was a problem i cant find where to copy my config_sample file to
Should've mentioned that I complied tint from source. There's sort of a bug in using tint fluxbox showing a window (borders & all) upon running tint.

If you compile from source, you'll find tintrc in ~/.config/tint.

---

### Post by urukrama on 2007-12-30
There is a thread for tint (and visibility) configuration [here]("http://ubuntuforums.org/showthread.php?t=510528&highlight=tint+visibility")

---

