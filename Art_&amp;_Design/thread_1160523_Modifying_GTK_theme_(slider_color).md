---
title: "Modifying GTK theme (slider color)"
date: 2009-05-15
forum: Art &amp; Design
---

### Post by nortexoid on 2009-05-15
I'm trying to modify my gtk theme to change the color of the slider used in things like the volume applet, i.e. NOT the scroll bar. I can't find anything that might do it in the gtkrc file. Any help is greatly appreciated.

Oh, also is there any way to put some sort of highlighting around an active tab? I have a black theme and it's difficult sometimes to distinguish which tab is active. A little light highlighting around its edges would help a lot.

---

### Post by days_of_ruin on 2009-05-15
> **nortexoid said:**
> I'm trying to modify my gtk theme to change the color of the slider used in things like the volume applet, i.e. NOT the scroll bar. I can't find anything that might do it in the gtkrc file. Any help is greatly appreciated.

Oh, also is there any way to put some sort of highlighting around an active tab? I have a black theme and it's difficult sometimes to distinguish which tab is active. A little light highlighting around its edges would help a lot.

What dark theme are you using? You could try looking at the New Wave theme.
It uses images for sliders.

---

### Post by nortexoid on 2009-05-16
> **days_of_ruin said:**
> What dark theme are you using? You could try looking at the New Wave theme.
It uses images for sliders.

I'm using Cole. I've found the color settings for the scrollbar which I changed, but I can't figure out the rest of the sliders.

I've looked at some other theme files as well but don't see anything relevant. I suppose I'll have to keep digging.

---

### Post by xl_cheese on 2009-05-16
look for a gtk*range* field.  Sometimes at the bottom of the gtkrc file there are the widgets and they just inherit the generic settings.  You may have to create your own settings for it.

Look at my modified clearlooks engine.
[http://www.gnome-look.org/content/show.php/xl_cheeselooks+gtk-engine?content=73163](http://www.gnome-look.org/content/show.php/xl_cheeselooks+gtk-engine?content=73163)

You the scroll bars are tinted to be the prelight foreground color.  You can open the gtkrc and do whatever you want with the range sliders.

---

### Post by nortexoid on 2009-05-16
Thanks cheese. I just tried tinkering a bit with some range values but they didn't have an effect. I'm pretty sure those sliders are inheriting the background color which makes them nearly impossible to see. I'll keep tinkering.

---

