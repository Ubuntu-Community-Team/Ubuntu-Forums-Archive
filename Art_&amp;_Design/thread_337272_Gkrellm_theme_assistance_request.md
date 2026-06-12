---
title: "Gkrellm theme assistance request"
date: 2007-01-12
forum: Art &amp; Design
---

### Post by yabbadabbadont on 2007-01-12
I am seeking advice on how to create (or modify an existing) gkrellm theme so that the entire thing is transparent, but with a dark tint (black with 50% alpha channel) so that the text is always visible regardless of the wallpaper.  Currently, I just use a fully transparent theme that I hacked together:
```
/home/bubba/.gkrellm2/themes/bubba $ cat gkrellmrc 
author = "Bubba"
StyleChart  *.transparency = 1
StylePanel  *.transparency = 1
StyleMeter  *.transparency = 1
StyleMeter  *.border = 3,3,3,3
StylePanel  *.border = 3,3,3,3
StyleChart  *.border = 3,3,3,3
chart_in_color       = green
chart_out_color      = red
chart_in_color_grid  = black
chart_out_color_grid = black
StyleChart  *.textcolor     = white black shadow
StyleMeter  *.textcolor     = white black shadow
StylePanel  *.textcolor     = white black shadow
StyleChart  *.alt_textcolor = white black shadow
StyleMeter  *.alt_textcolor = white black shadow
StylePanel  *.alt_textcolor = white black shadow
```
I have tried, unsuccessfully, to modify existing themes using GIMP, but I've never managed to get it right.  Any advice would be appreciated.

Edit: Here is a screenshot for clarification.  I have modified the weather desklet to have the tinting that I desire in gkrellm as well.

[[IMG]http://img407.imageshack.us/img407/4145/screen20070112183143iu5.th.png[/IMG]](http://img407.imageshack.us/my.php?image=screen20070112183143iu5.png)

---

### Post by yabbadabbadont on 2007-01-15
Shameless bump.  (I'm sure I'll burn for this :D)

---

### Post by yabbadabbadont on 2007-01-22
Bueller, Bueller, anyone, Bueller?  :)

---

### Post by autocrosser on 2007-01-22
I've created Gkrellm themes before by editing the .pngs & the gkrellmrc files. There is a users list you can subscribe to & I'd goto the main website:  

[http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)   and the Theme info page:

[http://members.dslextreme.com/users/billw/gkrellm/Themes.html](http://members.dslextreme.com/users/billw/gkrellm/Themes.html)

That should give you the info you need:wink:

---

### Post by yabbadabbadont on 2007-01-22
Thanks for the reply.  Although I forgot to mention it before, I've read through that information many times.  My main problem is that I haven't been able to create the theme png files in GIMP that are nothing but a tinted alpha channel.  No matter how I've tried to modify the png's, I've never managed to get gkrellm to display it correctly.  I guess I need to work though some GIMP tutorials and then try again.  :D

---

