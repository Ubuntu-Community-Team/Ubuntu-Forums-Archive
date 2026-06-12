---
title: "Page layout: A7 pages on A4 paper (booklet printing)"
date: 2013-04-09
forum: Art &amp; Design
---

### Post by Keith_Beef on 2013-04-09
I couldn't find a better section for this than "Art and design", but page layout could be considered document design, so here's my problem.

I'm trying to print booklets with sixteen A7 pages on an A4 sheet of paper; I want to then fold the paper and staple or stitch it and then slit the outer folds.

Here are the steps I took.
I made the A7 page layout in Open Office, laid out the text and printed to a sixteen page A7 document.
For now, I'm just working on the first page of what will be the final A4 document to send to the printer.

I used pdftk to: 
[LIST]
[*]burst the document into sixteen individual PDF files named pg_00[01-16].pdf.
[*]rotate the following pages 90° clockwise: 1, 4, 13, 16.
[*]rotate the following pages 90° anticlockwise: 5, 8, 9, 12.
[/LIST]

Now I want to assemble these into a single A4 document again, but preserving the rotations I just gave to the A7 pages now in landscape orientation.

p9    p16
p8    p1
p5    p4
p12  p13

I tried concatenating them together (this gives me a sixteen page landscape A7 document), then pdfnup to make these pages fit on an A4 sheet.

The resulting file is an A4 document with all my eight A7 pages on it arranged in two columns of four, ready for printing, except for one big problem… whatever options I pass to pdfnup, the A7 pages are always rotated back to their original upright orientation! I have tried passing --turn false, tried printing in landscape, nothing seems to preserve the rotations 90° clockwise or anticlockwise that the pages had when they were one long sixteen pages of A7.

Am I missing something glaringly obvious?

---

### Post by oldfred on 2013-04-09
I have never done it but have these two old links.

Print alt pages to make booklets:
Postscript
[http://dsl.org/cookbook/cookbook_25.html](http://dsl.org/cookbook/cookbook_25.html)
Scribus
[http://ospublish.constantvzw.org/tools/how-to-print-a-booklet-in-16-steps](http://ospublish.constantvzw.org/tools/how-to-print-a-booklet-in-16-steps)

---

### Post by Keith_Beef on 2013-04-09
Thanks for the links.
> **oldfred said:**
> 
Print alt pages to make booklets:
Postscript
[http://dsl.org/cookbook/cookbook_25.html](http://dsl.org/cookbook/cookbook_25.html)

I'll need to study this some more. It might be that pdfnup lacks some of the flexibility of psnup… it's 02h00 here, and I ought to get a bit of sleep before attacking from a different angle.


> **oldfred said:**
> Scribus
[http://ospublish.constantvzw.org/tools/how-to-print-a-booklet-in-16-steps](http://ospublish.constantvzw.org/tools/how-to-print-a-booklet-in-16-steps)
That one is for A5 pages on folded A4 sheets, without the complication of pages rotated both clockwise and anticlockwise. Not all that useful for my problem.

---

### Post by Keith_Beef on 2013-04-10
Well thanks to oldfred's hint, I got quite a lot further on with this, and I've almost finished what I set out to accomplish.

However, I'm stumbling over the generation of an A4 page with eight A7 pages imposed on it: I keep getting an output US Letter page.

I've tried passing -pa4 and -pA4 as arguments to psnup, I've set /etc/papersize to a4 and to A4, and the output file is still US Letter.

Any clues?

---

### Post by Keith_Beef on 2013-04-14
Right, I figured this out. I wrote a script to do all the hard work and bundled it with an Open Office document for testing and demonstration purposes.

The new thread is [here]("http://ubuntuforums.org/showthread.php?t=2135458&p=12602855").

---

