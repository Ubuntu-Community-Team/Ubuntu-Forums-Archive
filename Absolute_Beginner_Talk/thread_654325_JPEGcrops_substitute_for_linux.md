---
title: "JPEGcrops substitute for linux"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by noynac on 2007-12-30
I regularly use a windows utility, jpegcrops, that performs the single function of cropping digital images to proportions set by the user . The user determines the area to be cropped by moving/resizing a frame on a large thumbnail of the image (very important). The beauty of this utility is that you can easily crop 30 digital photos in 60 seconds or less.

Linux has a number of utilities that allow you to crop images but they all take too much time. Does anyone know of a linux utility similar to jpegcrops?

BTW, jpegcrops uses lossless routines to avoid a loss of image quality, and this is certainly a desirable feature.

BTW (2), I haven't tried JPEGcrops under Wine, so that may be a possibility.

Thanks

---

### Post by p_quarles on 2007-12-31
Short of trying JPEGcrops in Wine, you could try this:
showfoto

It's KDE-based, but regardless of the environment you're running, it's a very lightweight and fast photo viewer that allows you to crop and perform other basic editing functions. I'm not certain that it will be quite *as *fast as the one you're looking to replace, but it's the best one I could find in the repos.

---

### Post by sloggerkhan on 2007-12-31
There's a nautilus plugin that resizes images from a right click menu.
nautilus-image-converter
from synaptic.

---

### Post by noynac on 2007-12-31
@ P_quarles. Showfoto (which apparently is part of the larger DigiKam program) does ratio cropping, which is what I need. Thanks for the suggestion--I'll give it a try. 

@ Sloggerkhan. I need the ability to manually select the crop area, so I don't think the Nautilus plugin would do the job. I appreciate the response, though. 

The following is a screenshot of JPEGcrops:

[http://ekot.dk/programmer/JPEGCrops/pic/0.6.12b/JPEGCrops0.6.12b_02.png](http://ekot.dk/programmer/JPEGCrops/pic/0.6.12b/JPEGCrops0.6.12b_02.png)

It's an unusual program because it does so little, but for someone who processes many digital photos, it's immensely useful.

---

