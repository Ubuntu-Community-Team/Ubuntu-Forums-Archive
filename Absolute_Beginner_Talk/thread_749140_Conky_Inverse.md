---
title: "Conky Inverse"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by wormser on 2008-04-08
I like to change my wallpapers often.  Is there any way to make Conky always show the inverse color?

---

### Post by finer recliner on 2008-04-08
i dont see any options for inverting the background colors in the man page:

[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)


a lot of people (including myself) set the font colors to to white, and give it an outline border of about 1 px colored black. this will make conky readable on most backgrounds.

---

### Post by nilarimogard on 2008-04-08
And how do you do that?

---

### Post by finer recliner on 2008-04-08
edit you ~/,conkyrc file. add the following lines above the TEXT line:

```

draw_outline yes # amplifies text if yes
default_color grey

```

i think thats all you need.

the easiest way to customize conky is by example. look at other peoples' conky setups and just copy/paste anything you like:

[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)

---

