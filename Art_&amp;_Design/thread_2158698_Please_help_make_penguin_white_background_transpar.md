---
title: "Please help make penguin white background transparent but not penguin's chest"
date: 2013-06-30
forum: Art &amp; Design
---

### Post by snowweb on 2013-06-30
I'm using Gimp 2.8 and I have the GNU Penguin image on a white background, which I want to make transparent, while keeping the penguin (including his white chest) entirely opaque.

I tried following [this thread]("http://ubuntuforums.org/showthread.php?t=354976") (post #4) but when I got to the bit where it said:

> Drag black color on to the image to "bucket fill" the selected areas  with black color. Since the layer mask (not the actual image) was  selected, the black color will be painted on the layer mask.

Nothing happened at all, the black colour was not painted on the mask.

The thread was a 2007 thread, so perhaps it's not correct for the later versions. Any help, much appreciated.

---

### Post by Toz on 2013-06-30
With the layer mask selected, click the bucket fill tool to select it, then click on one of the selected regions on the image.

There is an easier way to do this though (using this image):
[ATTACH=CONFIG]244279[/ATTACH]
1. Make sure the image has the Alpha channel enabled (Layer->Transparency->Add Alpha Channel)
2. Select the region you want transparent.
3. Press the delete key.

Perhaps you could post the image you are using. If there is any bleeding between the transparent areas and the white chest, it will be tougher to do.

---

### Post by snowweb on 2013-06-30
> **Toz said:**
> ...Perhaps you could post the image you are using. If there is any bleeding between the transparent areas and the white chest, it will be tougher to do.

Thanks Toz. Here is the image:

[IMG]http://snowweb.net/images/penguin.gif[/IMG]

---

### Post by snowweb on 2013-06-30
> **Toz said:**
> ...
1. Make sure the image has the Alpha channel enabled (Layer->Transparency->Add Alpha Channel)
2. Select the region you want transparent.
3. Press the delete key...

I just tried your nethod above and I think your last statement applies:

> ..Perhaps you could post the image you are using. If there is any bleeding  between the transparent areas and the white chest, it will be tougher  to do.

Actually, what I attempted was selecting the parts that I don't want transparent and then inverting the selection, but it's not ideal because when you zoom in, what previously looked like a fairly crisp edge is actually gradiented or feathered from the full colour to the background colour and I have a job knowing what to do about that. The dilemma is if I select all white pixels, those pixels which were light grey, will continue to be light grey, but should that still be the case if for instance, the image is placed on a pink background? If I include them in the selection, then there is no feathering and the image looks jagged.

What would be great is if I could mask the penguin's chest (and include his eyes) and then, when I use "Colour to Alpha", everything inside the area I masked is ignored. Is there something like that please? 

Appreciate your help.

---

### Post by Toz on 2013-06-30
Follow the instructions I gave above:
1. Layer -> Transparency -> Add Alpha Channel
2. Select the "Fuzz Select tool. Here you might want to play around with the threshold value so you can select more of the background white (and lighter values). 
3. Click on the white background and press delete. You'll want to do this numerous time for this image (will also need to get the area between the U and X in the word Linux as well as the areas inside the P, O and R), or hold down the shift key and multi-select all those areas then press delete.
4. Save the file.

Here is a version with the Fuzzy Tool threshold set at 45.
[ATTACH=CONFIG]244286[/ATTACH]

---

### Post by snowweb on 2013-06-30
Perfect Toz. Worked a treat. Many thanks.

The result can be seen on [http://snowweb.net/](http://snowweb.net/).

---

### Post by Niva on 2013-07-08
That works mostly but I can still easily see the shadow around both the penguin and the letters, it really looks too sloppy if you intend to use it for professional purposes.  There's got to be a more accurate way of doing this.

---

### Post by Buntu Bunny on 2013-07-08
> **Niva said:**
> That works mostly but I can still easily see the shadow around both the penguin and the letters, it really looks too sloppy if you intend to use it for professional purposes.

Negative. The shadow keeps it from appearing too flat.

---

### Post by Niva on 2013-07-09
Double negative, if you want an actual shadow then make one. The original goal was to define the transparency 	accurately.  Right now it looks sloppy and unfinished.

---

### Post by Snowhog on 2013-08-04
Here is a 'clean' shadowed image for you.
[ATTACH=CONFIG]245075[/ATTACH]
Click to view. Click again to open in a new tab. Save image as.

---

### Post by ofnuts on 2013-08-17
OK, I'm late but just for the record...  The proper way to remove a uniform background (no jagged edges, no faint remnants) is this:
- Add alpha channel if not there: Layer/Transparency/Add Alpha channel
- Select the background with the Magic wand (if you have letters or other holes", shift-click on them t add them to the selection)
- "Select/Grow" the selection by one pixel (so that the selection includes the border pixels of the subject
- Colors/Color to alpha, using the background color (you can also bucket fill in "Color erase" mode, this is equivalent)

The explanation of the "magic" is [there]("http://gimpforums.com/thread-proper-subject-extraction-background-removal-and-background-painting").

---

