---
title: "for advance gimp users only! How would you go about making a silhouette?"
date: 2007-06-09
forum: Art &amp; Design
---

### Post by Parasitesss on 2007-06-09
Well, |short and simply put|

FOR THIS:

[IMG]http://i92.photobucket.com/albums/l7/SCAPULAARTisdead/atrestdesign3copy.gif[/IMG]

1. How did they turn the trees into that brown silhouette?
2. How did they Color the trees brown?
3. HOW DO YOU TURN ANY IMAGE into a silhouette??

For this image:

[IMG]http://i92.photobucket.com/albums/l7/SCAPULAARTisdead/designcopy-1.gif[/IMG]

1. How did they turn the monster green?
2. and if you look at the grave stone crosses, it has a whilte outline, how do you do that?

---

### Post by King_Critter on 2007-06-10
I think I can help you a bit here.

One way (well, the only way I know of :P) of doing outlines is thus:

Let's say you have some text. First, duplicate it, then do Alpha to Selection on the bottom layer. Right click on the layer, go to Select>Grow. Grow it by a few pixels. Then take the bucket fill tool, select Fill whole Selection, choose your color, and click on the layer. Now, assuming I'm not remembering wrong, you should hove an outline. Enjoy. ^_^

---

### Post by maruchan on 2007-06-11
This effect is pretty easy to achieve with Inkscape, using the "trace bitmap" functionality, or whatever they're calling it. You simply reduce the number of traced colors to 2 or 3, then change the colors once your image has been converted to paths.

Alternately, you can just trace as black & white, then change the colors to whatever you want.

Silhouettes are simple - you can delete highlight & shadow colors from a traced image, or draw a quick path around a bitmap object and fill with a solid color.

There are ways to do this in GIMP too...I would probably try the Threshold tool combined with "colorize" and multiple layers...

---

