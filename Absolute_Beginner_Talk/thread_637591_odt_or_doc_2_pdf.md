---
title: "odt or doc 2 pdf"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by diamantis13 on 2007-12-11
Hi!,

I have a few .doc files that I wrote in Open Office and I would like to combine them to a pdf. When I tried to export to pdf, the new pdf file has some minor, but important, problems in the way fonts are looking. I tried to print it to a file (as a .ps) but I constantly get a printing error. I even tried to use a online .doc2pdf utility  (PDFonline), but it changed the layout of the text (as if it was printed in a larger or smaller paper).
I finally sent the files as they were, but I suppose I, or someone else,  will run again in such a problem, so if there are any ideas please give some help.

Thank you very much, 
Diamantis

P.S. I am using Ubuntu 7.04, the documents where written in Open Office 2.2.0

---

### Post by Xbehave on 2007-12-11
Im not sure how to do this in gnome but under KDE there is a pseudo printer that prints to a pdf file.

you could also conver the ps to pdf ps2pdf

---

### Post by JillSwift on 2007-12-11
Same for Gnome as KDE, there is (by default, anyway) a PDF pseudo-printer installed. (A pretty good one, too.)

---

### Post by diamantis13 on 2007-12-11
How do I access this pseudo-printer? When I select File->Print from OO I see only my physical printer, and at System->Administration->printing I see no other option.

---

### Post by JillSwift on 2007-12-12
You should be able to make a new PDF printer.
[INDENT]System --> Admin --> Printing
New Printer
"Print Into PDF file", URI: cups-pdf:/, forward
"Generic", forward
"PDF File Generator", forward
Choose names for your new PDF printer, Apply
[/INDENT]When you print to the pseudo-printer, it will place the PDF file in ~/PDF/

Hope this helps =^_^=

---

