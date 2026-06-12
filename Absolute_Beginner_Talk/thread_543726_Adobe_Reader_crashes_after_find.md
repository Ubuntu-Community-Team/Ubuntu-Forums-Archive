---
title: "Adobe Reader crashes after find"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by rmccabe3701 on 2007-09-05
When I attempt to find a word in a pdf document using Adobe Reader (via control-F) Adobe immediately closes after it finds (or doesn't find) the word.  Someone please help me troubleshoot this.
Thanks.

---

### Post by sstusick on 2007-09-05
You could always use Evince, instead. It comes with Ubuntu by default.

---

### Post by svalding on 2007-09-05
You don't happen to have a hot key turned on someplace that using ctrl+f to close do you? Adobe could be misinterpreting that. How large is the file you are trying to find the word in? What version of Adobe is it?

---

### Post by asmoore82 on 2007-09-05
how was Adobe Reader installed?

---

### Post by dca on 2007-09-05
Has the PDF file been OCR'd???  If not, I don't think the 'find' function will work to begin with...

---

### Post by rmccabe3701 on 2007-09-05
This is how I installed adobe reader 

[http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox-in-feisty-fawn.html]("http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-with-plug-in-for-mozilla-firefox-in-feisty-fawn.html")

It is not an issue with the Control-F hot key since Adobe still closes when I locate Find through the menus.

I don't like Evince as much because the characters often appear aliased and it doesn't support text/figuring copying as well as adobe.

I have tried several (random) PDF files all with the same result (I have no idea what OCR'd means).

It is version 7.0.8.

I will re-install and see if that fixes anything.

---

### Post by dca on 2007-09-05
Optical Character Recignition.  See, when you search for text in OpenOffice or MS Office the files (ODF, .DOC, etc, etc) are still editable.  If you use Acrobat full vers (Pro) to convert an oddball text file or even Word Doc it doesn't OCR the file...  You need a 3rd party app to OCR it after conversion.  I may be off on this as far as this being the cause for Reader crashing, though...  OpenOffice is able to OCR the OO writer files it exports to PDF...

---

### Post by rmccabe3701 on 2007-09-05
Re-installation did not help -- I still have the same problem ...

---

### Post by rmccabe3701 on 2007-09-05
Update:  I re-installed using Synaptic Package Manager (instead of the command line apt-get) and it works great now.  I have no idea why it wasn't working before.  
Thanks for the help.

---

### Post by rmccabe3701 on 2007-09-05
Actually I found the problem:  For whatever reason the "find" capability only works on pdf files with a version number <= 1.2,  otherwise it crashes.  weird.

---

