---
title: "Gimp image transparency"
date: 2009-12-22
forum: Art &amp; Design
---

### Post by DJ . on 2009-12-22
Just upgraded to Ubuntu 9.10 and I need to know how to make a transparent eraser in gimp. If there is no way, is there another program that supports transparency? 

I know I am using the correct filetype(png)

Thanks

---

### Post by SunnyRabbiera on 2009-12-22
Odd, you didnt flatten your image right?

---

### Post by hyperdude111 on 2009-12-22
Gimp DEFO supports transparency.

I have never had an issue with it but you could try making a new image from scratch then opening the file you want to edit as a layer. 

To see it supports trans just go layers - new layer - then transparent.

---

### Post by Exodist on 2009-12-22
> **DJ . said:**
> Just upgraded to Ubuntu 9.10 and I need to know how to make a transparent eraser in gimp. If there is no way, is there another program that supports transparency? 

I know I am using the correct filetype(png)

Thanks

Pardon me, as I dont fully understand what you are asking. But maybe this below will help.

GIMP supports transparency.
On the Layers Panel you can adjust the layers individual Opacity setting from any value from 0.0 to 100.0.

If you are trying to REMOVE the transparency from an image just simply add a new background to the image and then re-save the image.

---

### Post by Peter76 on 2009-12-22
You are probably working on a layer / image without transparancy. Right click on the layer and go to add alpha channel. Now when you use the eraser it will erase to transparency.

---

### Post by DJ . on 2009-12-22
> **Exodist said:**
> Pardon me, as I dont fully understand what you are asking. But maybe this below will help.

GIMP supports transparency.
On the Layers Panel you can adjust the layers individual Opacity setting from any value from 0.0 to 100.0.

If you are trying to REMOVE the transparency from an image just simply add a new background to the image and then re-save the image.
Sorry I didn't really explain that much. What I am Trying to do is to make the white background transparent. When I use the layers opacity it makes everything transparent.
EDIT: Fixed the problem thanks to Peter76

---

### Post by Exodist on 2009-12-22
> **DJ . said:**
> Sorry I didn't really explain that much. What I am Trying to do is to make the white background transparent. When I use the layers opacity it makes everything transparent.
EDIT: Fixed the problem thanks to Peter76
Also if you start a new file in GIMP and accidently choose to have a background instead of a transparent one. You can easily just create a new layer then delete the original background. Sometimes you have to move the transparent layer to the background position tho. I get in a hurry sometimes and have to do this.

---

### Post by pri2sh on 2009-12-23
nice infor thanks.

---

