---
title: "Hoigh quality increase of the size of a photo with the tools available in Ubuntu"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by siddartha on 2007-12-07
Hello,

I was wondering about how to make a digital photo larger. I wanted to give some for publishing and I was told that 10MP is not good enough. Now, I changed from jpeg to raw as there are some pixel losses on the sides when converting. But from here on I have no idea what to do. I need something that goes for quality irrelevant of the computing time.

Cheers,
Sidd

---

### Post by disturbedite on 2007-12-07
there is a rule of media, you can't make something better quality than it already is.
as for images, whenever you try to make them larger, they degrade in quality, that is unavoidable.  there is however different techniques that yield varying results.
here is a rule of thumb:
when shrinking an image, use the (bi)cubic filter.
when enlarging an image use the lanczos (aka sine) filter.

not all programs allow you choose the resampling/resizing filter tho.  but the better ones do.  i'd recommend gimp.

---

### Post by SOULRiDER on 2007-12-07
I dont know how imagemagick (yes, with a ck) does it, but you might wanna give it a try.

---

### Post by Hospadar on 2007-12-07
well as a rule, if you are enlarging a photo, the quality is going to get worse.  there is just no way to magically squeeze more resolution out of an image than there already exists.  If you're shooting 10MP raw files, I would look into loading them into gimp with UFRaw (available from synaptic)  It gives some really good options for the raw importing process.

UFRaw is really a backend for dcraw, a command line tool for converting raw files.  I would suspect that dcraw (and thus UFRaw) will give you better results than just shooting directly as a jpeg.  to use UFRaw, just open your raw files with UFRaw and you can do some basic modifications before you convert them and load them into gimp.  You might also want to look into learning the command line options for dcraw if you want to be able to do this quicker and more automatically.

That said, there are some things you can do if you must enlarge an image.  you can look into sharpening tools in gimp, these will sometimes help, especially with images that have well defined figures.  there are also different enlargement algorithms available in gimp that may provide better results for different images, depending on the image content.

Hope this (sort of) answers your question!

---

### Post by firefly76 on 2007-12-07
10 MP is fine for very large prints, I don't know who told you that is not good enough.

Anyway, for the very best in image quality you are on the right track.  As I am into photography as well, I have a few suggestions:
[LIST]
[*]Keep shooting in RAW mode for the best quality, and post-process those files later.  This way you suspend the in-camera processing for later and save ALL the sensor data, and retain control of the final processing (this also lets you take advantage of newer software, since the camera's built-in conversion is probably not the best).  This process is known as the digital darkroom.
[*]If you want to keep your Linux distro clean of all non-free software, use dcraw or ufraw.  ufraw is just basically a GUI for dcraw.  This will allow you to process your RAW files and export them to TIFF or other.  You can then convert to whatever with ImageMagick.  dcraw is command line only and ufraw is point 'n click, but is still quite technical.
[*]The program I most highly recommend is LightZone.  Depending on your processor you can download one of several versions built for Linux.  A working java JRE is required.  Lightzone for Linux is maintained by a developer who loves Linux who apparently works for Light Crafts, but it is NOT open source software, although you can legally install and use it for free on Linux.  This program allows you to artistically and intuitively process your RAWs and export them to JPEG or TIFF.  It also allows you to save all changes to the negative (original RAW) by recording the changes you made in a separate .lzn file, thus preserving the original.  A very nice program, one which I highly recommend.
[*]Aside: To maintain the highest quality in Lightzone, shoot in RAW, process in LightZone, crop to your required aspect ratio and export as a TIFF.  This process will give you remarkable prints.
[/LIST]

Hope that helps.

---

### Post by firefly76 on 2007-12-07
> **disturbedite said:**
> 
not all programs allow you choose the resampling/resizing filter tho.  but the better ones do.  i'd recommend gimp.

Sorry to quote you disturbedite, but I would stay away from the GIMP and only use the very similar CinePaint if you're going to go this route.  CinePaint offers 16bits while the GIMP support 8.  For everyday graphics the GIMP is great, and I use it all the time, but for prints, where you want to preserve as large a dynamic range as possible, you need CinePaint.  If you spend all this time shooting RAW, developing with dcraw or LightZone, then load and save in the GIMP for some reason you are undoing all the quality you have just salvaged.

---

### Post by siddartha on 2007-12-07
Eh, I know how to develop raw files and usually I go straight to jpg with the in-camera processor. But my photos are like 29M uncompressed. Now, check these demands as an example of what the real world demand.

[https://secure.alamy.com/stock-photography-guide.asp]("https://secure.alamy.com/stock-photography-guide.asp")

In the end it's not a matter of weather this is right or wrong. Photoshop is the most used tool, but Photoshop is expensive and should be run in Wine which would make it even less usable.

---

### Post by disturbedite on 2007-12-09
> **firefly76 said:**
> Sorry to quote you disturbedite, but I would stay away from the GIMP and only use the very similar CinePaint if you're going to go this route.  CinePaint offers 16bits while the GIMP support 8.  For everyday graphics the GIMP is great, and I use it all the time, but for prints, where you want to preserve as large a dynamic range as possible, you need CinePaint.  If you spend all this time shooting RAW, developing with dcraw or LightZone, then load and save in the GIMP for some reason you are undoing all the quality you have just salvaged.
i meant for resizing, i don't think color is a factor in resizing.

but even if it is, fair enough.  but by that argument i could argue not to use cinepaint cuz adobe photoshop cs3 has 32bit support.

---

### Post by firefly76 on 2008-02-14
> **disturbedite said:**
> i meant for resizing, i don't think color is a factor in resizing.

but even if it is, fair enough.  but by that argument i could argue not to use cinepaint cuz adobe photoshop cs3 has 32bit support.

Good point, fair enough.

---

### Post by siddartha on 2008-02-14
disturbedite and firefly: you both have a good argument. in my particular case, gimp is out of the question unless it is the only tool available mainly because of the 8bpp. about photoshop going 32bpp, from my part they can go all the way 1024bpp - nikon supports 12bpp in raw photos and in latest cameras went up to 14bpp. meaning Cinepaint is excellent for the near future as well.

now, i understood that cinepaint split quite a while ago making the current code different in cinepaint and gimp. how do they relate on this interpolation/growing up side? are they using the same algorithms? how are they implemented?

---

### Post by disturbedite on 2008-02-14
sorry, i don't know the answers to those questions.
one other program of the same nature i'm finding quite nice is krita.  i don't know which processing color depths it supports, but it is nice nonetheless.

---

### Post by Mad_Dawg on 2008-02-14
If you mean by "10MP" 10 megapixals, then the quality is good enough to make a high quality poster sized pictures.

---

