---
title: "Need something that can import XML artwork file"
date: 2008-01-21
forum: Art &amp; Design
---

### Post by John Jason Jordan on 2008-01-21
I have a Java application (TreeForm) that creates vector artwork with lines and text. I need to place the artwork into OpenOffice.org for academic papers. Its native format is XML. I can open the XML files in OOo, but all I get is a page of XML code. I am trying to find a graphics program that can open the XML files and resave in some vector format that OOo can use (AI, EPS, etc.). 

Any suggestions?

---

### Post by smartboyathome on 2008-01-21
maybe try Inkscape?

---

### Post by John Jason Jordan on 2008-01-21
> **smartboyathome said:**
> maybe try Inkscape?
Inkscape cannot import or open XML. At least it does not see .xml files as image files.

Still looking.

---

### Post by smartboyathome on 2008-01-21
Rename it to .svg. That is an XML file which makes an image (I think what your program exported and SVG is the same thing, though I may be wrong).

---

### Post by John Jason Jordan on 2008-01-21
> **smartboyathome said:**
> Rename it to .svg. That is an XML file which makes an image (I think what your program exported and SVG is the same thing, though I may be wrong).
Thanks, but still didn't work. The program (TreeForm) doesn't export as XML; XML is its native format. It can export to JPG or PNG, but only as bitmaps. I am trying to figure out how to get vector images out of it. My only options to work with are its native XML, or its exported PNG or JPG bitmaps. The bitmaps really suck because the images are nothing but lines and text, all of which come out fuzzy.

I tried to print to PDF using CUPS PDF printer, but the print function in TreeForm is broken on Gutsy x86_64. TreeForm is written in Java and there must be some problem getting it to see CUPS.

There  must be some way to get vector image files out of TreeForm.

---

### Post by smartboyathome on 2008-01-21
Looks like you are stuck with exporting it as a PNG :(

---

