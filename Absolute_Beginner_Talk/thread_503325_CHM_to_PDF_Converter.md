---
title: "CHM to PDF Converter"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-07-17
I need to convert a CHM file to a PDF, so I can print out all the pages. Please assist!

---

### Post by Voynix on 2007-07-17
> **homerj742 said:**
> I need to convert a CHM file to a PDF, so I can print out all the pages. Please assist!

The best solution I have found for linux is to extract the pages from the chm file and then using  htmldoc  bundle the files as a pdf. This is what I normally do:

Install both libchm-bin and htmldoc. Using the terminal extract/decompile the chm file using something like: 

```
extract_chmLib your_book.chm target_directory
```The output will be a folder with lots of html files. Open htmldoc, import the html files (this normally takes some time as you have to manually place them in the right order) and select pdf as the output.

It has always worked for me. 

I hope this helps,

Voynix

---

### Post by homerj742 on 2007-07-17
I installed HTMLdoc, but I can't find it when I browse through my apps

---

### Post by Voynix on 2007-07-18
for some reason the icon does not appear on the menu. You can open it using the terminal by typing: htmldoc.

```
htmldoc
```

Cheers

---

### Post by deepclutch on 2007-07-18
devels,this is a cool app if built on.pls do make one chm to pdf convertor..thanks

---

### Post by Dylock on 2007-08-25
Just wanted to comment on this process, extract_chmlib seems to not preserve case sensitive filetypes

---

### Post by Golyadkin on 2007-08-25
Well, CHM is made for Windows, and the windows filesystems FAT32 and NTFS are not case sensitive. That might be a reason. (A .chm for viewing in Windows can never contain a file.txt and File.txt in the same directory.)

There is also a Gnome CHM viewer, called GnoCHM: [http://gnochm.sourceforge.net/](http://gnochm.sourceforge.net/) which you can use, and there is a program called xchm. They should both be in the repository.

---

### Post by odieman on 2007-12-30
I was looking for the same thing, it probably wasn't around here until recently.
But now there is a nice tool:

[http://www.karakas-online.de/forum/viewtopic.php?t=10275](http://www.karakas-online.de/forum/viewtopic.php?t=10275)

this will convert any of your .chm to PDF easy.

---

### Post by odieman on 2007-12-30
For Ubuntu users, there is a guide:
[http://code.google.com/p/chm2pdf/wiki/HowToInstall](http://code.google.com/p/chm2pdf/wiki/HowToInstall)

this is short and precise follow-through for installing all the dependencies before installing the 'chm2pdf' it self (just scroll down to the comment), I just tried it and it works great , indexed PDF out of .chm file - sweet

I just did one change - did not install the 'pdftk' - since author of the 'chm2pdf' script made changes to it and 'pdftk' is not needed any more ... works fine for me (tried).

---

### Post by deepclutch on 2008-01-01
@odieman: Thank You very much for letting us know of this project!thanks to the developers :D

---

