---
title: "Coloured Sliders"
date: 2009-10-30
forum: Art &amp; Design
---

### Post by Psyphre on 2009-10-30
Hi, I'm trying to make a theme for gnome, but am stuck with the sliders.

Many themes have coloured in areas as the slider moves along. For some reason I can't seem to get the same even though I'm using the same engine (in this case murrine).

I have tried putting down all of the colour variables and set them all to red to see if anything changes.
e.g:
fg[selected],fg[prelight].... etc etc
bg[selected,bg[prelight]....etc etc
base[selected],base[prelight]....etc etc
and so on.

Here is an example of what I mean. The top is someone elses theme, the bottom slider is mine.

[[IMG]http://img692.imageshack.us/img692/7656/sliders.th.jpg[/IMG]](http://img692.imageshack.us/i/sliders.jpg/)

Click to view in full size.

Is there something I'm missing? An option I'm suppsed to enter for the engine to make it work?

I'll be so grateful if anyone can help me. 

Thanks in advance,
Psyphre.

---

### Post by days_of_ruin on 2009-10-30
```
GtkScale::trough-side-details = 1
```

---

### Post by Psyphre on 2009-10-30
Thanks alot days_of_ruin!!

---

