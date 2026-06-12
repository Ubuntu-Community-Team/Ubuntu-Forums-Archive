---
title: "Inkscape / Scribus color management"
date: 2013-02-02
forum: Art &amp; Design
---

### Post by JayPeeJay on 2013-02-02
Using Inkscape 0.48.3.1 r9886 on Ubuntu 12.04

Color management seems to have been disabled after upgrade to Ubuntu 12.04.  

Under Inkscape preferences it says "Note Color Management has been disabled on this build".

Also, I had to reinstall all of my color profiles after upgrade.

Also,  in Scribus, the color managed view seems to work perfectly, everything  is as I expect it to be, and I can mark out of gamut colors.  However,  when I try to export to a certain colorspace, it doesn't work, I just  get the same RGB image (I test by re-placing image, it says Unknown  color space in the preview, then using the same profile I tried to  export to, I still see the out of gamut colors.).

"Color  management" in Gimp appears to work as I can use the separate plugin,  export a cmyk tif, then place that in Scribus (in preview it correctly  says cmyk colorspace, and there are no out of gamut colors).

What do I have to do to resolve this?  I noticed I have littlecms1 and littlecms2.  Is this is confilct?

***update***  I can confirm that color management definately works in Gimp and Scribus.  The "unknown color space" when I go to place an image in Scribus has to do with the fact that the color profile information doesn't get imbedded, and apparently that is when it judges by, but the colors are in fact changed.  It still is a little weird to me that I have colors out of gamut, but my guess is that because there is no color profile embedded in the pdf on export, on import something is happening to the color.  However, if I have the two images side by side in Scribus I can see they are definately different and the out of gamut colors are also different (there aren't as many in the new image).  Opening the images in an external viewer it is what I expect:  The original is a bright RGB file, and the Scribus Export looks a little more muted (because of the colors that can't be accomplished with CMYK).

Also, even weirder, Color Management in Inkscape DOES kind-of work.  I can see the color managed view and the colors get muted as I would expect, and if I open the fill and stroke dialogue I can turn on CMS for each object.  Turning it on, however, automatically fixes the color, where as before it would leave it the same and just give me an out of gamut warning and I could adjust the sliders myself to fix.  Now, if I try to adjust the sliders, it glitches and turns the CMS off immediately upon touching them.

---

