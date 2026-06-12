---
title: "[SOLVED] OO.org Impress -- imported image quality?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by srhlefty on 2007-10-22
When I import a bitmap image into Impress, it looks different than its thumbnail and the way it looks in the GIMP.

This is really bugging me, because this behavior is not observed in the Windows version of OpenOffice.

The lower-quality image shows up during the slideshow as well.  Yet, if I export the show to PDF, the image shows up normally.

It sort of looks like Impress is converting the image to indexed color.

Have any of you seen this effect?  Am I missing some setting somewhere?  It is very easy to test on your own computer.  Just make a smooth gradient in the GIMP of any set of colors, and then import the image into Impress.


Here is a screenshot showing the effect:
(and don't give me grief for using PCLOS, my main home comp is Gusty, this is just my laptop :))
[IMG]https://webfiles.uci.edu/hunts/public/ooo.png[/IMG]

---

### Post by por100pre1 on 2007-10-23
I reproduced the issue you are facing. I used a gif image with the result you posted. I used a png image with no problems at all. Try using png images and let me know if this works. :)

---

### Post by srhlefty on 2007-10-23
Interestingly enough, I think it may have been distro related.  I tried the same experiement on Feisty, Gusty, and open SUSE 10.3, all of which successfully displayed the image.  In a fit of frustration, I replaced PCLOS on my laptop with Gusty, so I'm going to put the matter to rest.

Thank you for trying it as well, the PNG suggestion is a good one--I heard from someone at the OOorg forums that Impress stores images internally as png's, so importing a png is less likely to result in distortion.

---

### Post by por100pre1 on 2007-10-23
Yes, if png is actually the format used internally by OOo, is a good idea to import png files. GIF files are indexed images, at least to my knowledge. Glad to help! :)

---

