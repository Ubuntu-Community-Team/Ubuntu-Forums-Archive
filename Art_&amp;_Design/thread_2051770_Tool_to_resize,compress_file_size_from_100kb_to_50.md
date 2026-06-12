---
title: "Tool to resize,compress file size from 100kb to 50 kb."
date: 2012-09-02
forum: Art &amp; Design
---

### Post by clausrei on 2012-09-02
Hi,

I would like to resize a series of files (jpg images) to half of its size in terms of quality and file size - not in terms of scale.

On a Google search I have found this ImageMagick tool, but this seems to resize the pictures only in terms of scale.

I need to resize them, because I would like to save them as PDF file using the gscan2pdf package.  But when I feed this tool with the 114 jpg picutres,  ( file size of 100kb each) I get a PDF of about 160 MB, which is far to much.

What can I do ? Any suggestion might be useful. Thank you for your help !


Claus

---

### Post by Pinoy Tux on 2012-09-02
What tool did you use?  ImageMagick's convert tool can resample as well as change the compression quality of images.  I was able to tone down a 300dpi 2.8MB A4-sized scanned document to 54.2KB using 50% quality @ 96dpi, without changing the physical dimensions.

```
convert input-file.jpg -quality 50% -resample 96x96 output-file.jpg
```You can, of course, change the dimensions of the picture as well using the same tool.

```
man convert
```for more information.  Or do a search on the web.  There are tons of detailed explanations on how to use this tool.

---

