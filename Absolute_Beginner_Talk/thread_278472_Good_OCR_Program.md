---
title: "Good OCR Program"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by njohn858 on 2006-10-16
Does anybody know of a good OCR (Object Character Recognition) program that I can use to convert pictures of text into editable text?

---

### Post by ron999 on 2006-10-16
Hi njohn
I have used ocrad, but it wasn't much good when I tried it.
This is the thread from when I was struggling:-
[http://www.ubuntuforums.org/showthread.php?t=252000&highlight=ocrad]("http://www.ubuntuforums.org/showthread.php?t=252000&highlight=ocrad")

---

### Post by mips on 2006-10-16
Had a look at Kooka ? (It's a kde app though if you are allergic to kde)

---

### Post by Marsolin on 2006-10-16
[Clara]("http://linuxappfinder.com/package/clara") is another good graphical option. [Tesseract]("http://linuxappfinder.com/package/tesseract-ocr") was just released by Google to the public domain and it is reportedly very accurate, but it must be run from the command line, which may or may not be a problem for you.

---

### Post by njohn858 on 2006-10-31
The best thing that I found was Kooka. In addition to installing Kooka, I had to install actual OCR programs (I installed both GOCR and OCRAD). I got the best results using the GOCR engine. After installing Kooka and the OCR programs, I had to point Kooka to the OCR install location in order for it to be able to convert the JPEG to text. 

Thanks to all who replied. Hope this helps those who come after!

Just a Note on the installation: All three programs: Kooka, GOCR, OCRAD can all be installed using Synaptic Package Manager.

---

### Post by flygin on 2006-12-16
Just improved the tesseract wrapper to use it with xsane: The wrapper script below lets you use tesseract with a GUI (xsane)!!

You can find a precompiled version of tesseract, too (no waranties). 

[http://www.geocities.com/thierryguy/](http://www.geocities.com/thierryguy/)

---

### Post by koshari on 2007-02-18
i have compiled a working version of tesseract from source and it work very well. 

[http://www.ubuntuforums.org/showthread.php?t=361851&highlight=ocr](http://www.ubuntuforums.org/showthread.php?t=361851&highlight=ocr)

---

### Post by ben2talk on 2008-05-18
> **njohn858 said:**
> 

Just a Note on the installation: All three programs: Kooka, GOCR, OCRAD can all be installed using Synaptic Package Manager.

Wow, I'm working on a Hardy Heron installation, and OCR didn't come up in Synaptic... is this being dropped? left behind in 2006 maybe :(

---

### Post by Ahunt on 2008-06-24
Ben: I have been working on this same issue and think I have it solved!

The package you need is available on System>Administration>Synaptic Package Manager and is called "gocr". There are a number of pacakages with this name, you want the one called just "gocr".

After installing it you can scan a document for OCR with XSANE using grayscale and TIFF settings. Set the output to "viewer". When the viewer comes up select file>OCR and it will save it as a .txt file in your home folder which you can then open with gEdit. 

So far I haven't found the accuracy great, but higher scan resultion may help that to some extent.

Hope that helps

---

