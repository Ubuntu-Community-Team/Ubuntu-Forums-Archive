---
title: "How can I add text with some subscript/superscript to a picture?"
date: 2011-05-24
forum: Art &amp; Design
---

### Post by KIAaze on 2011-05-24
Hi,

How can I add text with some subscript/superscript to a picture?

I tried with Gimp and Inkscape. Gimp doesn't seem to allow it at all and in Inkscape I could only change part of the text to bold or italic. I couldn't find any subscript/superscript functions.
I can of course create the text elsewhere, convert it to a picture and insert it, buit I'd like to know if Gimp, Inkscape or any other image editor allow to do it directly. :)

I'm using Ubuntu 10.04 at the moment, so maybe later versions have such functions. If this is the case, please let me know.

---

### Post by earlycj5 on 2011-05-24
> **KIAaze said:**
> Hi,

How can I add text with some subscript/superscript to a picture?


Inkscape would be my recommendation.Just click the superscript or subscript (xy) button in the text menu bar.

---

### Post by KIAaze on 2011-05-25
Thanks. I installed the latest inkscape version from source (Inkscape 0.48.1 r9760 (May 25 2011) and it indeed does have subscript/superscript. :)
(Inkscape 0.47 r22583 (Apr  4 2010) which comes with Ubuntu 10.04 doesn't)

However, in the meanwhile I used openoffice presentation, which also works quite well. I just have to export as PDF and then convert the PDF to an image afterwards. But adding text with subscript/superscript is easy in it.

---

### Post by ApOgEEs on 2011-05-25
I think it should be easier in **Inkscape**. After you have added your text over the image, select the image and press **Shift+Ctrl+E** to open an **Export Bitmap** dialog.

Set the Width or Height of your resulting image, set the filename and click on **Export**

[IMG]https://lh5.googleusercontent.com/_QmenDvyMjlk/Td0UDMJ_0PI/AAAAAAAACVA/JumfbQwTdXE/s640/export-bitmap.png[/IMG]

Therefore, you don't have to convert to PDF and convert it back to image.

---

### Post by rajan on 2013-02-13
<dig> I discovered a native, but somewhat subpar way to make superscripts in Gimp, and I figured I should share it before I forget. If you're interested in getting special characters in Gimp, use the control-shift-u key combination that you usually use for inserting things like Greek letters, or math symbols, but instead use the unicode code for a superscripted number/letter. 

Basically, instead of [control-shift-u] + 03b2 for a Greek "beta" letter, use [control-shift-u] + 2093 for a subscripted "x"

The problem with these unicode sub/superscripted letters/numbers is that they still are required to fit on the same line, so they don't look as good. It's faster than creating your own sub/superscripts by creating layers of text and aligning them by hand. 

Here's the unicode directory:

[http://www.unicodemap.org/](http://www.unicodemap.org/)

For OP's question, it seems like Inkscape works best, but hope this helps someone save some time while using Gimp.
</dig>

---

