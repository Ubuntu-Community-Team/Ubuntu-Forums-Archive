---
title: "html2pdf"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by hannulan on 2007-08-08
I want to print alot of pages written in html to a pdf-document. Are there any good way to do this?

I'm looking for a program that takes the html-file as input and create a pdf-file who looks like the html-file would have look if I used Firefox.

---

### Post by FakeOutdoorsman on 2007-08-08
I've used this successfully:
[HOWTO: Install Cups-PDF ]("http://ubuntuforums.org/showthread.php?t=188860")
[HOW TO: Set up pdf printer]("http://ubuntuforums.org/showthread.php?t=140815")

You use it like you're printing a page, but it will create a PDF file.

---

### Post by hannulan on 2007-08-08
But as I understand it I have to use firefox. My which is to automate the printing with a bash script, using wget (or wget -O) to get the all the webpages and then create the pdf-documents and merge them together to one document which I than easily can print or save.

---

### Post by FakeOutdoorsman on 2007-08-08
I think I understand what you want to do now.  A better option might be to use the command-line programs html2ps and ps2pdf.  Then concatenate them with pdfjoin.

---

