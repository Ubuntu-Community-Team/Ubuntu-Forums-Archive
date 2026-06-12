---
title: "convert jpgs(scanned pages)to 1 pdf with txt as digitized characters,table of content"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-07-04
Hello,
We scanned a recipe book and the scanner saved each page as a jpg. I want to compile all the jpg-pages into one pdf file, with a Table of Contents in the start of the PDF. I would like the table of contents to have clickable links to the pages therein. I would like to know how to be able to specify the order of the jpegs when I get them into one pdf. 

I have tried ```
convert *.jpg foo.pdf
``` but it seems that the command put the pages into the filenames' alphabetical order. I don't like that order.

Also, is there a way to have my PDF using digitized characters for the text in the jpegs? I guess I'm asking for OCR capability. I think this would reduce the size of the pdf.

Thank you.

---

### Post by expatCM on 2007-07-04
You may want to take a look at gscan2pdf.  You should be able to import your scanned images and then convert to a pdf.
[http://gscan2pdf.sourceforge.net/](http://gscan2pdf.sourceforge.net/)

---

### Post by hanzj on 2007-07-04
The pages have been scanned already. All I have for now are the jpegs on my hard drive.

---

### Post by expatCM on 2007-07-04
I am not suggesting you do a fresh scans.  Use Import (File / Import) to bring your scanned images into the program and take it from there :)

---

### Post by hanzj on 2007-07-04
I see. Thanks. expatCM.

---

