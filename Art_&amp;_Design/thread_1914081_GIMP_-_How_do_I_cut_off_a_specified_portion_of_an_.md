---
title: "GIMP - How do I cut off a specified portion of an image's resolution?"
date: 2012-01-23
forum: Art &amp; Design
---

### Post by The Flying Penguin on 2012-01-23
So I have a bunch of pictures (actually they are nutritional  labels) that are 450x375. The problem is that there is a huge white space on the bottom of them with no information. The labels should really be about 450x240 or so. What I need is for gimp to automatically remove the extra 135 pixels on the bottom and all of the information. I'm not talking about resizing the image, that will still leave me with a bunch of blank space at the bottom.

What I have been doing is creating a new image at 350x240, using the rectangle select tool to copy out the area of the original picture that I want, and then pasting it into the new image. The problem with this method is it's somewhat tedious given the amount of images I have. Also, getting everything to line up right isn't the easiest thing for me since I don't have the steadiest mouse hand.

So is there any way I can just tell GIMP to cut off so many pixels of an image and leave me with a new size (again, not resizing but actually eliminating pixels)?

---

### Post by guine on 2012-01-23
Im not sure about anything that can automatically resize images to preset sizes, but the crop tool(the little knife thats the 14th tool if going row by row) would cut out everything you dont want and you can crop either by selecting the area you want with the mouse or by entering the dimensions you want by keyboard.

---

### Post by prokoudine on 2012-01-23
> **The Flying Penguin said:**
> 
What I have been doing is creating a new image at 350x240, using the rectangle select tool to copy out the area of the original picture that I want, and then pasting it into the new image.

This is really counter-productive. This is what the Crop tool is for. For a small amount of images just use it with fixed width and height. For lots of 
images use ImageMagick ([http://www.imagemagick.org/Usage/crop/](http://www.imagemagick.org/Usage/crop/))

---

### Post by BcRich on 2012-01-25
> **The Flying Penguin said:**
> So I have a bunch of pictures (actually they are nutritional  labels) that are 450x375. The problem is that there is a huge white space on the bottom of them with no information. The labels should really be about 450x240 or so. What I need is for gimp to automatically remove the extra 135 pixels on the bottom and all of the information. I'm not talking about resizing the image, that will still leave me with a bunch of blank space at the bottom.

What I have been doing is creating a new image at 350x240, using the rectangle select tool to copy out the area of the original picture that I want, and then pasting it into the new image. The problem with this method is it's somewhat tedious given the amount of images I have. Also, getting everything to line up right isn't the easiest thing for me since I don't have the steadiest mouse hand.

So is there any way I can just tell GIMP to cut off so many pixels of an image and leave me with a new size (again, not resizing but actually eliminating pixels)?
Hi 
You could use David's Batch Processor which can be found under Filters>Batch>Batch Process...
(GIMP 2.6.10)
Click *Add Files* button under the *Input* tab to add all the files you'd like to crop.
In *Crop* Tab set *width* and *height* 450x240
Click the *Rename* tab if you don't want to overwrite the original images and add a prefix/postfix
Finally click the *Output* tab if you want to change the files format (eg jpg, png etc)
Then *Start*.
NB I usually make a copy of my folder that I'm about to batch process before starting the operation just in case something goes wrong.

---

