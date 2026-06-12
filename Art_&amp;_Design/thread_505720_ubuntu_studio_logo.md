---
title: "ubuntu studio logo"
date: 2007-07-20
forum: Art &amp; Design
---

### Post by jijin on 2007-07-20
does anybody have a good vector for ubuntu studio?

any vector format will do. I have most vectoring programs and can convert most others.

svg would be perfect though


thanks in advance

EDIT: I have looked in the official UbSt art site and there is no vector.

---

### Post by Paul820 on 2007-07-20
Is this what you want? [https://wiki.ubuntu.com/UbuntuStudio/Artwork/OfficialFeisty]("https://wiki.ubuntu.com/UbuntuStudio/Artwork/OfficialFeisty")

---

### Post by jijin on 2007-07-20
there is no vector there ... thanks though... I'm looking for a vector of that logo, so I can easily resize it.

[http://en.wikipedia.org/wiki/Vector_graphics](http://en.wikipedia.org/wiki/Vector_graphics)

preferably in a svg ( [http://en.wikipedia.org/wiki/Scalable_Vector_Graphics](http://en.wikipedia.org/wiki/Scalable_Vector_Graphics) ) 

again thanks ahead of time.... also if sombody does have one how do we get the official artwork updated for the gutsy release of UbuStu?

---

### Post by Paul820 on 2007-07-20
It is an SVG, i just downloaded it my desktop. I'll put it here for you:

---

### Post by jijin on 2007-07-20
> **Paul820 said:**
> It is an SVG, i just downloaded it my desktop. I'll put it here for you:

erm ok... I didn't see one there

but THANKS! :D

---

### Post by jijin on 2007-07-20
is there a cleaner, higher resolution version?

no offence but that one is ugly and still has the gradiated glow.

Thanks though paul

I tried todo something with it but it didn't quite work

---

### Post by Paul820 on 2007-07-20
All i can really suggest is using that image as a reference, having it on it's own layer in inkscape and tracing round it. Shouldn't take too long to do using paths/bezier curves. You can get the font through synaptic: 'sudo apt-get install ttf-ubuntu-title' That's half the work done for you. :) I don't know what the other half of the logo font is though, google might tell you. The gimp opens SVG's but i wouldn't suggest using that as it ruins them. 

Oh, and you didn't offend me. :) Good luck!

---

### Post by richardq on 2007-07-20
> **jijin said:**
> is there a cleaner, higher resolution version?

no offence but that one is ugly and still has the gradiated glow.

Thanks though paul

I tried todo something with it but it didn't quite work

I just downloaded it and opened it up in Inkscape. From there I was able to 'ungroup' the object and separate everything into it's component pieces. So if the reflection glow is not what you want, you can take the rest of it without that. I saw no gradient problems on my end.

What application are you using to view/edit the svg file? 

Since it is a scalable vector graphic I can export it to a variety of resolutions without losing quality. It's not something you can just cut and paste into the Gimp (I don't think).

---

### Post by Paul820 on 2007-07-21
> **richardq said:**
> I just downloaded it and opened it up in Inkscape. From there I was able to 'ungroup' the object and separate everything into it's component pieces. So if the reflection glow is not what you want, you can take the rest of it without that. I saw no gradient problems on my end.

What application are you using to view/edit the svg file? 

Since it is a scalable vector graphic I can export it to a variety of resolutions without losing quality. It's not something you can just cut and paste into the Gimp (I don't think).

How do you do that richardq? I have not really used inkscape that much but that sounds like a handy thing to know.

---

### Post by richardq on 2007-07-21
> **Paul820 said:**
> How do you do that richardq? I have not really used inkscape that much but that sounds like a handy thing to know.

Ok. First you open up the svg file in inkscape.

When you click on it, it will be one single large object (including the reflection).

If you look on the status bar at the bottom of the window while it is selected, it will tell you that it is a group of 17 objects. This means that it is composed of 17 objects but has been grouped together as a single object.

While the object is selected, go Object->Ungroup in the menus. This will split it up. You'll see now that all the objects are selected separately.

Hit ESC to deselect all objects and then click on the part you want. If you want to select more than one part, hold shift while clicking. You can then move these pieces around if you like or stretch and modify them.

Now if you want to create a bitmap image (png file) of part of the image, then select the objects you want to export, and then choose File->Export Bitmap...

Pick the output filename and path and the size of the bitmap you want to create. The beauty of working with a n SVG (vector format) is that you can pick virtually any resolution you want. So you could export just the ubuntu studio icon to a 100x100 png file or a 1500x1500 png file.

Note: It will only export directly to a png file. So you'll then have to use another app (like GIMP) to convert the png to jpeg if you need it.

Hope that helps.

(I'm working on a site with another guy that has lots of inkscape screencast tutorials at [http://screencasters.heathenx.org](http://screencasters.heathenx.org) if you want to check it out.)

---

### Post by Paul820 on 2007-07-21
Thanks very much, i never knew you could do that. I only noticed that it had one layer when i opened it up, so i thought nothing could be done to it apart from tracing it like i said above. Great tip, thanks :)

---

### Post by jijin on 2007-07-21
> **richardq said:**
> Ok. First you open up the svg file in inkscape.

When you click on it, it will be one single large object (including the reflection).

If you look on the status bar at the bottom of the window while it is selected, it will tell you that it is a group of 17 objects. This means that it is composed of 17 objects but has been grouped together as a single object.

While the object is selected, go Object->Ungroup in the menus. This will split it up. You'll see now that all the objects are selected separately.

Hit ESC to deselect all objects and then click on the part you want. If you want to select more than one part, hold shift while clicking. You can then move these pieces around if you like or stretch and modify them.

Now if you want to create a bitmap image (png file) of part of the image, then select the objects you want to export, and then choose File->Export Bitmap...

Pick the output filename and path and the size of the bitmap you want to create. The beauty of working with a n SVG (vector format) is that you can pick virtually any resolution you want. So you could export just the ubuntu studio icon to a 100x100 png file or a 1500x1500 png file.

Note: It will only export directly to a png file. So you'll then have to use another app (like GIMP) to convert the png to jpeg if you need it.

Hope that helps.

(I'm working on a site with another guy that has lots of inkscape screencast tutorials at [http://screencasters.heathenx.org](http://screencasters.heathenx.org) if you want to check it out.)

Your awesomeness is intense!

---

