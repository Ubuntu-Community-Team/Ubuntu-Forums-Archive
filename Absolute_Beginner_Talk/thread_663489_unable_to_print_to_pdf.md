---
title: "unable to print to pdf"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2008-01-10
i have installed cups-pdf and configured the pdf in kubuntu (see screenshot 1). however when i try to take a printout through swiftfox, it doesn't display any other printer other than postscript (see screenshot 2). i don't want a postscript printer because the files do not open in acrobat reader. why isn't my print to pdf printer shown in swiftfox?

---

### Post by thenailedone on 2008-01-10
> **rkakkar said:**
> i have installed cups-pdf and configured the pdf in kubuntu (see screenshot 1). however when i try to take a printout through swiftfox, it doesn't display any other printer other than postscript (see screenshot 2). i don't want a postscript printer because the files do not open in acrobat reader. why isn't my print to pdf printer shown in swiftfox?

Had a look at what cups-pdf is all about and it seems that it is aimed at giving the option of printing to PDF on a network scale... 

From [http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/welcome.shtml:](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/welcome.shtml:)
> This software is designed to produce PDF files in a heterogeneous network by providing a PDF printer on the central fileserver.

Not sure how you are trying to use it...

---

### Post by rkakkar on 2008-01-10
> **thenailedone said:**
> Had a look at what cups-pdf is all about and it seems that it is aimed at giving the option of printing to PDF on a network scale... 

From [http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/welcome.shtml:](http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/welcome.shtml:)


Not sure how you are trying to use it...

okay.. so then how can i install a pdf writer?

---

### Post by mikeyphi on 2008-01-10
> **rkakkar said:**
> i have installed cups-pdf and configured the pdf in kubuntu (see screenshot 1). however when i try to take a printout through swiftfox, it doesn't display any other printer other than postscript (see screenshot 2). i don't want a postscript printer because the files do not open in acrobat reader. why isn't my print to pdf printer shown in swiftfox?

Have you got any 'real' printers connected to your system?
I run Firefox and it shows my two real printers and Cups/PDF and Postcript.

Could be a swiftfox problem? (never used it) or try rebooting!!!

Just looked at screeshot2 again - did you try the down arrow at the postscript window?

---

### Post by philinux on 2008-01-10
Just had a look at System>Admin>Printing.

I've one printer on my standalone system. If I choose add printer, one option is for a print to pdf type. Maybe this is the solution.

---

### Post by rkakkar on 2008-01-10
i installed the cups pdf printer with the generic postscript driver and it worked. however the images are all garbled. see attachment (see the ubuntu logo)

---

### Post by philinux on 2008-01-10
Ok so we are a step forward in the right direction then. :)

---

### Post by rkakkar on 2008-01-10
> **philinux said:**
> Ok so we are a step forward in the right direction then. :)

but not quite there yet :).. any idea why this is happening? i suspect the generic driver, but i don't know which other to install...

---

### Post by philinux on 2008-01-10
Looking at your screenshot most fonts look ok except the ubuntu logo.

Could it be a font thing? Or the generic driver?

Whats the pdf file look like in evince?

---

### Post by rkakkar on 2008-01-10
> **philinux said:**
> Looking at your screenshot most fonts look ok except the ubuntu logo.

Could it be a font thing? Or the generic driver?

Whats the pdf file look like in evince?

could be either dude... haven't tried it in evince.. same show in kpdf... will try playing with the settings...

---

### Post by thenailedone on 2008-01-11
So any luck yet... glad you can use the pdf printer on a standalone system :)

---

### Post by stchman on 2008-01-11
> **rkakkar said:**
> i have installed cups-pdf and configured the pdf in kubuntu (see screenshot 1). however when i try to take a printout through swiftfox, it doesn't display any other printer other than postscript (see screenshot 2). i don't want a postscript printer because the files do not open in acrobat reader. why isn't my print to pdf printer shown in swiftfox?

I have a tutorial on the cups-pdf package.

[http://www.stchman.com/pdf_cups.html](http://www.stchman.com/pdf_cups.html)

This is geared towards Gnome but should work the same with KDE.  The resultant output file is a .pdf file which should open in Acrobat.

---

### Post by rkakkar on 2008-01-11
it prints but images are still garbled! so as of now i use a workaround... i print using the default Kubuntu postscript printer and then use a free online postscript to pdf convertor :P. its cumbersome but gets the job done.

---

### Post by John Jason Jordan on 2008-01-22
> **stchman said:**
> I have a tutorial on the cups-pdf package.

[http://www.stchman.com/pdf_cups.html](http://www.stchman.com/pdf_cups.html)

This is geared towards Gnome but should work the same with KDE.  The resultant output file is a .pdf file which should open in Acrobat.
I tried this, but the instructions on the above link must be for an earlier version of Ubuntu, not Gutsy. There is no Generic printer in the listing of printer manufacturers.

I have installed cups-pdf, and I have installed a PDF_file_generator. But when I print to it I get a PS file, not a PDF file, and it defaults to my home folder, not /home/PDF/. Adobe Reader refuses to open the file  because it is not a PDF file, even if I rename it *.pdf.

The only way I can do anything with the PS file is to open it in KPDF, which pops up a window saying it is converting the PS to PDF. However, the resulting file is a bitmap, not a vector image, even though the data in the file I "printed" to the PDF_file_generator was a vector drawing.

Any suggestions welcome!

---

### Post by zhanglini on 2008-03-02
I am using Gutsy, when I print PDF, I can't find the print out anywhere, not in /home, nor is /home/pdf folder created.
Any help?

---

### Post by John Jason Jordan on 2008-03-02
> **zhanglini said:**
> I am using Gutsy, when I print PDF, I can't find the print out anywhere, not in /home, nor is /home/pdf folder created. Any help?
Try it again, and this time give the file a strange and unique name. Then go to a command line and type "locate <your strange and unique filename>. This should search for it everywhere on your computer and tell you the path to it.

---

### Post by zhanglini on 2008-03-02
> **John Jason Jordan said:**
> Try it again, and this time give the file a strange and unique name. Then go to a command line and type "locate <your strange and unique filename>. This should search for it everywhere on your computer and tell you the path to it.

Well I was never given the chance to give a file name.  When I select file>print, a "print" window came up, so I clicked print.  Another "printing" window came up and stayed for 5 sec before it disappeared.  
Maybe nothing was ever printed?

---

### Post by John Jason Jordan on 2008-03-02
> **zhanglini said:**
> Well I was never given the chance to give a file name.  When I select file>print, a "print" window came up, so I clicked print.  Another "printing" window came up and stayed for 5 sec before it disappeared.  
Maybe nothing was ever printed?
First, I misremembered something - cups-pdf does not pop up a filename window. 

Second, go to Applications > Accessories > Manage Print Jobs and see if there are any unprinted print jobs in a queue.If so, it means that cups.pdf is not installed or is not installed correctly.

Also, when you go to print something, look to see what printer is selected. You should have an option like "CUPS PDF File Generator." When you print to this "printer" it should produce a file with a name related to the application and document you printed, ending in .pdf. This document should appear in a folder labeled PDF in your home folder. Note that the folder name is case sensitive.

You could also try reinstalling cups-pdf from Synaptic. The package you want to install is called cups-pdf and you can just Search for it.

---

### Post by zhanglini on 2008-03-02
> **John Jason Jordan said:**
> 
You could also try reinstalling cups-pdf from Synaptic. The package you want to install is called cups-pdf and you can just Search for it.

Thanks again, I just reinstalled cups and everything is good now.
Before I did that , the only printer was "postcript/default" something (did not have cups).

---

