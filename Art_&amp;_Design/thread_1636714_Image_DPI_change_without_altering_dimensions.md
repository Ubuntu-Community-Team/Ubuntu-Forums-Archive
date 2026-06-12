---
title: "Image DPI change without altering dimensions?"
date: 2010-12-03
forum: Art &amp; Design
---

### Post by Ranko Kohime on 2010-12-03
I've been scanning in an old book of mine, and somewhere along the way, I goofed.  I'm going Xsane -> Unpaper -> Convert, and the resulting .tif's are the correct size pixel wise, but instead of the 600dpi I scanned them at, they're now 72dpi.

This prevents me from running Clearscan OCR on them in Acrobat Pro, which is where I'm wanting to go with the images.

Xsane and Unpaper both are running 600dpi, so I have to assume the problem is in my Convert parameters, but I can't find any options for DPI in Convert's --help.

---

### Post by dpny on 2010-12-03
I don't know that software, but dpi and image dimensions are two factors in the same equation. For instance, a 2" x 2" image at 600 dpi is the same as a 4" x 4" image at 300 dpi: if you size the image down from 4" to 2" **without resampling**, you will increase the resolution from 300 dpi to 600 dpi.

So, see what size images you have, as some scanning software will interpret '600 dpi' as meaning 'make it as large as it has to be at 72 dpi to give an effective resolution of 600 dpi'. If the images are about 8x larger in dimension than they should be, you can resize, but not resample, with no problems.

---

### Post by Ranko Kohime on 2010-12-03
> **dpny said:**
> I don't know that software, but dpi and image dimensions are two factors in the same equation. For instance, a 2" x 2" image at 600 dpi is the same as a 4" x 4" image at 300 dpi: if you size the image down from 4" to 2" **without resampling**, you will increase the resolution from 300 dpi to 600 dpi.

So, see what size images you have, as some scanning software will interpret '600 dpi' as meaning 'make it as large as it has to be at 72 dpi to give an effective resolution of 600 dpi'. If the images are about 8x larger in dimension than they should be, you can resize, but not resample, with no problems.
Yeah, I kinda already know what I have to do to the images, the holdup is that I don't know how to automate the process.  With over 700 images to work with, it'd be rather silly to do each one manually.  :D

---

### Post by dpny on 2010-12-04
> **Ranko Kohime said:**
> Yeah, I kinda already know what I have to do to the images, the holdup is that I don't know how to automate the process.  With over 700 images to work with, it'd be rather silly to do each one manually.  :D

Sorry, man, can't help you: don't know the software.

---

### Post by mcduck on 2010-12-05
> **Ranko Kohime said:**
> I've been scanning in an old book of mine, and somewhere along the way, I goofed.  I'm going Xsane -> Unpaper -> Convert, and the resulting .tif's are the correct size pixel wise, but instead of the 600dpi I scanned them at, they're now 72dpi.

This prevents me from running Clearscan OCR on them in Acrobat Pro, which is where I'm wanting to go with the images.

Xsane and Unpaper both are running 600dpi, so I have to assume the problem is in my Convert parameters, but I can't find any options for DPI in Convert's --help.

The *-density* option is what you are looking for: [http://www.imagemagick.org/script/command-line-options.php#density]("http://www.imagemagick.org/script/command-line-options.php#density")

---

### Post by Ranko Kohime on 2010-12-18
> **mcduck said:**
> The *-density* option is what you are looking for: [http://www.imagemagick.org/script/command-line-options.php#density]("http://www.imagemagick.org/script/command-line-options.php#density")

Thanks for the tip, but it doesn't seem to work.  -density 600x600 has no effect, convert doesn't give any errors, but the .tif output files are still 72x72.  :cry:

---

### Post by mcduck on 2010-12-19
> **Ranko Kohime said:**
> Thanks for the tip, but it doesn't seem to work.  -density 600x600 has no effect, convert doesn't give any errors, but the .tif output files are still 72x72.  :cry:

What tool are you using to check the DP value of the output file?

There are actually at least a couple of different methods used to store DPI info in image files, and if the program you are using uses a different method than what Imagemagick does. (As an example, EXIF and XMP tags can have different DPI value stored at the same time. And Photoshop also uses it's own tag).

It might help if you remove any previous meadata from the image with the *-strip* option.

Of course you could also try using the *exiftool* or some similar program to write the DPI metadata to the file.

---

