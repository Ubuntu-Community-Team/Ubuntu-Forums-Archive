---
title: "Converting text.jpg into text.txt?"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-01-21
Hi everyone,
As the thread's title suggests it, I got a .jpg email's attachment which is, in fact, a text.
Is there a way to convert this image to plain text so that I can, for instance, copy/paste it or modify it?

Any help would be much appreciated.

---

### Post by tom56 on 2007-01-21
You need some OCR software. Not sure what's out there for Ubuntu. Try googling.

EDIT: Someone else just asked a similar question so keep an eye on their thread too - [http://ubuntuforums.org/showthread.php?t=343237](http://ubuntuforums.org/showthread.php?t=343237)

---

### Post by jordilin on 2007-01-21
If it's really text, you can open it with gedit.

---

### Post by xyz on 2007-01-21
Thanks folks for pointing me in the right direction!
Trying this at the moment:
[Tesseract OCR]("http://sourceforge.net/project/downloading.php?group_id=158586&use_mirror=kent&filename=tesseract-1.02.tar.gz&81945140")
Will keep you posted.

---

### Post by xyz on 2007-01-21
> **jordilin said:**
> If it's really text, you can open it with gedit.
This doesn't seem to work. Thanks, though.
I'm assuming the text was scanned.

---

### Post by pebo on 2007-01-21
gocr or [ocrad]("http://www.gnu.org/software/ocrad/ocrad.html") 
Both can work through scanner programs such as kooka
hth

---

### Post by mikewhatever on 2007-01-21
If it is a scanned text, then it is much the same as a picture, in which case you definitely need OCR.

---

### Post by pebo on 2007-01-21
> **mikewhatever said:**
> If it is a scanned text, then it is much the same as a picture, in which case you definitely need OCR.

Not necessarily, if you convert the jpg to pbm format```
convert test.jpg test.pbm
```You need ImageMagick installed for this. Then ```
ocrad test.pbm > test.txt
```Can't beat the command line :wink:

---

### Post by CroEragon on 2007-01-21
Sorry for hijacking thread, but this is similar to your question so i'll post it here.
I have to do quite bit of translating, it there any program that would be able to convert scanned handwriting into plain text? I know im asking almost impossible, but i hope somebody know one. And BTW if program is for Win, no problem, i have dual-boot (but i prefer Ubuntu).

---

### Post by xyz on 2007-01-22
> **pebo said:**
> Not necessarily, if you convert the jpg to pbm format```
convert test.jpg test.pbm
```You need ImageMagick installed for this. Then ```
ocrad test.pbm > test.txt
```Can't beat the command line :wink:

First of all, thank you to everyone for helping. Much appreciated!
So...I converted my .jpg to a "claudio.pbm" file in my home.

I downloaded ocrad, uncompressed/instatlled it fine.
I have imagemagick.
Then I ran:
```
ocrad claudio.pbm > claudio.txt
```
and
> bash: ocrad: command not found

as root or user.
I'm obviously missing something but what?

---

### Post by rkh on 2007-01-22
I believe that you want to use an OCR -optical character recognition- program to convert it to a readable text file. clara and gocr are both in the repositories. I have played with them both a bit and, unfortunately haven't had great success with either one. 

First you need to convert the jpg into a format that the OCR can work with- like an pnm, pbm, pgm, ppm. This is easier. IF you have imagemagick installed -in the repos- the command would be convert filename.jpg filename.pnm(or whatever).

-hope this helps

RKH

---

### Post by pebo on 2007-01-22
> bash: ocrad: command not found
as root or user.
I'm obviously missing something but what?
It works ok on my setup.
You could try gocr - same syntax. I think the quality of the results depends on the scan resolution of the original, so don't expect miracles :wink:

---

### Post by ciscosurfer on 2007-01-22
And you've tried renaming the file to a .txt file instead of .jpg and then opening it?

---

### Post by xyz on 2007-01-23
Well it kinda worked but not really!
I opened the jpg file with The Gimp to improve the quality of the image.

Then I (re) converted the jpg to a pbm file and ran:
```
 gocr claudio1.pbm > claudio1.txt

```
and it did create the txt file.

However, the text's not correct. Here's a sample phrase. Sorry it's in French but I'm sure you'll see how strange it looks:

> La peînture de Glaudío _ell'Anna &tonne au premíer rggard. En$uîtg elIe nous
gptu_, s'empa% de...
And this is what it should read:
> La peinture de Claudio Dell'Anna étonne au premier regard. Ensuite elle nous capture, s'empare de...
This is the best, most understandable sentence I found in there!
What do you think? Any point in trying to "improve" again the image?Or...?

---

### Post by pebo on 2007-01-23
Probably the "Or" option, in the time you save you could probably learn to touch type! :D

---

### Post by xyz on 2007-01-24
> **pebo said:**
> Probably the "Or" option, in the time you save you could probably learn to touch type! :D
That's for sure! :wink: 
I just wanted to convert this file to see if Ubuntu could do it! Oh well...thx anyways!

---

### Post by Roasted on 2007-07-22
Question.

jason@jason:~$ cd Desktop
jason@jason:~/Desktop$ convert PIC.txt PIC.pbm
convert: Improper image header `PIC.txt'.



What's the problem here?

---

### Post by Roasted on 2007-07-22
Nobody has any idea? To my surprise I've found very little on a google search of this error... and seeing as though I listened to what was said above I really don't know what I'm doing wrong.

---

### Post by SammyBoy247 on 2008-02-03
> **Roasted said:**
> Question.

jason@jason:~$ cd Desktop
jason@jason:~/Desktop$ convert PIC.txt PIC.pbm
convert: Improper image header `PIC.txt'.



What's the problem here?


PIC.txt is not an image, it's a text file.

Convert is not OCR it's an Image converter.  JPG -> TIFF etc...

Convert will ignore the suffix and try to detect the format of the image PIC.txt from it's header, the first bytes of the file, looking for it's 'Magic Number" or any standard conventions of various image types.  All it finds are the first lines of your text file.

---

### Post by JazonEsti on 2008-02-12
> jason@jason-desktop:~$ convert page1.jpg page1.pbm 
convert: unable to open image `page1.jpg': No such file or directory.

I also tried it. But I got this. What am I missing?  The file in on the desktop.

---

