---
title: "printing with Digikam, dark prints or blown highlights"
date: 2009-12-16
forum: Art &amp; Design
---

### Post by dspisak on 2009-12-16
Hello.  I would appreciate some help with a problem I have.

I'm using ubuntu linux as the OS and I want to print to my HP printer. I use Digikam 1.0.0 for processing. If I use the recommended hpijs driver the prints are very dark and muddy. Adjusting brightness or gamma has no effect. Has anyone had a similar problem? Is there a solution?

If I use the CUPS+Gutenberg driver I can get a print very close to what is shown on the monitor (Samsung 2343bwx). However, highlights on a yellow object, say a lemon or a pepper, look blown-out with a green tint to the edges (!). I've tried decreasing brightness or gamma with minimal effect. Does anyone have any solutions?

Thank you for your help.

Dan

---

### Post by AlphaLexman on 2009-12-18
I would recommend NOT printing with Digikam if you want high quality results.

Hopefully you are shooting in RAW format. You will have much better post processing control if you are.

Do all your white balance and exposure settings, etc. with digikam [or UFRaw, a plugin for Gimp] and print with the Gimp. You can convert RGB to CMYK in Gimp by Clicking --> Image, Seperate, Seperate.

I would also check your ICC color profiles for your camera, screen and printer. Some programs will read the internal ICC profile and adjust the image to look correctly on your screen. Printing to a specific printer through a particular driver MAY read the original ICC profile embedded in the file and counteract your adjustments in the software.

Because there are so many cameras, monitors and printers, not one software can adjust for all of them. Digg into your camera, monitor, and printer manuals to check the ICC profile handles.

Hope this helps!

---

