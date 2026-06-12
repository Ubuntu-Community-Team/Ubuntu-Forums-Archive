---
title: "Need Help From The Themers - Clearlooks.xml question"
date: 2005-05-30
forum: Art &amp; Design
---

### Post by MetalMusicAddict on 2005-05-30
Ok. I, like everyone else seems to like clearlooks. 

I like dark themes but I hav'nt found one I like so I am making my own. 

Problem is in the metacity-theme-1.xml file I cant figure out what line defines the titlebar color. In the Selected and Unselected states. There seems to be just the 2 states. The file seems to get its color from the gtkrc file. If this the case and it references a color I don't want can I define them in the metacity file?

Any help is cool. ;)

EDIT: I cant post the xml file. The board is saying its too big.

---

### Post by bvc on 2005-05-30
Yes, when you see something like
shade/gtk:bg[NORMAL]
it is referring to the gtkrc of the gtk theme in use.

Don't know if this will help or if you've already found it...
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

I d/k how to specify an absolute color because I've never done a pure mcity.

---

### Post by MetalMusicAddict on 2005-05-30
Here's what I have so far:
[[IMG]http://img271.echo.cx/img271/4175/untitled19wg.png[/IMG]](http://img50.echo.cx/img50/4660/untitled9pc.png)
Click for 2560x1024.

Im trying to get shading on the Active Titlebar. Its supposed to be black but when I took the screenshot 1 wasnt hilighted. Its completely black though. Only th white glyphs show. Also the Close, ect buttons need defined as well as their states defined.

---

### Post by bvc on 2005-05-30
use the gimp to take the screenshot with a delay so you can select a window to be active, heh, you can even just shoot the active window as well.

---

### Post by bvc on 2005-06-07
the new clearbox specifies a pressed button color
i'd think the same would appy in other areas
```
<draw_ops name="menu_button_pressed">
  <include name="bg_topbar"/>
  <line color="#AD3841"
```
(I changed the color from the default yellow)

---

### Post by N'Jal on 2005-06-07
I'm not a themer but i can say that's gona be one sweet theme when it's done!

---

### Post by TravisNewman on 2005-06-07
heeeey look at that! I'm in the screenshot :)

Seriously, that's gonna be slick.

---

### Post by MetalMusicAddict on 2005-06-09
Im still workin on it. Ive had some things to do. Family and all. :) Also Im setting up MythTV on my new 42" plasma. It looks SO GREAT with a PC hooked up to it. :)

Things to do on the theme:

-Make panel&Apps menu black without changing button color.
-Make shading on titlebar&buttons white.
-Make Sliderbar&Buttons black with proper shading.

If there is anyone who would like to collaberate with me I would love the help. :)

---

