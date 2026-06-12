---
title: "SVG --&gt; Corel"
date: 2007-11-12
forum: Art &amp; Design
---

### Post by galv on 2007-11-12
HI,
Have some drawings that I made in Inkscpe, and saved in SVG format, now I need to pass it to Corel Format so I can do some (large) printing. Is there anyway to do it?

Need help!

Thanks :)

---

### Post by leonidas666 on 2007-11-12
The Corel Draw native Format is evil, proprietary and closed. You will most probably not find a proper svg to cdr converter. So if you want to open your svg in corel draw (is corel draw really not able to open .svg? maybe there is some kind of plugin?), you have to convert your svg to some other format , maybe wmf, or dxf, or hpgl. Maybe imagemagick can do the conversion.
Otherwise, if you just need to print your .svg, maybe there is a more direct way to do it than by using corel draw. If you write something about the setup of your printer, maybe we'll find a better way to print it than using corel draw.

---

### Post by galv on 2007-11-12
It's not my printer,  i'm printing in a store,
I'll be printing 2meters by 1,60 meters, so I have to send a png/jpg with the right size (huge amount of MBs) or I could send a Corel file so that any last minute change (in fonts, or something) can be made in the store. The guy only has Corel, so I'm kinda stuck!

I'Ve tried imagemagick but no luck

---

### Post by maruchan on 2007-11-12
Corel can import SVG, but of course it probably won't correctly render blurs and things like that. PNG isn't a bad idea...a person who runs a print shop should be more than able to import a PNG of that size at the correct resolution.

---

### Post by leonidas666 on 2007-11-12
> **galv said:**
> It's not my printer,  i'm printing in a store,


If you knew the type of the printer, then you could find out what kind of language it understands. E.g. if it understands Postscript, you could create a postscript file, and then you don't need any program to print it, just pipe it to the parallel port. Similarly with e.g. a hpgl plotter. Of course this depends on how flexible this guy in the store is.
Ideally he could just install inkscape... :)

---

### Post by kayosiii on 2007-11-13
Corel can import SVG & has been able to since version 9 (where you had to download it as an add on.

I can't tell you how well it will support all features - you would have to try it first.

As a backup & I always do this - render out a bitmap of your work - you will need to ask the printer what dpi (dots per inch) the printer is designed for - typically 300 on a home printer smaller on large format printers - find out any area that must be left blank - margins, bleed etc & factor this in. Create a bitmap at the DPI, width and height of your final image. Open the file in the GIMP check that the DPI is correctly set. flaten the image and convert to tiff (not strictly necessary but most printers are more familiar with this format). 

You should take this file to the printer along with the SVG & all the fonts you used (SVG doesn't embed fonts) or you could try importing the SVG into scribus and producing a PDF from there.

---

### Post by galv on 2007-12-02
I end up importing the SVG with Gimp and then generate a very large PNG that I sent to the guy.

---

### Post by smartboyathome on 2007-12-02
You can export it as an SVG using Inkscape (File > Export Bitmap). I find it a little better quality than GIMP.

---

### Post by galv on 2007-12-02
I know, I because part of my drawing was bigger than the page Inkscape didn't export any of that part. I'm more familiar with Gimp than Inkscape so some retouch were allot easier to do in Gimp.

By the way, how to do a crop (a real crop) in Inkscape?

---

### Post by smartboyathome on 2007-12-02
Use the button in the top right hand corner to change the page size.

---

