---
title: "GIMP Problem"
date: 2010-02-13
forum: Art &amp; Design
---

### Post by kenpdx2 on 2010-02-13
[SIZE=3]On a single layer with a white background, how do you move a line drawing around within that same single layer without moving the whole layer and without leaving a big hole in the layer exposing all that checkerboard business?
[/SIZE]

---

### Post by Minipalmer on 2010-02-14
Here's your problem: That black line is merged on the same layer with the white background. So when you move the black, you move the white.

Here's what I recommend: Make a new layer, call it "White Background". Look over at your layer list (probably on the right window) and make sure it is down below the other layer you are working with.

Now, with your original layer, change the layer mode (a drop down menu above your layers) to "multiply". This will make it so only the black shows. Now, you can move the black around anywhere you want it.

---

### Post by mcduck on 2010-02-14
> **kenpdx2 said:**
> [SIZE=3]On a single layer with a white background, how do you move a line drawing around within that same single layer without moving the whole layer and without leaving a big hole in the layer exposing all that checkerboard business?
[/SIZE]

You don't. You draw the line on another layer. That's what the layers are for.. ;)

---

### Post by 23dornot23d on 2010-02-14
Create a base layer that is white ... the background layer ..... 

See other thread for a total answer ......

I would like to see an example of exactly what you are doing to make it as simple as possible for you  .....

[http://ubuntuforums.org/showthread.php?t=1406417](http://ubuntuforums.org/showthread.php?t=1406417)

Why have you done two threads, for almost the same question ....

---

### Post by durand on 2010-02-14
It seems like inkscape would be a more useful program for what you want to do. [website]("inkscape.org") [install]("apt:inkscape")

Also, if you use a more descriptive title for your thread, you may get more help..

---

### Post by SoFl W on 2010-02-14
See your other (3rd?) thread on this same topic.
[http://ubuntuforums.org/showthread.php?t=1406356](http://ubuntuforums.org/showthread.php?t=1406356)

---

