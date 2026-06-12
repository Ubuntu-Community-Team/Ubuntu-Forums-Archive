---
title: "Creating a Velvet Texture in Gimp?"
date: 2010-11-15
forum: Art &amp; Design
---

### Post by MasterNetra on 2010-11-15
I was wondering if anyone know any good tutorials on how to create a smooth flat velvet texture in Gimp or know how to do it themselves?

---

### Post by MasterNetra on 2010-11-17
*bump*

---

### Post by bigsmitty64 on 2010-11-18
Not sure if this is exactly what your looking for but, I'm subscribed to the user who made [THIS]("http://www.youtube.com/watch?v=IFZ8cQ2r2Dg") video. Maybe this will help. Lotsa good tutorials on her channel.

---

### Post by ursaminor on 2010-11-29
Find a good velvet image with a smooth texture. After cropping to desired size, go to Filters>Map>Make Seamless to make the image tileable or a tile. Load the image onto your Desktop Background to see if it will work.

Or use the image provided--no restrictions attached.

---

### Post by MasterNetra on 2010-12-06
> **ursaminor said:**
> Find a good velvet image with a smooth texture. After cropping to desired size, go to Filters>Map>Make Seamless to make the image tileable or a tile. Load the image onto your Desktop Background to see if it will work.

Or use the image provided--no restrictions attached.

That is pretty much what I am asking in terms of what kind of velvet, just wanting to know how to make it from scratch.

---

### Post by Tenzy on 2010-12-08
Just had a play around in gimp for you and this is what the end result is.

These are the notes I made while doing it. I hope you can decipher them and my apologies in advance if they are not correct. This is the best I can do in such a short time.

filter -> artistic -> clothify
duplicate layer
gausian  blur duplicated layer by 2
filters -> map ->bump map background layer with blurred layer
on bg layer use g'mic filter "pen drawing". set  amplitude to 0.68 (google for g'mic plug in)
 in g'mic do softglow still on the same layer
scale image 25%
use the make seamless filter
save as .pat in pattern folder

make new image fill with pattern you just saved.

scale image 175%
filters -> enhance -> sharpen 33
duplicate layer 
(might have flipped the layer here with the flip tool, not sure)
map -> displace X -46 Y -54

colors -> brightness and contrast - move the contrast up.

---

