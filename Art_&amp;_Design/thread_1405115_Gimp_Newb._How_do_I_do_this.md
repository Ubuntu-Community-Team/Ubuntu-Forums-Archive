---
title: "Gimp Newb. How do I do this?"
date: 2010-02-12
forum: Art &amp; Design
---

### Post by Roasted on 2010-02-12
Two things. I'm making one large image based on a ton of small images together, kind of like a collage type thing. The images come together to form a design and they're all in black and white, and I want to apply some sort of a color image to the background which sites behind EVERYTHING else. How do I do that?

Secondly, for some reason there is a white blurb on the white canvas. Like if I disable the show background portion, it disappears showing me the dark gray/light gray boxes that form some sort of a checker-board like grid, and then there's the random white splot. I tried the eraser and whatnot but I don't know how to get rid of it. What can I do?

Also, this is the last thing I need to do before I'm done, so if it'd be easier for me to "grab" all of the contents of the image and paste them to a larger canvas that already has the background image in place, I'd be game for that too.

---

### Post by prshah on 2010-02-12
> **Roasted said:**
> kind of like a collage type thing.

Like if I disable the show background portion, it disappears showing me the dark gray/light gray boxes that form some sort of a checker-board like grid

Second question first: The "checkerboard" pattern you see indicates a transparent area. It will not show up in the image. It is merely a "placeholder" to indicate to the designer that the area so marked is transparent. If you save your image in a format that supports transparency (such as GIF or PNG) then it will retain the transparency; if you save it as a JPEG, it will be converted to the background color.

For your collage, I suggest you place your main / background image first. Then add a layer, and set it's transparency to 50%. Place your small images on this layer. You can play with the transparency settings once you have everything done.

Sorry, I don't know how you can (if you can) automate this process.

---

### Post by Roasted on 2010-02-12
> **prshah said:**
> Second question first: The "checkerboard" pattern you see indicates a transparent area. It will not show up in the image. It is merely a "placeholder" to indicate to the designer that the area so marked is transparent. If you save your image in a format that supports transparency (such as GIF or PNG) then it will retain the transparency; if you save it as a JPEG, it will be converted to the background color.

For your collage, I suggest you place your main / background image first. Then add a layer, and set it's transparency to 50%. Place your small images on this layer. You can play with the transparency settings once you have everything done.

Sorry, I don't know how you can (if you can) automate this process.

Well, I can't do that, since I already have the layers in place and now I'm trying to add a background layer. Plus like I said there's that white blurb that I can't seem to get rid of them, even with the eraser. Kind of weird...

Any other suggestions? I'm going to try and make this happen tonight...

---

### Post by Minipalmer on 2010-02-12
Hmm, I'm having a little bit of trouble understanding your dilemma, but I'll try to help.

Since you don't want to restart your image apparently, there is a way to add a background. Just make a new layer with "layer > new layer". A window pops up. Name it "Background". Find this "Background" layer on your layer list (right window) and click and drag it down to the very bottom of your list. Now it's acting as a background layer. If you would like to fill it with a color, just find your fill tool (paint bucket), pick a color, and click to fill. (When doing this, make sure you have the Background layer selected)

As for the "white blurb" you can't get rid of, it's probably part of one of your layers. I've had this problem before too, where there is a color splotch that I can't find. I just had to toggle the transparency (click the eye) of each layer until I found it.

---

### Post by Roasted on 2010-02-12
Great... new problem... luckily I saved the work yesterday, but I came home and my pc was off. We must have had an outage earlier today. I reopened the work in progress and it comes down as one layer, which is fine because I'm done with it, but the one layer IS the background image - with all of the pictures, white background, thumbnails, etc. The entire thing is 1 layer, and there's nothing separate from the background image vs the layers I applied.

Great... how can I work around this issue now? :( :(

---

### Post by Merk42 on 2010-02-12
What did you save it as?
.xcf is the file format for GIMP.  If you saved it as something else, jpg, png, gif, etc. Then it flattened it all and I'm afraid you'd have to do it over again (or depending on the image, re-cut it up with the marquee tool and paste into new layers)

---

### Post by Minipalmer on 2010-02-13
Yeah, when you save your images you'll to do it in .xcf, the Gimp layer format. I'm afraid there's not really much working around that.

On the bright side, now you won't have to worry about that annoying white blotch anymore!

---

### Post by 23dornot23d on 2010-02-13
Have you seen collage creator .... very quick and easy to use .....

[http://www.shapecollage.com/download-linux.html](http://www.shapecollage.com/download-linux.html)

Shape Collage ..... as soon as you download it and unpack it you can run it


Check the video first though ..... there is quite a lot you can do with it ,,, its quick and easy to use ......



I created this just now to check it works ok ..... this was just on default setting .... but there are many more ways .... of laying them out .... and spacing them too
you just drag a folder of photos onto it and it does the rest .........

[IMG]http://i50.tinypic.com/33dxjf6.jpg[/IMG]

---

### Post by Minipalmer on 2010-02-13
Wow! That's quite the tool! I'm not sure that's what OP is looking for, but I'll certainly take note of it.

---

