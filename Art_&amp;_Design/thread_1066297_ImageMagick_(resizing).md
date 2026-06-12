---
title: "ImageMagick (resizing)"
date: 2009-02-10
forum: Art &amp; Design
---

### Post by Eric the Red on 2009-02-10
I'm trying to convert a .PDF to a .BMP 

So I tried,
```

convert "thedoc.pdf" "converted.bmp"

```
This does indeed converted the .PDF to the .BMP however, it seems like the resolution is like 50% of what the .PDF resolution was. This makes reading any text in my .BMP impossible. How do I keep the quality the same in the output as it was in the orginal PFD input?

---

### Post by smartboyathome on 2009-02-10
According to [this]("http://blog.robfelty.com/2008/03/11/convert-pdf-to-png-with-imagemagick/"), you need to run this command to get it how you want:
```
convert -density 600x600 -resize 800x560 -quality 90 "thedoc.pdf" "converted.bmp"
```
Why are you trying to convert it to BMP, though, instead of JPG or even PNG? BMP takes up a lot of space for a horrible quality image.

---

### Post by Flimm on 2009-02-13
Try using the GIMP.

---

