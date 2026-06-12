---
title: "Where to get basic gimp help for noobs?"
date: 2010-03-19
forum: Art &amp; Design
---

### Post by Kurtosis on 2010-03-19
Hi all, is there a good forum for asking basic GIMP questions?  I don't see one on gimp.org, and imagine Ubuntuforums isn't exactly it.

I'm just trying to draw a straight line on a screenshot following the [GIMP tutorial]("http://www.gimp.org/tutorials/Straight_Line/").  While the method works in a new blank image, it's not working on my screenshot.  

Not sure what the problem is, or where to find help, and imagine I'll have other such basic questions as I use it more.

Thanks.

---

### Post by Tom Collier on 2010-03-19
Read up on how to use layers.  Ctrl-L toggles the layers dialog box. Don't make the mistake of trying to get all the elements of your image onto a single layer until you are ready to export. Reason to come...

Your screenshot should be the bottom layer, add a layer with transparency on top of that layer, use the pencil tool, left click where you want your line to begin then move the cursor to the point where you want your line to end, hold ctrl and left click again.  If you want to add text, click the "T" tool and text will automatically add another layer. (You're up to 3 layers now.)

Save your original file in Gimp's native xcf format, then export your image in the format that you want.  Assuming jpg, it'll "flatten" the image, i.e. reduce all layers to 1 layer.

The trick is to save your working file as a Gimp file, then export to the other formats you might want to use.

---

### Post by Newfoundlander on 2010-03-19
Search on YouTube for "GIMP tutorial" and you'll find some excellent videos and tips.

---

