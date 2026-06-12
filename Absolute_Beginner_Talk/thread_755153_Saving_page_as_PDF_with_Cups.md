---
title: "Saving page as PDF with Cups"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by r3bol on 2008-04-14
I'm trying to save my web pages as pdf documents with cups and using print to file as the print option. The resulting file seems to be a postscript document which is not readable by adobe's PDF, but is readable by evince PS viewer. 
I have searched a little and the forum help pages seem dont seem to be relevant any more. Does someone have any advice on what to do?

Thanks.

---

### Post by sillyxone on 2008-04-14
you need to install a virtual printer. It's the cups-pdf package in Synaptic.

once installed, just print to it (pretty much like cutepdf in Windows)

---

### Post by stchman on 2008-04-14
> **r3bol said:**
> I'm trying to save my web pages as pdf documents with cups and using print to file as the print option. The resulting file seems to be a postscript document which is not readable by adobe's PDF, but is readable by evince PS viewer. 
I have searched a little and the forum help pages seem dont seem to be relevant any more. Does someone have any advice on what to do?

Thanks.

[http://www.stchman.com/pdf_cups.html](http://www.stchman.com/pdf_cups.html)

Very handy tool to have.

---

### Post by r3bol on 2008-04-14
Thanks. I had cups installed already and setup. 
I realized that if I choose print, and check the 'print to file' checkbox, the outputted file (any PS printer selected) is unreadable with adobe pdf. BUT if I **don't** check 'print to file' the outputted file (any PS printer selected)** is readable** with adobe pdf.

Would that be a bug?

---

### Post by sillyxone on 2008-04-14
> **r3bol said:**
> Thanks. I had cups installed already and setup. 
I realized that if I choose print, and check the 'print to file' checkbox, the outputted file (any PS printer selected) is unreadable with adobe pdf. BUT if I **don't** check 'print to file' the outputted file (any PS printer selected)** is readable** with adobe pdf.

Would that be a bug?



no, PostScript is the native format that the printer can understand but not PDF. Adobe Acrobat Reader doesn't read PostScript file. 

Basically the cups-pdf read a PostScript data from application and convert it to PDF.

---

