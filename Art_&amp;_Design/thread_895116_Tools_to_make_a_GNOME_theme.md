---
title: "Tools to make a GNOME theme?"
date: 2008-08-19
forum: Art &amp; Design
---

### Post by theyain on 2008-08-19
Anyone know of good tools to use to make a GNOME theme.


Alos, don't suggest GIB, I'm currently working on giving it SVG support :3

---

### Post by smartboyathome on 2008-08-19
Start by editing themes in your ~/.themes/ directory. This is what I do when I create a theme. The files are all XML, so they're relitively easy to read and edit. See the link in my sig for more info.

---

### Post by theyain on 2008-08-19
I already have those book marked, but editing the files takes a long time.

Any well thought out program can halve the production time.

---

### Post by airtonix on 2008-08-21
Couple things I would like is to have an empty metacity & gtk theme file prepared with all the elements ready but no styling.

Then have it so i can click on any real part of the gnome desktop and have the editor jump down or highlight the lines that affect the gui elements i clicked.

example: 

+ I start a new theme, and have two text files open. 
+ They both declare all the elements like window edges, window resize grab, radio boxes, ok buttons, scale sliders etc.
+ I click on the editors "Grab Element Definition" which then allows me to click on real gui elements.
+ I click on the gnome-panel, where there is no icons/controls
+ the editor highlights the relevant lines in the gtk text file showing me where i can apply my styles.

The idea is similar to what the firebug addon for firefox does. allows you to click on webpage elements and see the css/html styling that is relevant.

---

### Post by smartboyathome on 2008-08-21
Get coding, then, because I don't think anyone has done this yet. :(

---

### Post by spupy on 2008-08-23
You don't just start making a GNOME theme. There are different GTK engines with different settings. Choose an engine. Good choices are Clearlooks, Aurora, Murrine. I personally recommend Murrine - it looks good, is very fast, and has a GUI configurator.

Also, really get coding. Besides the Murrine gui configurator, there are no other tools I know of, and the **gtkrc** files are ridiculously simple. You have to find out how the different gui elements are called in these files. What are styles, prelight, trough, slider, handle etc. gtk specific things.

Good luck! :)

---

