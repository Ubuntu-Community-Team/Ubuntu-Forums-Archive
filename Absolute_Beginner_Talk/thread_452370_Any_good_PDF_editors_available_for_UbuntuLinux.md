---
title: "Any good PDF editors available for Ubuntu/Linux??"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-05-23
Looking for free (possible open source) Linux pdf editor.  Does anyone have any suggestions??

---

### Post by vigleik on 2007-05-23
It depends what you're looking for. Almost any linux program can create pdf's, that's not a problem at all. If you're looking to edit pdf's made by someone else then....no, there aren't any good programs. The best I can think of is to use kword to import the pdf, make your changes, and then export (or print) as pdf again.

---

### Post by kevdog on 2007-05-23
As far as editing pdfs, I want to actually fill in the forms, and possible add images (png) to the documents.  I dont know if image addition could be performed since this would require "another layer" such as in photoshop.  If pdfs are imported into KWord, will the program allow me to edit them.

Ive already installed a cups pdf driver, so creation of pdfs is not a problem.

---

### Post by vigleik on 2007-05-23
As far as kword goes, after you've imported a pdf you are free to edit it, add images, do anything you want. The only problem is that the pdf import function is far from perfect, so if your pdf document is complex it's likely to screw up the formatting, sometimes badly. If anyone know of a better way I'd be interested too.

---

### Post by perce on 2007-05-23
You can try this one:

[https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit)

I haven't tried it yet, I'm going to install it now.

---

### Post by kevdog on 2007-05-23
Ive done extensive looking over the last 24 hours, and I can answer my own question -- THERE IS NO GOOD PDF EDITOR!  I tried PDFEdit, probably the best program I found, however its very limited, can only add text.

In order to add images, I simply have to split the PDF up into individual pages.  Import the page of interest into gimp, add the photo as a new layer, flatten the image, and then print the image as a pdf file, and then rejoin the whole file into one large pdf.  

I wish there were a simpler way, but there is not (at least from what I can find).  Substituting the default pdf printer for kprint in gimp was also a major revelation.

---

### Post by thesonisshining on 2007-06-10
what about scribus. i've only messed with it for a moment but it might work.

---

### Post by kevdog on 2007-06-10
Thanks for telling me about scribus -- I might use it for other things, however I dont think it will work for editing PDFs.  Ive never tried but I got this from just perusing the documentation on the site:

> Note: you can only import one page of a PDF at a time, and you cannot yet edit imported PDFs nor can you edit PDFs created with another application.

---

