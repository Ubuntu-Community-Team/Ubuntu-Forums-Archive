---
title: "I need to open/read .pps/.jpeg files?"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-01-03
Hi everyone,
Would OO do it? I don't have it installed because it's 'heavy' and I, by far, don't need most of OO's options/functions. Abi's is fine for my need.
Or any other way?
Thanks for your time.

---

### Post by steve.horsley on 2007-01-03
Yes, OOo can oprn .pps files. I don't know what else can.

For jpegs, eog should do for viewing, and it's installed by default in Ubuntu. For editing jpegs, I would suggest gimp or gimpshop.

---

### Post by xyz on 2007-01-03
> **steve.horsley said:**
> Yes, OOo can oprn .pps files. I don't know what else can.

For jpegs, eog should do for viewing, and it's installed by default in Ubuntu. For editing jpegs, I would suggest gimp or gimpshop.
Thank you Steve!
So I tried to open "affiche.JPEG" with The Gimp and got this:
> JPEG image Message: Not a JPEG file - starts with 0x50 0x4b
I googled for "0x50 0x4b" and it returned that it was in fact a .zip file.
Sorry for misleading you but when I get a "affiche.JPEG"...I assume it is a JPEG file!
So in a terminal:
```
unzip affiche.JPEG
```
> th@luser:~/Desktop$ unzip affiche.JPEG
Archive:  affiche.JPEG
 extracting: mimetype
 extracting: Pictures/10000000000003070000016872E55C90.png
 extracting: Pictures/100000000000030700000065E864661D.png
 extracting: Pictures/100000000000023E0000002D6520C200.png
 extracting: Pictures/100000000000025800000144733A92BC.png
  inflating: content.xml
  inflating: styles.xml
 extracting: meta.xml
  inflating: settings.xml
  inflating: META-INF/manifest.xml

OK "affiche" just means 'poster'. I know what the file contains: a bunch of saxophones' photos + a few lines of text all on 1 page.

So unzipping created the files/folders you see in the above quote.
I'm telling you... I'm totally lost here! I just want this all on 1 page so I can print it.
What am I supposed to do now?

---

### Post by bartbes on 2007-01-03
In Abiword just choose to import images/pictures (I use the Dutch version, so sorry for bad translations), go to the right directory (where the pictures are) and import them. As I an see from your output it are .png files, which Abiword can handle. The text is in XML, which isn't plain text (as you could guess), AFAIK there's no way to import them correctly.

---

### Post by steve.horsley on 2007-01-03
I wonder if the original affiche.JPEG file is some kind of OpenDoc format. Try renaming it to affiche.odt and see if it opens with openoffice. Just a long shot, but the filensmes inside the archive look roughly right for an OpenDoc file (which is in fact a zip file with xml files inside).

---

### Post by bartbes on 2007-01-04
You're probably right, I once opened an odt file with the file archiver. So that came into my mind but I forgot it was with OOo files.

---

### Post by xyz on 2007-01-04
Thanks folks for your help!
The short story is OO opens JPEG files.
I'll post this in case it might help someone else.  In a terminal:
```
sudo aptitude install openoffice.org openoffice.org-gnome openoffice.org-java-common openoffice.org-l10n-en openoffice.org-help-en
```
Change the "en" to your language.
To launch it:
```
oobase, oocalc, oodraw, ooimpress, oowriter...or whatever you want
```
Obviouly:
*Applications > Office...*
I just launched it running:
```
oobase
```
Then:
*File > Open > Desktop > affiche.JPEG*
And there it was.
It also opened a .doc file containing images.

PS: Now I'll need to check into opening .pps files.
Good day/night to all!

---

### Post by steve.horsley on 2007-01-04
Gimp is right. IF OpenOffice can open the file and display it properly, then it's not a real jpeg file at all. JPEG (Joint Photographic Expert Group) format is for compressed images. The file has been mis-named.

---

### Post by macogw on 2007-01-04
OOo is installed by default unless you're using Xubuntu...

---

### Post by Hagar Delest on 2007-01-05
> **xyz said:**
> 
```
th@luser:~/Desktop$ unzip affiche.JPEG
Archive: affiche.JPEG
extracting: mimetype
extracting: Pictures/10000000000003070000016872E55C90.png
extracting: Pictures/100000000000030700000065E864661D.png
extracting: Pictures/100000000000023E0000002D6520C200.png
extracting: Pictures/100000000000025800000144733A92BC.png
inflating: content.xml
inflating: styles.xml
extracting: meta.xml
inflating: settings.xml
inflating: META-INF/manifest.xml
```
No, OOo cannot open .jpg files, it's not an image viewer (but it can display it in a document of course).

As said in a previous post, what you've unzipped is a .odt file, this is why it has opened also the doc file containing these pics. ODT is a XML based format, it is in fact a bunch of files zipped together. When pictures are embedded in a document, they are stored in the /Pictures folder of this archive.

The right filename of the file is affiche.JPEG.odt !

---

### Post by xyz on 2007-01-05
Thank you all for making it clear to me.
This document was obviously made in Windows, I'll just have to ask the person who emailed it to me why it was saved as a jpeg file.

---

