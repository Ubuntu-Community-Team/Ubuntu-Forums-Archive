---
title: "Most high quality and lossless image filetype with GIMP?"
date: 2009-05-07
forum: Art &amp; Design
---

### Post by Fzang on 2009-05-07
Yeah, I know I post a lot but sometimes I just keep having questions..

You may call me picky if you like :p

I feel like I can spot individual pixels right on and it really annoys me because I keep feeling my artwork is looking low-quality.

What's the most lossless and quality preserving options? I would imagine png is the most lossless, but GIMP also gives me a lot of other options which I don't really know wether to select or not to preserve quality.

So, what is the best quality for GIMP?

---

### Post by mongoosled on 2009-05-07
from what i can tell from a quick search on google, TIF, PNG, and BMP are all lossless, so any of those would be the best quality because it doesn't really compress them like, say, a jpg.

---

### Post by Bölvaður on 2009-05-07
go with PNG. it had transparency and gives you small files from vector images (think inkscape)

---

### Post by Fzang on 2009-05-07
Which options in png do I check/uncheck? I have no idea what saving layer offsets or gamma do

---

### Post by Neon Lights on 2009-05-07
[http://docs.gimp.org/en/gimp-images-out.html#gimp-using-fileformats-export-dialog](http://docs.gimp.org/en/gimp-images-out.html#gimp-using-fileformats-export-dialog)
Scroll down to "1.2.3. Saving as PNG" ;) Heheh. I'd say your best bet is PNG. TIFF works too, but I don't know what all websites would support uploading it.

---

### Post by lukeiamyourfather on 2009-05-07
Assuming the image is perfect quality to begin with the image can only be displayed as sharp as the dot pitch on the monitor (physical dimension of each pixel on the monitor). Formats that are lossless will have the highest quality but that's only if the images used to make it were not compressed to begin with, crap in, crap out. Over sharpening and scaling up images can also reduce quality dramatically.

Something else to consider in image formats (not related to sharpness) is bit depth and the capability for layers. BMP is loss but supports only 8-bits per channel color where as PNG supports up to 16-bits per channel color. Some image formats like EXR support up 32-bits per channel color (floating point color). Generally speaking images that are 8-bits per channel without layers and slight lossy compression are standard for viewing on the web. Cheers!

---

### Post by CharmyBee on 2009-05-07
BMP is also uncompressed, and does not support 32-bit color (only 24-bit, no alpha channel). No one uses BMP on the internet but newbies. I only use BMP for older OS without support for any other format for backgrounds (Win9x)

---

### Post by kayosiii on 2009-05-08
Gimp only supports up to 8bit per channel images.

So pretty much anything that can gif or jpg will be lossless as long as it isn't a paletted image.

PNG,TIFF or TGA would be my first port of call - depending on what you are using the image for.

The options in PNG are really mostly about information stored inside the png file that might be useful to a program trying to open it. They don't really affect the quality of the data in any way.

---

### Post by paullinux on 2009-05-09
Always use '.xcf' extension as long as you are working on the picture, this preserves the original elements when using layers.  Only when finally ready then save as either PNG (if transparency is required) of JPG (be aware: Gimp will use the highest compression as standard!!  The less compression the better the image).  But it is always a trade off: more compression = less loading time on webpages...

As been said above already: everything starts with the quality of the original image...

---

### Post by hessiess on 2009-05-10
^ Neaver use Jpg unless it is absolutly nesoserry, eavent the highet quality mode is lossy and introduces artifacts, eapetily around airias of sharp colour changes(line drawings). In this case a palleted format like PNG is much better, or using vector graphics insted. Jpg was only designed to compress photographic data, which id does very well, for vertually everything else it can produce awful results.

---

### Post by Fzang on 2009-05-10
Thanks for all the replies. I'll try to do some high quality work now :)

---

### Post by MikeCyber on 2013-04-09
How is it going? I remember a good while ago that manipulating png images resulted in a lower quality image than doing the same in Photoshop 7.

---

### Post by overdrank on 2013-04-09
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

