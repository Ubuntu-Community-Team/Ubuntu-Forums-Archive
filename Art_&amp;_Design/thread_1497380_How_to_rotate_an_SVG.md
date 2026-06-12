---
title: "How to rotate an SVG?"
date: 2010-05-30
forum: Art &amp; Design
---

### Post by undecim on 2010-05-30
I'm an Inkscape noob, and Google has failed me.

Pretty straightforward question: How can I rotate a complete image in Inkscape?

---

### Post by aklo on 2010-05-30
Click on the anywhere on image once, you will see arrows at the 4 corners of the object.
If they point out it means you can increase or decrease the size of the image.

Now click a second time and you will see the arrows change. That will be the mode you want to be in if you want to rotate an image.

---

### Post by koostudios on 2010-05-31
Hi,
I don't think there's a way to actually rotate the entire image from Inkscape. I would imagine you could swap the horizontal and vertical dimensions of the canvas and then rotate all the objects on the canvas (Ctrl-A and then Rotate). That's how I'd do it, even though I've never had to do it before.
KOO

---

### Post by ysangkok on 2010-09-23
Sorry for bumping.

You can rotate an element in SVG by wrapping it in a group that has the transform="rotate(180 x y)" attribute.

If everything is already contained in a group (pretty common. If it's not you can wrap it in a group by using Control-G on all elements [select with Control-A]) you can just add the attribute to the tag. For example if the group looks like:

<g id="layer1">

you can change it to

<g id="layer1" transform="rotate(180 50 50)">

It says "50" here in both X and Y coordinates. This only works if your image is 100 units wide. Just use half the length.

Inkscape has a built-in XML editor you can use.

But actually you don't need the text editor, you can just select everything like mentioned in the previous post and wrap it in the group and then rotate. Sometimes Inkscape performs poorly on very big images though, so I think it's nice to know how to do it in the text editor. Makes it easier to automate too.

---

