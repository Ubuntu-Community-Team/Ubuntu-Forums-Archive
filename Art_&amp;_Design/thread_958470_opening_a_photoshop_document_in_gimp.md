---
title: "opening a photoshop document in gimp"
date: 2008-10-25
forum: Art &amp; Design
---

### Post by jerryroy on 2008-10-25
i want to know if there is a way to open a photoshop document in gimp

---

### Post by Half-Left on 2008-10-25
Yes you can but it doesn't show them proper if you use layer effects from Photoshop. Just open it like a normal file.

---

### Post by Merk42 on 2008-10-25
I believe fonts get rasterized too, unless that's changed in 2.6?

---

### Post by VeeDubb on 2008-10-25
I don't know about the fonts, but from my little bit of testing, 2.6 handles fully layered PSD files with no problem.

---

### Post by banago on 2008-10-26
GIMP 2.4 does not open properly PSD docs. Let's hope version 2.6 will fix this, haven't tried it yet.

---

### Post by stephanvaningen on 2008-10-26
I've tried to open a .psd file with Gimp 2.6 without any success.

I've also tried other options:
 - Krita (from kde) - no success
 - Scribus - no success
 - convert - no success
 - plugin-installation GIMP - no success

Does anybody have a simple step-by-step or (last resort) an online function to upload a psd and download a png or eps or something?

---

### Post by VeeDubb on 2008-10-26
Hhmmm....   Not sure why you had trouble with 2.6.

I'm running Gimp 2.6.0, compiled from source, on Ubuntu 8.04 64bit(fully updated).  

I have found that this version of Gimp easily opens even highly complicated, fully layered PSD files (I have tried several). 

It even properly displays guidlines that are set up in the PSD file for publishing purposes, that are not a part of the graphic.  (I was very happy about this in fact)

---

### Post by stephanvaningen on 2008-10-26
Aha, sounds interesting, maybe something wrong with my GIMP installation? I get error message: "Error loading PSD file: Unsupported color mode: CMYK" when opening the .psd-file.

It shows a preview however.

The computer it is running on is Ubuntu 8.10 intrepid beta, updated to-date.
My installation comes from a dist-upgrade from 8.04

---

