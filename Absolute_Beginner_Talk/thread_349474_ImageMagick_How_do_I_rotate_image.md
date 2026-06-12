---
title: "ImageMagick: How do I rotate image?"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by newbie22 on 2007-01-30
How do I rotate image?  Say 90 degrees.

---

### Post by NewOldTimer on 2007-01-30
New here but heres how I do it....open image viewer>image>rotate>file>save

---

### Post by newbie22 on 2007-01-30
Thanks for responding, but I am planning to use it for a script, so it has to be CLI-able.

---

### Post by Roger Mudd on 2007-01-30
Information below is pulled from [here]("http://www.imagemagick.org/script/command-line-options.php#rotate"):

> -rotate degrees{<}{>}

apply Path image rotation to the image.

Use > to rotate the image only if its width exceeds the height. < rotates the image only if its width is less than the height. For example, if you specify -rotate "-90>" and the image size is 480x640, the image is not rotated. However, if the image is 640x480, it is rotated by -90 degrees. If you use > or <, enclose it in quotation marks to prevent it from being misinterpreted as a file redirection.

Empty triangles left over from rotating the image are filled with the color defined as background. The color is specified using the format described under the -fill option.

---

### Post by NewOldTimer on 2007-01-30
sorry speed reading with a slow mind today. this help any?  [http://www.cb.uu.se/~magnusg/index.php?pidimagemagick](http://www.cb.uu.se/~magnusg/index.php?pidimagemagick)

---

### Post by newbie22 on 2007-01-30
Thanks for the help!

Silly me...  I went to this page prior to asking:

[http://www.imagemagick.org/script/command-line-tools.php](http://www.imagemagick.org/script/command-line-tools.php)

I "Ctrl+F: rotate" and found nothing.  Only after the above did I realize rotate is an option under convert.

---

