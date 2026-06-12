---
title: "[SOLVED] Capture with scrolling window"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by sundol on 2007-04-05
I want to capture a long html page on internet. 
How can I do scrolling capture? just like snagit in Windows.

---

### Post by gary4gar on 2007-04-05
make a vedio of it by istanbul
> Istanbul is a desktop session recorder for the Free Desktop.  It records your session into an [Ogg]("http://www.xiph.org/") [Theora]("http://www.theora.org/") video file. To start the recording, you click on its icon in the notification area. To stop you click its icon again. It works on [GNOME]("http://www.gnome.org/"), [KDE]("http://www.kde.org/"), XFCE and others.
refer [http://live.gnome.org/Istanbul](http://live.gnome.org/Istanbul)

---

### Post by sundol on 2007-04-05
It's interesting but I want an image file rather than a movie file.
Is it impossible? Then, the movie file can be a second best answer.

---

### Post by nike984 on 2007-04-05
I also think snagit just when i saw the title :)
Making it into a video may be a solution which I never want to try.

What about printing the material into a pdf file,
then convert the pdf file into a jpg image file?

if you don't know how to print into a pdf file format,
you may use this short tutorial.

Print to PDF
==============================
   1. Install the cups-pdf package (I used version 2.2.0-1)
   2. Go to System -> Administration -> Printing
   3. Doubleclick "New Pinter"
  10. There is now a "PDF Printer" detected, select it
  11. Select the Generic, Postscript Color Printer (Rev 3b)
  12. Give it a name, like PDF Printer
  13. Right click on the newly created printer, and select Properties
  14. Click "Print a Test Page"
  15. The file should be in your Home folder, under the PDF folder 
==============================

I've seen the option in acrobat professional which enables to 
convert a pdf file into jpg image. So, I think there must be some 
kind of tools to convert pdf => jpg file in linux.

---

### Post by Dr. Nick on 2007-04-20
Thanks for the tip, Just what i wanted

here is a site you can use to convert pdf and other to different formats
[http://media-convert.com/](http://media-convert.com/)

unfortunately pdf-jpg doesnt look possible there, but you can convert it to txt or flash

---

### Post by sundol on 2007-07-21
> **nike984 said:**
> I also think snagit just when i saw the title :)
Making it into a video may be a solution which I never want to try.

What about printing the material into a pdf file,
then convert the pdf file into a jpg image file?

if you don't know how to print into a pdf file format,
you this short tutorial.

Print to PDF
==============================
   1. Install the cups-pdf package (I used version 2.2.0-1)
   2. Go to System -> Administration -> Printing
   3. Doubleclick "New Pinter"
  10. There is now a "PDF Printer" detected, select it
  11. Select the Generic, Postscript Color Printer (Rev 3b)
  12. Give it a name, like PDF Printer
  13. Right click on the newly created printer, and select Properties
  14. Click "Print a Test Page"
  15. The file should be in your Home folder, under the PDF folder 
==============================

I've seen the option in acrobat professional which enables to 
convert a pdf file into jpg image. So, I think there must be some 
kind of tools to convert pdf => jpg file in linux.

Thank you. 
I originally think that website -> an image file like jpeg but pdf file is also OK. :)

---

### Post by nike984 on 2007-08-14
> **nike984 said:**
> I also think snagit just when i saw the title :)
Making it into a video may be a solution which I never want to try.

What about printing the material into a pdf file,
then convert the pdf file into a jpg image file?

if you don't know how to print into a pdf file format,
you this short tutorial.

Print to PDF
==============================
   1. Install the cups-pdf package (I used version 2.2.0-1)
   2. Go to System -> Administration -> Printing
   3. Doubleclick "New Pinter"
  10. There is now a "PDF Printer" detected, select it
  11. Select the Generic, Postscript Color Printer (Rev 3b)
  12. Give it a name, like PDF Printer
  13. Right click on the newly created printer, and select Properties
  14. Click "Print a Test Page"
  15. The file should be in your Home folder, under the PDF folder 
==============================

I've seen the option in acrobat professional which enables to 
convert a pdf file into jpg image. So, I think there must be some 
kind of tools to convert pdf => jpg file in linux.

Recently I've found a very simple trick to convert PDF into jpg in Linux.
First, you must have imagemagick installed in your system.
Then open a terminal and print

```
convert abc.pdf abc.jpg
```

It is too simple

---

