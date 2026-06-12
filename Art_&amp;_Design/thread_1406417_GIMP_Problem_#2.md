---
title: "GIMP Problem #2"
date: 2010-02-13
forum: Art &amp; Design
---

### Post by kenpdx2 on 2010-02-13
[SIZE=4]A layer has a line drawing with a white background.

How do you make the background transparent and then move the remaining line drawing across another layer below it, that has a [/SIZE][SIZE=4]white background and a [/SIZE][SIZE=4]line drawing, connecting the two line drawings?[/SIZE]

---

### Post by Minipalmer on 2010-02-14
Hi, I just posted an answer to your first question. I think it may also work for this question. Let me know if it does not.

Also, this is a fine place to get GIMP questions answered. But people are busy, so try and give them at least 12 to 24 hours before bumping or asking questions

---

### Post by mcduck on 2010-02-14
You'll have to select the white background, either by doing Select->By Color (also in the tool panel as "Select by Color Tool") and then clicking on some white area, or by using some of the selection tools (loke the Fuzzy Select Tool.

Either way, you won't get a perfect result as your drawing is probaly antialiased against the white background clolor, so you'll need to play with the selection tool options and the Treshold value to get a good selection.

When you have an acceptable selection of the white background you can just press the Del key (or select Edit->Cut to cut it away from your layer.

If you just have a black drawing against a white background you also have the option of simply setting that layer's blending mode to "Overlay" or "Darken Only" to make it appear as black drawing over whatever is in the underlying layers.

Still, whenever possible, you'd better off drawing on separate transparent layers. Of course if you are working with scanned drawings originaly made with pen & paper, for example, that's not an option and you'll have to paly with the selection tools to cut the white background away or use the blenfding modes to blend the layers together.

What comes to combining the drawings, it's best to keep things on separate layers as long as possible. Anyway, there are two ways to combine layers together. First, you can merge a layer to one under it by selecting that layer, and then Layer->Merge Down. Second, you can merge two or more layers together by hiding all the other layers , leaving only the ones you wih to merge visible, and then selecting Image->Merge Visible Layers. Both these options also appear in the right-click menu when you click a layer in the Layers panel.

---

### Post by oedipuss on 2010-02-14
Also, you can try the 'Color to Alpha' filter, in the Colors menu. 
The effect is more or less the same with selecting with the magic wand and deleting.

---

### Post by 23dornot23d on 2010-02-14
[SIZE=4]then move the remaining line drawing across another layer below it[/SIZE]

[SIZE=4]connecting the two line drawings?[/SIZE]

( These two parts of the statement sound like you need to select an area of the drawing to move it around ...... this if needed needs to be done after the following  )

Do you have an example of part of this picture ...... if it is like the previous user stated not a completely white background you may have to work on that first ......

**Colors -  desaturate **

( if its a colour photo you took of a black and white image )

It may even be scanned in ..... but Isolate the black and white first job .....
as white is not always pure white ..... in photos

Scanned images are ok as you can get that to just be black and white ......


Be nice to see an example of the photo or picture ..... and exactly what you are
trying to do with it ......



**Colors - threshhold - adjustment** ....... can be useful too bring the selection in from each side ..... makes the black and white stand out if its not a pure white background.


This has previously been stated .....

**Layer add Alpha Channel** if it is not already there ... click ..  on your layer

**Colors - Color to Alpha ..... **will isolate the black lines ..... if you choose white

_________________________________________________________

**Create a new background layer - that is perfect white** ....... 
make sure this is the bottom (base)  layer on your layer list ......

________________________________________________________

**Image mode greyscale** too if you do not need any color on it ..... 
should reduce the file size if its a big one .......

If you need to select part of the image and move it around .....

First select the layer in the layer dialogue with the lines on it .....

Select the part you want to move around ..... 

Edit cut ....

Paste ...... move it to where you want it .......

Then paste it as a new layer .........


Hopefully after that you will have a perfect job ......

Hope this helps ......

---

### Post by kenpdx2 on 2010-02-18
[SIZE=4]Thank you all for your help, _[COLOR=black]but I am still stuck[/COLOR]_.  Here's a new angle(question) from which to get at a solution to my problem:

How do you make the background of a float selection transparent so that you can line up perfectly with something on a lower layer?

[/SIZE]

---

### Post by hessiess on 2010-02-18
Reduce the opacity slider on the layer pallet.

---

### Post by kenpdx2 on 2010-02-19
[SIZE=4]Thanks again for all the help.  I am happy to report that I have made progress.  But I'm still a bit foggy on the following:

Two layers.  The bottom larger one has a white background with black font color text within it.  The layer above is smaller, transparent, and with [/SIZE][SIZE=4]black font color text.  A little bit of the text in both layers is the same exact text and I want to line them up perfectly.  I've managed to move around the bottom layer while the top layer stays put.  But I really want to do it the other way around.  I want to move around the top layer while the bottom layer stays put.  How do you do that?
[/SIZE]

---

### Post by 23dornot23d on 2010-02-19
Set your canvas larger to begin with -** image - canvas size**

Now with your two layers ,,,,, by pointing to the one that you know is the bottom layer you

can then move that around ......

This works because the mouse will only select the active layer that there is detail on .....

The canvas has to be big enough to allow the bottom layer to move within it though .....

hope that this helps ...... 

( you can also use a selection which may be better ..... by using a selection you might be able to avoid breaking the text )

wish I could see what you are working on ..... it would give me a better idea ..... all I can presume is house plans or

a design drawing ..... but the technique is to select the area that you want to move using either the lasoo select or the 

pen nib (paths) tool for cutting out odd shapes ..... this may make you selection easier ..... but the smaller selection

should always be you upper layer ....... and by selecting a black line on it ..... will allow you to move it around .....

---

