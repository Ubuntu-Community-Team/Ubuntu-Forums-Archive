---
title: "HDR Imaging"
date: 2007-08-22
forum: Art &amp; Design
---

### Post by mzracer360 on 2007-08-22
I am looking for an open-source/free HDR Imaging software.  Are there any available?

thanks,

mzracer360

---

### Post by ChaKy on 2007-08-22
You can try Qtpfsgui, it has HDR and Tone mapping. You can download it from here [http://www.getdeb.net/app.php?name=Qtpfsgui](http://www.getdeb.net/app.php?name=Qtpfsgui)

---

### Post by Golyadkin on 2007-08-22
It is not free, but very cheap, and the closest you can get to a replacement for Photoshop in Linux if you don't grok the Gimp: [http://www.kanzelsberger.com/pixel/?page_id=12](http://www.kanzelsberger.com/pixel/?page_id=12)    The Pixel Image Editor

---

### Post by mzracer360 on 2007-08-22
Are there any tutorials for creating HDR images in Gimp?  I haven't really messed with Gimp much, but would love to figure it out!  I just found out about HDRI and am loving the looks of them!!!

---

### Post by henriquemaia on 2007-08-22
> **mzracer360 said:**
> Are there any tutorials for creating HDR images in Gimp?  I haven't really messed with Gimp much, but would love to figure it out!  I just found out about HDRI and am loving the looks of them!!!

I’m also interested in that, specially to try the new 2.4 rc1 version.

---

### Post by Sindwiller on 2007-08-24
> **henriquemaia said:**
> I&#8217;m also interested in that, specially to try the new 2.4 rc1 version.

GIMP doesn't support HDRI images... but you could try [Krita]("http://www.koffice.org/krita/"), I think.

---

### Post by guine on 2007-08-26
Ive been able to create hdr images using Qtpfsgui easily, the problem is I havent been able to change the file type to something else that most programs can recognize.(Ive tried gimp cinepaint and krita but none of them could open up the image to save it as something else)
Gimp also has a dynamic range extender that although not true hdr since it lacks tone mapping, does combine an underexposed and overexposed image into one picture.  This is one picture I used gimps dynamic range extender to create:
[IMG]http://farm2.static.flickr.com/1080/532617045_4aba8a6b44.jpg[/IMG][flickr]("http://www.flickr.com/photo_zoom.gne?id=532617045&size=m")
If anyone knows how I can change save the version of this shot that I made using Qtpfsgui in a normal file type Ill post it here so that you can see the difference between gimps dynamic range extender and a true hdr image that used tone mapping.

---

### Post by Qinjuehang on 2007-10-20
You could try searching sourceforge. I like qtpfsgui too, but it lacks some features.

---

### Post by Qinjuehang on 2007-10-23
I found Cinepaint, it is eally good :D

---

### Post by Rey Merin on 2007-10-23
HDR Imaging is quite fun. I've tried it out on Photomatix which works well, but I think that costs some money.

Other than that, I don't really know programs that do it. Just wanted to show my appreciation for it :D

---

### Post by Darxus on 2009-08-28
GIMP can't handle HDR because it can only do 8 bits per color per pixel, which means only 255 brightness levels.  (Yes, technically, those 255 levels *could* span a high dynamic range, specified with an ICC color profile, but it's never done, because the precision between levels would be useless.)

This is why cinepaint exists.  32 bits per color per pixel, 4.3 billion brightness levels.  You know how when you change levels a couple times in GIMP and it ends up looking terrible because it loses precision each time?  cinepaint doesn't have that problem.

You can save an hdr image from qtpfsgui (I've tested .exr files) and open and edit them in cinepaint.


"not true hdr since it lacks tone mapping"

Wow, that is so wrong.  Tone mapping is only the surreal way of converting HDR to LDR.  Tone mapping is not HDR.  HDR is High Dynamic Range.  

The reason you can't save HDR images to normal file types (like jpeg) is that those normal file types don't have anywhere near the number of bits per pixel required.  You first need to convert the image to LDR.  To do this without the surreal effect of tone mapping, just reduce the contrast.


[http://en.wikipedia.org/wiki/High_dynamic_range_imaging](http://en.wikipedia.org/wiki/High_dynamic_range_imaging)

---

