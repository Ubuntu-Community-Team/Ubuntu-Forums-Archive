---
title: "Requesting GIMP help."
date: 2009-05-15
forum: Art &amp; Design
---

### Post by Celestika6 on 2009-05-15
What I'm trying to do is turn one image transparent (the entire image, not just the background) and lay it over another image so that it creates an effect almost like a picture watermark. I can't find any half decent online tutorials so if anyone knows how to do this, please please explain.

---

### Post by Saint Angeles on 2009-05-15
paste it as a new layer and lower the opacity?

---

### Post by shinkaide on 2009-05-15
> **Celestika6 said:**
> What I'm trying to do is turn one image transparent (the entire image, not just the background) and lay it over another image so that it creates an effect almost like a picture watermark. I can't find any half decent online tutorials so if anyone knows how to do this, please please explain.

See if this helps...

**1.** Open the base image in the GIMP (the one you want to put a watermark on).

**2.** Press CTRL + D to create a duplicate image, and then save it as *yourfilename*.xcf ... then close the previous image.

**3.** Using your file manager, look for the image file you want to use as a watermark. Once you've found it, drag the icon of the file into the GIMP window of ***yourfilename*.xcf** ... this will load the image into the open window on top of the base image.

**4.** Now notice your **layers** dialogue. You should have two layers in there: first, one corresponding to the base image, and then above that should have the name of the image you dropped into the window. Select the second layer.

**5.** Still in your layers dialogue, above the layers, there should be a slider labeled "**Opacity**". A value of 100 means the layer you selected in #4 is completely solid. A value of 0 means the opposite. It's up to you to choose how transparent you want it to be.

**6.** Once you've finished whatever editing you've done and you're raring to put your creation to good use, save your current file as it is, then press CTRL + D again to create a duplicate. This is so you won't lose the ability to edit/re-edit your work.

**7.** Close the previous window with the.xcf file. Focus on the duplicate window you just created, and right click on your layers dialogue. Select the option that says "**Flatten Image**" (If you are presented with any options, the default selections should work well most of the time).

**8.** Save your work as .jpg or .png, or whatever file format you want it to be in.

That's it. I hope this helps a bit.

---

