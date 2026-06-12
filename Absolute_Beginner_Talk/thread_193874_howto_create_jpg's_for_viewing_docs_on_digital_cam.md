---
title: "howto create jpg's for viewing docs on digital camera??"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by stairwayoflight on 2006-06-10
hi all,

ubuntu rocks! i love automatix. thanks to everyone for all the hard work.

just wondering.. i seem to remember reading about converting docs to jpegs for viewing on a digital camera.

mine has a screen resolution of 640x240, (basically 4:3 aspect ratio on the lcd). i would like to convert documents of arbitrary type (probably pdf's or something easy to create) into either a bunch of jpegs, one per page, 640 px's wide, or simply one very tall jpg 640 wide.

i can do it in the gimp on a per page basis, but i would have to save the doc one page at a time, because gimp will only import the first page of a pdf as far as i can tell.

i am guessing i need to use scripts or cups or something but i'm not sure. i would have put this in programming, but i'm not sure this thread belongs there.

anyone have any ideas??

(i probably don't have to say it, but the faster the better!) :)

---

### Post by nalmeth on 2006-06-10
I don't know, can kpdf / evince / adobe-acrobat do this?

---

### Post by uno on 2006-06-10
pdftk contains a utility to split a pdf into single pages. Then run gimp on each page.

---

### Post by uno on 2006-06-10
I tried this out and it worked. About 1 page per second throughput on a 1.4GHz machine.

$ pdftk Prius_User-Guide.pdf burst output Prius_User-Guide_p%02d.pdf

$ mogrify -format jpg -geometry 640  Prius_User-Guide_p*.pdf

mogrify is from the imagemagick suite and does batch conversions. In theory imagemagick could directly convert the pdf into a bunch of jpg files, but that wasn't working when I tried it.

---

