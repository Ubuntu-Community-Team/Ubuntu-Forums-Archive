---
title: "Can a children's book be illustrated and typeset on Ubuntu?"
date: 2012-02-27
forum: Art &amp; Design
---

### Post by LightSnack on 2012-02-27
Suppose someone had written a children's book, and was currently in the sketch stage of the illustration. The sketches soon will need to be scanned and colored in a program that can meet the printer's requirements for printing. 

The printer's requirements are that the artwork be in CMYK colors (as opposed to RGB) and converted to pdf format  ("printing press" option, instead of "web use" in Microsoft Word.)

A typical typesetting program is Microsoft Word, but I would like an alternative program to be used if possible. Is it possible to avoid Microsoft when illustrating/typsetting a children's book and still meet the printer's requirements? 

The PDF program will need to have a "single page" option instead of "spreads." I am not even sure what that means, I just know it is one of the requirements of the printer.

---

### Post by ageofsteam on 2012-02-27
I don't know about the others, but GIMP *can* be tweaked for CMYK support:
[CMYK plugin]("http://www.blackfiveservices.co.uk/separate.shtml")
[wiki page: CMYK support in The GIMP]("https://wiki.archlinux.org/index.php/CMYK_support_in_The_GIMP")

---

### Post by MG&amp;TL on 2012-02-27
Not sure if it supports CMYK, (I don't use it much), but *scribus* is a really good publishing application. It's in the repositories.

---

### Post by LightSnack on 2012-02-27
> scribus is a really good publishing application
Thank you. A quick search indicated that Scribus can save PDFs in single page format, which is one of the press requirements:

[http://wiki.scribus.net/wiki/images/8/88/Pdf_form_howto_new_doc.png](http://wiki.scribus.net/wiki/images/8/88/Pdf_form_howto_new_doc.png)

Another search shows a Pre-Press tab on the PDF export dialog:

[http://wiki.scribus.net/wiki/images/thumb/3/3c/Bleed2.png/700px-Bleed2.png](http://wiki.scribus.net/wiki/images/thumb/3/3c/Bleed2.png/700px-Bleed2.png)

That's a very good sign.

Thanks for the Gimp suggestion. I thought Gimp only used RGB colors.

---

### Post by LightSnack on 2012-03-01
Just found a tool that I believe could come in handy for someone who wants to illustrate a book or document for high quality printing:

Tiff 2 pdf. 

[http://manpages.ubuntu.com/manpages/gutsy/man1/tiff2pdf.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/tiff2pdf.1.html)

---

### Post by Ben_G_9C9 on 2012-03-05
I've been working for a local dance studio. 
For our flyers and program handouts, I used G.I.M.P. to manipulate images and LibreOffice Draw to set the final layout for the printer. 
Both programs are free and LibreOffice exports to *.pdf files painlessly.

---

### Post by Lightbeam7 on 2012-03-06
Both Scribus and Gimp are excellent opensource tools for this. Scribus has a CMYK setting. Gimp can do nearly anything photoshop can.

---

### Post by Dry Lips on 2012-03-06
A less known tool that I only recently heard of myself is SK1. [http://sk1project.org/](http://sk1project.org/) What's awesome about this program, is that you can import your Inkscape files into SK1, and it is able to give you press-ready PDF output.

But for book layout, Scribus is what you'd use.

---

