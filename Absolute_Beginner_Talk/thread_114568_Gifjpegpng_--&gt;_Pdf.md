---
title: "Gif/jpeg/png --&gt; Pdf"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-01-08
Is there any package that will allow me to convert a .gif image (or similar) to a .pdf file in the same way I would convert a .tex file to a .pdf file?  I have tried to install 'gif2pdf' but apparently the package doesn't exist.  Thanks, I appreciate the help if anyone knows...

---

### Post by stuporglue on 2006-01-08
Here's a not-very-pretty way to do it...
Imagemagic will install a collection of graphics tools, including giftopnm and pnmtops (pnm is one of imagemagic's native formats). ps2pdf should already be installed so....

giftopnm foo.gif > foo.pnm
pnmtops foo.pnm > foo.ps
ps2pdf14 foo.ps foo.pdf

The Gimp may be able to do it with a GUI if you prefer. :-)

---

### Post by matthew on 2006-01-08
You could import the image into an OpenOffice document that fills the page ad then export as a pdf...again, not ideal, but it would work.

There must be a better way, though. Hopefully someone here will suggest it.

---

### Post by kakashi on 2006-01-08
is this gif2pdf a real program. if so give the link to it source code and i'll create a deb for you.

---

### Post by amcavoy on 2006-01-08
By convering to ps then to pdf, my original image lost quality and was distorted.  I can't really find anything on GIF2PDF for Linux, but there is something for Windows.  It may be that I just have to create these PDF files on my Windows OS.  Thanks for the help.

---

### Post by xmastree on 2006-01-08
You could use open office. Insert the graphic in a blank page, then save the document as a pdf.

---

### Post by kakashi on 2006-01-08
try wine

---

### Post by amcavoy on 2006-01-09
The program I would like to install (it seems to be alright) is located here:

[http://sourceforge.net/project/showfiles.php?group_id=96216&package_id=102740&release_id=333697](http://sourceforge.net/project/showfiles.php?group_id=96216&package_id=102740&release_id=333697)

I'm having trouble getting it installed with sourceforge's instructions.  Any ideas on how to do this?

Thank you.

---

### Post by neepster on 2006-01-09
This method works fairly well....

Example:
 a2ps --title='Chemistry Lecture Notes' -R
 --columns=1 --rows=1 *.png
 --output=test.ps
 
 ps2pdf test.ps test.pdf
 
 Requires ImageMagik and the Ghostscript library.

---

### Post by anaconda on 2007-09-25
Install the package imagemagick,
Open a terminal, go to the folder where all the pictures are and run:
```
convert *.jpg outfilename.pdf
```

Just had the same problem, and had to add the solutin here too. 
Some solutions take longer to find than others.. :D

---

### Post by stani on 2008-02-01
... or even more easy use Phatch (PHoto bATCH processor):
[http://photobatch.stani.be](http://photobatch.stani.be) > free download

It can convert any format to pdf and handles subfolders too. You could create a droplet with it and drag&drop all your folders or images which need to be converted.

Stani

---

