---
title: "printing .eps via .pdf"
date: 2011-06-08
forum: Art &amp; Design
---

### Post by maclenin on 2011-06-08
Hello!

Essentially, my goal (in Lucid) is to add a logo to a .pdf document, which I can then print via Adobe Reader 9.

Here's a current work-flow sample:

1. Receive start.pdf (document without logo) from 3rd party.
2. Open start.pdf in Inkscape.
3. Save start.pdf as start.svg.
4. Receive logo.eps (logo) from 3rd party.
5. Open logo.eps in Gimp.
6. Save logo.eps as image type (i.e. png) that Inkscape can handle.
7. Open start.pdf in Inkscape.
8. Open logo.png in Inkscape.
9. Copy logo.png into start.svg.
10. Save start.svg (document now with logo) as end.pdf via Inkscape.
11. Open end.pdf in Adobe Reader 9 - all looks well!
12. **However**, in the end, end.pdf will not print via Adobe Reader 9 - having tried with (at least) these image types: logo.png, logo.jpg, logo.gif....

Thanks for any suggestions!

---

### Post by maclenin on 2011-06-08
Well, I think I've **solved** the riddle....

Insert the following into the **op** work-flow sample, for pure joy:

10**a**. Navigate to the directory where end.pdf resides.
10**b**. Open the terminal there and type: ```
**pdf2ps** end.pdf
```
10**c**. Keep the terminal open and type: ```
**ps2pdf** end.ps
```
10**d**. Open the (10**sub**.) resultant end.pdf in Adobe Acrobat 9 and print thy file!

I hope this helps someone as soundly as it seems (thus far) to have helped me!

---

### Post by maclenin on 2011-06-09
Any suggestions, generally, about how to best edit .pdfs? My results - though the inserted logo looks great - are sketchy, at best, with regard to the legibility / clarity of other elements (images / text / cad drawings) within "start.pdf" after conversion to (and printing of) "end.pdf"....

Thanks, in advance, for any kernels!

---

### Post by Dry Lips on 2011-06-13
> **maclenin said:**
> Any suggestions, generally, about how to best edit .pdfs? My results - though the inserted logo looks great - are sketchy, at best, with regard to the legibility / clarity of other elements (images / text / cad drawings) within "start.pdf" after conversion to (and printing of) "end.pdf"....

Thanks, in advance, for any kernels!
You mean editing existing PDFs?

In that case, there's a program called PDF editor that you could have a look at:
```
sudo apt-get install pdfedit
```

Otherwise, I'd say Scribus is the best editor for creating PDFs from scratch.

---

