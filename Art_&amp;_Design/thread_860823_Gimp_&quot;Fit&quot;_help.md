---
title: "Gimp &quot;Fit&quot; help"
date: 2008-07-15
forum: Art &amp; Design
---

### Post by projectgonewrong on 2008-07-15
Okay so I have 2 maps that are both suppose to be of the United States and I want to overlay them.  Problem is the maps are different and don't line up as easily as I thought they would.

So I was wondering if there was a way to trace the bottom layer map and then make the other one just like liquify and fit to the same exact dimensions/angle/shape of the other.

---

### Post by miked2 on 2008-07-16
I think you need to open the maps in two layers in the gimp.  (Open one image then from the image's file menu use open as layers).  
Now using the Measure tool, measure the pixels between two prominent reference points as far apart as possible on layer a (dimension a), then switch to the other layer (we'll call it layer b) and measure the same distance in pixels (dimension b). You then need to scale one of the layers (from menu layer - scale layer).  
The scale layer dialog will display a width and a height.  You just want to change one of these so that the aspect ratios of the two layers remain the same, so just change either the width or the height, but not both.  I'll assume you're changing the width.  The new width you need is either:
to scale layer a - multiply existing width by (dimension b / dimension a), or, 
to scale layer b - multiply existing width by (dimension a / dimension b).  
If it's not close enough after the 1st attempt, you can repeat until the maps align to your satisfaction.  
(I'm about 90% sure I got the multiplication the right way round, but you get the idea).

---

