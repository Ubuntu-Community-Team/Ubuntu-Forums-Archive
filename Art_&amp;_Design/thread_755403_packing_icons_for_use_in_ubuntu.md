---
title: "packing icons for use in ubuntu"
date: 2008-04-14
forum: Art &amp; Design
---

### Post by m.musashi on 2008-04-14
There are some neat icons on the vladstudio site ([http://www.vladstudio.com/ra/](http://www.vladstudio.com/ra/)). I'm not sure if they are free to all but as a registered member I can download them. However, I think they are meant for windows. How would one go about packaging them to work with ubuntu? Obviously ubuntu would need to know what each icon is to be used for so I suspect there will be some manual labor involved.

---

### Post by smartboyathome on 2008-04-14
They are most likely .ico, so they have to be converted to .png (I don't know if they can be converted to svg easily). Once they are converted, replace icons in one icon set with these icons.

---

### Post by m.musashi on 2008-04-14
Thanks for the info. They are .ico but when I open them with gimp there are actually several icons in the file (different sizes). I suspect just converting the .ico to .png or .svg will not preserve the multiple icons or will just compact them. In Ubuntu there seems to be different sized icons in separate folders. Will I need to break these apart or is there a tool than can convert them?

Also, when you say to replace icons in one set with these, do you mean to a one for replacement such as old trash can ico with new trash can icon and preserve the name of the old trash can icon?

EDIT: I've attached one as an example.

---

### Post by smartboyathome on 2008-04-14
Convert the ico to png. This will make several of different sizes. Then, take an icon set, and replace one of each size with these converted icons.

---

### Post by m.musashi on 2008-04-14
Thanks again. I don't mean to be dense but I'm not getting something. You said to convert to png and that would save the differnt sized icons. The only way I see to convert to png is to open with gimp and save as png. However, that just flattens the layers givening me one file with "stacked" icons. Is there something I'm missing?

---

### Post by smartboyathome on 2008-04-14
I think Imagemagick converts ico to png. I know I did it once, and I know I got a whole bunch of different sized icons.

---

### Post by m.musashi on 2008-04-16
Hey, imagemagick totally worked. Not sure how I'll ever get all these converted, placed into the right folders by size and set up as a theme but I'm one step closer. Thanks.

---

