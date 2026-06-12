---
title: "Help with Macromedia Flash"
date: 2010-06-05
forum: Art &amp; Design
---

### Post by thedarklaith on 2010-06-05
Hi all, hope this is in the right section :)

There are 2 things I'm trying to do with flash. This is for a photo gallery kind of thing.

Firstly I'm trying to get a button to press and hold, so the action continues while the button is pressed. (this is for scrolling)

The second is that I want the effect of the down (say for example the photo changes size when I press it) to stay after I release the picture.

---

### Post by alex.rayu on 2010-06-07
You need to use a flash buttons instance. Or you can create your own movie clip and add script to have the desired behavior. Does not quite relate to Ubuntu.

---

### Post by thedarklaith on 2010-06-07
Well you can get Flash on Ubuntu and I've gotten help on Javascript before on here and I like the Ubuntu community.

Anyway, if you know how to do it could you please tell me.

---

### Post by thedarklaith on 2010-06-07
If it helps here is the .fla file:
[http://www.sendspace.com/file/8db2zt](http://www.sendspace.com/file/8db2zt)

---

### Post by alex.rayu on 2010-06-10
Its been a few years since I did ActionScript, but as far as I can tell from your FLA file, you should create a function that moves the gallery some 3 pixels to the right (the .x attribute) and that is looped - probably with timer-based loop. Then, you should link an onrelease event to change a variable that would serve a condition on which looping breaks.

---

