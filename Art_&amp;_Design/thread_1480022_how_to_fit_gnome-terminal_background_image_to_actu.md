---
title: "how to fit gnome-terminal background image to actual window size"
date: 2010-05-11
forum: Art &amp; Design
---

### Post by karesz on 2010-05-11
Hi! I have a nice background for my gnome-terminal, but I always see only parts of it. How can I make it automatically adjust to it's size?

---

### Post by karesz on 2010-05-12
bump

---

### Post by trinetra on 2010-05-21
Facing same issue, if anybody have solution let us know. I am also struggling in case if I get I will post here. Thanks

---

### Post by trinetra on 2010-05-21
> **karesz said:**
> Hi! I have a nice background for my gnome-terminal, but I always see only parts of it. How can I make it automatically adjust to it's size?

So far what I found is that there is not specific option to fit the image according to the window size. For now I resized the image (on trail and error base) using Gimp and using it.

Any other help will be definitely appreciated. Thank you.

---

### Post by VCoolio on 2010-05-22
You may want to consider switching to rxvt-unicode terminal; it's more lightweight and according to a lot of people better than gnome-terminal. You can do what you asked with urxvt like this: ```
urxvt -pixmap '/path/to/image.png'
``` This will stretch the image to your terminal size; check the difference with ```
urxvt -pixmap '/path/to/image.png;geom:root'
```

---

### Post by pythonholum on 2011-08-26
I am able to find the package for rxvt, Is there a different one for urxvt?

---

### Post by maintainie on 2011-08-27
Would you sent a pic to explain?I need to know more then.Good luck!

---

### Post by VCoolio on 2011-08-27
> **pythonholum said:**
> I am able to find the package for rxvt, Is there a different one for urxvt?

The packagename is rxvt-unicode. The command to launch it is urxvt.

---

