---
title: "Converting a pdf file to an image file"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-09-09
Hi,
I have created a one page spreadsheet and I would like to insert this chart in to my google document.
I can convert the spread sheet to a pdf file but I can not insert a pdf to my google document so I need to convert it to jpg. does anybody know how to convert a pdf file into jpeg or gif file?
I hate GIMP so please dont recommend me GIMP in anyway.

Thanks...

---

### Post by parvinder on 2007-09-09
The easiest way will be to print screen and then paste it into any pic editor and extract the chart by selection/cut tool and paste it in your presentation.:guitar:

---

### Post by schorsch on 2007-09-09
There is a binary called "pdfimages" which should do the trick. It is in the package "poppler-utils".

---

### Post by vanadium on 2007-09-09
pdftoppm converts PDF to portable pixmap (which can than be converted to jpg or another format of your choice). pdfimages does something else: it extracts graphics embedded in PDFs.

---

### Post by schorsch on 2007-09-09
.... once again I learned something new .... thanks@vanadium

---

### Post by ubuntu.daemon on 2007-12-27
sweet.  just in time to help me redig some artifacts of mine!
:popcorn:

---

### Post by Tristan_F on 2007-12-27
You can also use imagemagick if you have it installed using

convert my_file.pdf my_file.jpg or whatever extension you need. It can be really awesome if your pdf file has multiple pages because you will have a JPG file for each page of the PDF file

---

