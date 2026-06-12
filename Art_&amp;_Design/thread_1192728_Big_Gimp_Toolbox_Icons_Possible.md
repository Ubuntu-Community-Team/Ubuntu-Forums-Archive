---
title: "Big Gimp Toolbox Icons Possible?"
date: 2009-06-20
forum: Art &amp; Design
---

### Post by cubeist on 2009-06-20
Hi, I hate the tiny 48x48 toolbox icons in the gimp and really want to replace them with beautiful custom 128x128 icons.

I have tried replacing the icon in the source and then recompiling, but the larger icon is just squeezed into the existing 48x48 frame (see pic). It is slightly bigger, but not the way I want it.

Is it possible to have nice big icons in the Gimp? Or do I have to rewrite some of the source?

---

### Post by AJB2K3 on 2009-06-20
I take it you didn't check gimps setting before wasting time recompiling gimp then?

Gimps icons are theme chosen from within gimps preference menu's.

---

### Post by cubeist on 2009-06-20
Can you be more specific AJB2K3?  I have tried changing the theme, it was naturally the first thing I tried, but if the pixmap is only 48x48, and in the theme you tell it to be 128x128, if you don't actually change the pixmap (ie, make it bigger), then the theme will simply stretch the 48x48 icon...

I hope I am making sense... if you have big icons from changing your theme can you please post the gtkrc for me, thanks!

PS - Compiling a waste of time...nah, it took about 15 seconds of input and about 7 minutes of cpu time in the background...easy, peasy!

---

### Post by cubeist on 2009-06-22
I hate bumping my own thread...but I know there are a ton of Gimp users out there and I can't believe I am the only one that wants big, and nice looking, toolbox icons...Anyone have any ideas?

---

### Post by AJB2K3 on 2009-06-23
I was poking around the files in user/share/gimp/themes as I can't find any of the old data.

---

### Post by jesterthejedi on 2009-06-25
There is one trick. You save the icon in the 48x folder, but actually use a 96x icon in its place. In other words you double its size. I was playing around with 256x icons in my 128x folders and noticed that this works for icons like the Computer(on the desktop). Of course this would only be recommended to so inside gimps own icon folder, or a specific theme written for gimp.

---

### Post by cubeist on 2009-06-26
Thanks jester...no go though...
I have discovered that *bigger* icons are possible, but are capped at the maximum gtk size of *dialog*, which is 48x48 pixels.  This is still a big improvement over the stock 22x22 pixel icons (my first post was wrong calling the stock icons 48x48's).  I am currently re-drawing all the icons for gimp and when I am done will post an icon set and a tutorial on how to integrate them into the Gimp (Gimp icons are compiled into the program) for all those interested.

---

