---
title: "How to add metadata to png file?"
date: 2007-07-27
forum: Art &amp; Design
---

### Post by eyemeansit on 2007-07-27
Hiya!

I have created a series of 50 .png images for use as a slideshow or screensaver. I would like to add image credits, authorship data, comments,etc. to each file, (as metadata, not as part of the image itself) but can't figure out how to do this. The .png's are artwork that I created in Blender/Gimp/Xara, and thus have no exif info such as what a camera would provide. Any ideas on how to do this? (Preferably GUI... command line, as in "ImageMagick" is beyond me!)

Thanks!

Les

---

### Post by Dragonbite on 2007-07-29
Imagemagick is the only one I know of, but I hope there is an easier one available.

---

### Post by eyemeansit on 2007-08-15
In the end, I had to convert these images to .jpg's, then I was able to do what I wanted using Digikam's Kipi plug-in tools. Apparently there is no standard format for metadata for .png's, and thus no standard tools to add metadata.

Thanks!

---

### Post by darkazurka on 2009-11-25
> Apparently there is no standard format for metadata for .png's
Because you and I don't know doesn't mean anything. Well it means something.

"It means we don't know"

---

### Post by Priswell on 2009-12-08
*I would like to add image credits, authorship data, comments,etc. to each file, *

So, not visible on the image, right?

Go to Image > Properties (or Alt + Return) then click the Comment Tag. A window will be available to type in data about the image. As well as authorship data, I include information about some of the colors, font name and anything else pertinent to creating the image.

---

### Post by eyemeansit on 2009-12-09
I assume you are talking about "Image>ImageProperties" in the Gimp. I found it. Thanks for the tip. :)

---

### Post by darkazurka on 2009-12-11
If Priswell is not meaning some feature in GIMP(which I checked, Yes! There is such a comment tab there too!), I think Priswell means some new Ubuntu version which supports this feature, without opening GIMP up. It certainly is more practical this way to use your file manager if it is only related to metadata.

Was that what you meant Priswell?

---

### Post by poikiloid on 2010-02-26
> **Priswell said:**
> *I would like to add image credits, authorship data, comments,etc. to each file, *

So, not visible on the image, right?

Go to Image > Properties (or Alt + Return) then click the Comment Tag. A window will be available to type in data about the image. As well as authorship data, I include information about some of the colors, font name and anything else pertinent to creating the image.


This is bad advice. Metadata is STRUCTURED. you are not supposed to add all that in the comment field. many of the data you listed have their own fields. use digiWF (works directly in nautilus) or digikam.

---

### Post by darkazurka on 2010-04-17
> **eyemeansit said:**
> In the end, I had to convert these images to .jpg's, then I was able to do what I wanted using Digikam's Kipi plug-in tools. Apparently there is no standard format for metadata for .png's, and thus no standard tools to add metadata.

Thanks!

Digikam is the exact program you will use (without plugins!) to change metadata in png's. This video (better download the highest quality video and open in VLC): [http://www.youtube.com/watch?v=Y0nd3awkkP4](http://www.youtube.com/watch?v=Y0nd3awkkP4)
shows some basics. It helped me, and now I'm using digikam for my png's like mad!

---

