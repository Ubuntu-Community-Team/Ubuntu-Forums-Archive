---
title: "Imposition of A7 pages into A4 paper"
date: 2013-04-14
forum: Art &amp; Design
---

### Post by Keith_Beef on 2013-04-14
I've been wanting for a while to understand how to print a small format booklet onto bigger paper, to fold and slit to make a booklet, and a post in another forum where I am active stirred me to do something about it.

The technique is called imposition; there are Wikipedia articles about this in a few languages, the easiest way to find them is from the [English version]("http://en.wikipedia.org/wiki/Imposition").

So I started by creating an Open Office document with an A7 page format, filled it up with sixteen pages of lorem ipsum dolor text, exported this to a PDF file and then set to work making a script to handle the imposition onto two sides of A4 paper.

The files in the attached tgz archive are:
[LIST]
[*]the example Open Office file, 
[*]the BASH script to do the work.
[/LIST]
 

I tried to put enough comments into it to make it clear how it works.

It requires commands from the following packages:
[LIST]pdftk,
[*]poppler-utils,
[*]texlive-latex-recommended,
[*]psutils.[/LIST]

To use the script, make a directory containing ONLY the PDF file that you want to impose onto A4 paper, place yourself in this directory and then launch the script.

The document must be 16 pages long; the script does not check that there is only one PDF file, nor does it check that the file contains exactly sixteen pages.

Feel free to post comments about the script and to improve it.

---

### Post by lowo on 2014-03-12
Thanks for the script!

anyway, there's an error in it. maybe the update caused it.

change the word "1E" to "1east", "1L" to "1left", etc. you'll be find :D

thanks again for the script

---

