---
title: "Weird GIMP Problems with window refresh"
date: 2012-07-07
forum: Art &amp; Design
---

### Post by skullmunky on 2012-07-07
I recently upgraded to 12.04 and now I'm having all kinds of bizarre problems with Gimp 2.6.  I removed and re-installed GIMP, and wiped the .gimp-2.6 directory, and the problems remain.  Here are a few:
 
1. Resizing an image hangs GIMP (Image->Scale Image)

2. Copying and pasting creates new layers, but the new layers are invisible.  They appear in the Layer Dialog and have correct thumbnails, but cannot be viewed in the actual document.  The Visibility buttons next to the layers don't function.

3. I can create new layers, but sometimes the layer boundary size seems to be locked to a smaller dimension, even after doing Layer->Layer to Image Size

4. Paintbrush and pencil work as expected, but other operations such as Fill and Gradient have no effect.

5. Overall, what seems to be happening is that operations that involve blitting blocks of pixels are not refreshing in the document window.  The operations actually are working, behind the scenes, doing the correct things to the data, they just aren't appearing in the window.  Using the paint, pencil, or eraser tools makes the refresh occur.  

Example:

1. create a new document, 256x256, RGB, transparent background.
2. create a new layer
3. fill the new layer with a Mandelbrot (Filters->Fractal Explorer).  Notice the thumbnail in the layer dialog is updated with a little fractal, but the main Gimp window remains empty.
4. select the background layer (empty, behind the layer with the fractal)
5. using the Eraser tool, erase in the background layer.  This should not do anything, as the layer is already empty - however, the eraser strokes cause the top layer to refresh and the fractal becomes visible.  

The same is true for fill, gradient, copy and paste, etc.  In some cases refreshing is triggered by moving another window in front of the Gimp window.  

What on earth is going on?  Gimp has always been solid like a rock for me.  I'm totally flummoxed!

---

### Post by GreatDanton on 2012-07-08
If I were you I would delete Gimp 2.6 and install Gimp 2.8 which is way better and similar to Photoshop.

Take a look at this link and follow the instructions:
[http://www.unixmen.com/install-gimp-2-8-rc1-in-ubuntu-12-04-precise-pangolin-via-ppa/](http://www.unixmen.com/install-gimp-2-8-rc1-in-ubuntu-12-04-precise-pangolin-via-ppa/)

Edit: I didn't see that you upgraded you OS. If you upgrade your Os then this will likely be the problem.

---

### Post by skullmunky on 2012-07-08
Thanks - I'm installing 2.8 right now.  It looks like it has the three major featuress I've been waiting for for years - layer groups, in-window text editing, and single-window mode - brilliant! 

... 

Actually I misspoke in my question - I hadn't actually upgraded, I was thinking of another machine.  So I have no idea why this would've happened.  

...

Installation done.  Everything works now.  Hoorah!

---

### Post by GreatDanton on 2012-07-08
I am glad you solved your problem. Now just click on the thread tools and mark thread as solved :-)

---

