---
title: "merging images"
date: 2009-03-17
forum: Art &amp; Design
---

### Post by Joe_Linux on 2009-03-17
I have included 2 images one of a cd cover and one of text to put on that image. How would I merge these two images so that the text sits on top of the cd cover ? (please see 2 files included). Both were made with Gimp. 
Thanks Joe

---

### Post by abn91c on 2009-03-17
the text need to be floating layer

---

### Post by dtom2444 on 2009-03-18
i guess the easiest way would be to set the layer mode of the text to "Overlay". Question though, why is your "cd2.jpg" image soooo big?

---

### Post by anaconda on 2009-03-18
Basically.. 
Install and open krita.
Then open one of the pictures in it, and 
select "Layer>New>Insert Image As layer"
And select the another image.

Now you have both images in same picture one over the other. Then you may need to use 
"Layer>scale layer" to match the sizes of the layers.

Hey.. and it seems that the image with the text has WHITE background.. not good. the background coulour is supposed to be transparent so that the 2nd picture will show throug the topmost one..
But no problem. Select the layer with the text and use the magic wand selection tool from the left toolbar to select the text.. and then copy and paste to new layer.. (which will have transparent background....)

Krita is an exellent program.. cant wait for to new version of it, which will come with koffice2... whenever they get it to be stable..

---

### Post by hessiess on 2009-03-18
Never save images which sould be overlayed onto anouther image it a format that dousent support alpha, and avoid using lossy formats like jpg as much as posable.

---

### Post by Ben Crisford on 2009-03-19
***Open the .xcf> Make a new layer> Put the text on it> Set the mode to overlay***

I think that'll do it...
If i'm wrong then please tell me, i'm a bit of a newb in gimp, but it would've worked in paint.net :).

---

