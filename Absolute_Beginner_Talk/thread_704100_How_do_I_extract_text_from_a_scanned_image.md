---
title: "How do I extract text from a scanned image?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by slymi2005 on 2008-02-22
I am trying to scan a typed document onto the computer, I just want the text, and I've been using Xsane but it won't let me save as text. I tried making it into a pdf and then copying the text but i can't select the text it just copys it as an image. Is there a program that I could use to make the process easier?

---

### Post by spiderbatdad on 2008-02-22
Obviously you can make a pdf out of the image, but the pdf is encoded. To turn that into text would require a program to decode the pdf. There are programs for this...their successful use might be questionable...pdftk is in synaptic...never tried it though. I don't think this is supposed to be easy...can't have people just going around editing pdfs.

---

### Post by slymi2005 on 2008-02-22
Well thanks for the optimism, I tried something called libgocr and it worked but the text didn't come out great. I found out that the project was abandoned in 2006 i think so I'm not sure where I go from here. I guess I'll try the pdf decoder but now I know that the ocr way is possible.

---

### Post by PaulFr on 2008-02-22
Perhaps **tesseract** or **gocr** may help. 'aptitude search ocr'

---

### Post by slymi2005 on 2008-02-22
ok I downloaded them, what now?

---

### Post by spiderbatdad on 2008-02-22
nm

---

### Post by roboxking on 2008-02-22
Your problem seems to me like one huge mess. As a programmer, I know that such a task would require heavy programming mumbo jumbo, and the software may be incredibly hard to find, let alone free. Sorry I couldn't be more help, but such a program, is very hard to find.

---

### Post by gnelson on 2008-02-22
You definitely need OCR (Optical Character Recognition) software, but I have found that most of it is lacking - on any platform.  My advice: If it's a simple document, save yourself the headache and retype it.

But, if you wish to forge ahead with OCR, [this link]("http://ubuntuforums.org/showthread.php?t=361851") favors **tesseract** and there is a tutorial on getting it up and running.

---

### Post by irw on 2008-03-11
It depends on the complexety of the text.

I am currently learning French and have a simple list of words issued each week. I scan these with sane, and convert to text with gocr;

A spell checker and a few minor changes(or sometimes none), and I have my list on the PC - quicker than typing them out.

---

### Post by faintscrawl on 2008-03-12
I'm finding gocr doesn't recognize the words well at all. The source document is even a freshly printed document in 12-point times new roman. After gocr does its thing and spits out the text file it's mumbo jumbo.

---

### Post by castudil on 2008-03-12
Usually the quality of the recognition of letters depends directly on the quality of the image.

If the image has a very high quality, means that in one centimeter more points are captured in the image and thus, OCR software can be more accurate.

if your document just have simple words in standard size and font type, then its most likely that the problem is the image quality.

if you have the original document in paper, try to scan it in 300 or more dpi (dots per pixels) ad try with the OCR software again

---

