---
title: "Gimp Alpha Channel Transparency Help Please"
date: 2007-02-06
forum: Art &amp; Design
---

### Post by rsambuca on 2007-02-06
Hi all,  I have found a picture of earphones that I want to turn into a desktop icon.  To get rid of the background and make it transparent, I went 

Layer -> Transparency -> Color to Alpha  

The background turns transparent, and the icon looks pretty good.  The one thing that bugs me is that the closest earphone contains some white in it and also gets slightly transparent.  Does anyone know how to mask that earphone so that it doesn't become transparent when I do the Alpha Channel thing?

I have attached two pictures.  1. is the starting picture I uh, found, and 2. is a snapshot of the icon on my desktop - as you can see, the background comes through the earphone.

---

### Post by ndru on 2007-02-06
Hi, you can use the Fuzzy Selection Tool/Magic Wand to select just the regions you want to apply transparency to (i.e. the area around the earphones).

---

### Post by Nodapic on 2009-04-07
Hi,
I am really struggling on how to proceed once I have the area selected; how do I add transparency? I just can't get it to work...
Thanks!

---

### Post by unutbu on 2009-04-07
In the Layers Dialog (Windows>Dockable Dialogs>Layers), right-click on the image layer. 

Select "Add Layer Mask".
A new window will pop up. Click "Add".
There should now be a white square next to the image in the Layers Dialog. This is the layer mask. The layer mask is a grayscale image which can be manipulated like any other GIMP image, but which is interpreted by GIMP in a special way. White represents 100% alpha (opaque), Black represents 0% alpha (transparent). Intermediate grays correspond to intermediate values of alpha.

Note that you can left-click on the image and its mask in the Layers Dialog. Only one can be selected at a time. If you use painting or selection tools, they will only affect one or the other. So left-click on the image in the Layer Dialog, and then go about selecting the areas that you want to be visible or transparent.

Once you have the selection, left-click on the layer mask in the Layers Dialog. Drag black color on to the image to "bucket fill" the selected areas with black color. Since the layer mask (not the actual image) was selected, the black color will be painted on the layer mask. 

Whereever the layer mask is black, the main image window should now look transparent. If the parts you want transparent are instead opaque and vice versa, simply select Colors>Invert to flip the black and white parts of the layer mask.

You can blur the layer mask to smooth the transition between opaque and transparent areas.

For many purpose, this is all you have to do to add transparency to an image. But if you want to, you can make the change permanent by right-clicking the layer in the Layers Dialog and selecting "Apply Layer Mask".

---

### Post by kayosiii on 2009-04-08
for hard edged shapes like the headphones I would tend to favour the bezier tool to create a path around the headphones. and turn said path into a selection and then invert it before removing the background. A bezier if placed right should get all the edge pixels at the right levels of transparency and give very smooth results.

---

### Post by BRAXS69 on 2009-04-08
well you could make another layer under it and re apply the white to the areas. 

but the way i probably would do it, is duplicate the image and the top layer using the pen tool cutout everything else but the headphones. and then use color to alpha on the bottom layer so we would preserve the shadows.

also if the attacked image of the head phones it what you are working with i recommend you use a larger image. higher the res the more crisp it will look.

---

### Post by Neverest on 2012-06-04
Thanks Unutbu! That info was awesome!

---

### Post by overdrank on 2012-06-04
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