### Post by Zimmer on 2008-10-26
Support for cmyk in GIMP seems to be the problem..
[http://registry.gimp.org/node/2011](http://registry.gimp.org/node/2011)

There may be a plug in that could help from the post above.
also this one...maybe
[http://www.blackfiveservices.co.uk/separate.shtml](http://www.blackfiveservices.co.uk/separate.shtml)

I expect the psd files you can access are those saved in a non cmyk mode.
BTW, came across this...
[http://rants.scribus.net/2006/06/03/why-no-cmyk-in-gimp-is-a-good-thing-now/](http://rants.scribus.net/2006/06/03/why-no-cmyk-in-gimp-is-a-good-thing-now/)

---

### Post by stephanvaningen on 2008-10-26
> **Zimmer said:**
> Support for cmyk in GIMP seems to be the problem..
[http://registry.gimp.org/node/2011](http://registry.gimp.org/node/2011)

There may be a plug in that could help from the post above.
also this one...maybe
[http://www.blackfiveservices.co.uk/separate.shtml](http://www.blackfiveservices.co.uk/separate.shtml)

I expect the psd files you can access are those saved in a non cmyk mode.
Yeah, thanks but I already tried that plugin, no luck :-/

The link to the 'improved' I have not tried yet: ... pending,

---

### Post by VeeDubb on 2008-10-27
That's it for sure.  It's the CMYK issue.  The only other thing I could suggest would be the updated 2.6.1 version of gimp, which is supposed to include an updated PSD import filter.  However, it will probably still choke on CMYK until we get all the way to version 3.0 and GEGL is fully implemented. (I believe that's when we're supposed to get CMYK and high-bit depth support)

---

### Post by kayosiii on 2008-10-27
Gimp currently supports 8bit greyscale , 8bit pallete colour images, or 24bit RGB images currently. Other colour spaces seem to fail - though 48 and 64 bit images seem to be downsampled on import. Also features added past photoshop 6 aren't supported - I think....

Hope that helps. With Krita you could try going out of photoshop as a multilayer Tiff.

---

### Post by smartboyathome on 2008-10-27
> **kayosiii said:**
> Gimp currently supports 8bit greyscale , 8bit pallete colour images, or 24bit RGB images currently. Other colour spaces seem to fail - though 48 and 64 bit images seem to be downsampled on import. Also features added past photoshop 6 aren't supported - I think....

Hope that helps. With Krita you could try going out of photoshop as a multilayer Tiff.

Thats not true starting with GIMP 2.6. GIMP now has GEGL, which allows it to do CMYK as well as RGB.

---

### Post by VeeDubb on 2008-10-27
> **smartboyathome said:**
> Thats not true starting with GIMP 2.6. GIMP now has GEGL, which allows it to do CMYK as well as RGB.

sorrry.  no.

GEGL will 'eventually' allow CMYK and high bit depth images.  At the moment, GEGL does very little, and is only integrated into gimp on the most basic levels.  In fact, it's usage is still optional, and doesn't include anything that can't be done without it.  Some types of filters seem to work a little better with GEGL, but that's it.  

We probably won't see reliable CMYK or high bit depth until 3.0

---

### Post by roonie on 2009-12-23
Im trying to open a PSD file on GIMP 2.6.7 and it's still not opening since its a CMYK 8-bit file.

---

### Post by mikethedj4 on 2009-12-23
> **jerryroy said:**
> i want to know if there is a way to open a photoshop document in gimp

Open the .psd file in Gimp (Filters/Open) Now if the PhotoShop project/document has blending options it won't be shown if not, then you're good to go.

---

### Post by Stoneface on 2010-03-14
> **roonie said:**
> Im trying to open a PSD file on GIMP 2.6.7 and it's still not opening since its a CMYK 8-bit file.
I am having the same problem:
```
Opening '/home/me/Desktop/file.psd' failed:
Error loading PSD file: Unsupported color mode: CMYK
```

---

### Post by Tikkyca on 2010-03-14
You can do that by opening it like normal gimp file,but it doesn't support layer stiles.

---

### Post by codyddddd on 2010-03-14
Can anyone help me with gimp ? I need to take two photos and transparent include them to make one photo ! Please someone help me I would appreciate it a lot .
 
Thank's !
 
[EMAIL="loker992@yahoo.com"]loker992@yahoo.com[/EMAIL]
I can email you the photos I want to do this with.
 
Thank's a bunch.
 
-Cody

---

### Post by Zimmer on 2010-03-15
> **codyddddd said:**
> Can anyone help me with gimp ? I need to take two photos and transparent include them to make one photo ! Please someone help me I would appreciate it a lot .
 
Thank's !
 
[EMAIL="loker992@yahoo.com"]loker992@yahoo.com[/EMAIL]
I can email you the photos I want to do this with.
 
Thank's a bunch.
 
-Cody
Do not quite understand your 'transparent include' ....
Do you mean to layer the images with transparency.. do they have the same background, or are you superimposing part of an image onto another? 
Have a look here for a few pointers...
file://localhost/usr/share/gimp/2.0/help/en/gimp-image-combining.html
assuming you have the GIMP helpfiles loaded..

---

### Post by Stoneface on 2010-06-13
> **Tikkyca said:**
> You can do that by opening it like normal gimp file,but it doesn't support layer stiles.

With CYMK psds I still get:

```
Opening '/Users/me/Webdesign/file.psd' failed:

Error loading PSD file: Unsupported color mode: CMYK
```

I installed the plugin [separate]("http://cue.yellowmagic.info/softwares/separate-plus/index.html"), but that does not seem to help opening CYMK based psds..

---

### Post by Stoneface on 2010-06-13
Well, one thing I can do now is convert the CMYK based psd to pngs (no merge option chosen (-layers merge)) using ImageMagick and the following command:```
$ convert cmyk.psd -channel rgba -alpha on -colorspace rgb rgb-image.png
``` The first png is like the entire psd, but with merged layers and the others (all 50 of them) are layers represented by pngs. I will see if this can be finetuned, but so far so good ;-) .

---

### Post by kayosiii on 2010-06-15
you can then drag and drop the png images onto the layer dialog in the gimp which will import all the images as layers...
You will probably have to move them around to their right positions.

---

### Post by Stoneface on 2010-06-18
Thanks for the tip Kayosii! Will play around with ImageMagick and Gimp som more this weekend.

---

### Post by LepeKaname on 2012-02-13
Thanks Stoneface! It worked great!

---

