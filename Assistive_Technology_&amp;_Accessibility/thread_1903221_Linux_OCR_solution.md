---
title: "Linux OCR solution"
date: 2012-01-01
forum: Assistive Technology &amp; Accessibility
---

### Post by jtarin on 2012-01-01
OCR in Linux is alive and well.
Lios is a free and open source software for converting print in to text using a scanner. It can also produce text out of scanned images from other sources. Program is given total accessibility for visually impaired.

Features

1 Single scan & Repeated Scanning, 2 Scan images from folder or Pdf, 3 Full GUI environment, 4 Brightness optimizer, 5 Audio converter, 6 Easily Accessible Preference Window, 7 5 OCR Engines (OCROPUS,CUNEIFORM,TESSERACT,GOCR,OCRAD), 8 Good text manipulation with Find, Go-To-Page, Append file, Punch File. 9 Low vision support in the tools menu, 10 Dictionary Support for english(Artha) 11 And more features are in the preferences. 
[http://code.google.com/p/linux-intelligent-ocr-solution/](http://code.google.com/p/linux-intelligent-ocr-solution/)

---

### Post by robert shearer on 2012-02-10
looks good but alas does not open files :-( so no processing is possible.
Oneiric 11.10

---

### Post by russell hedger on 2012-02-13
I could not get this to run properly on kubuntu 11.10. I also had problems uninstalling the package, and had to resort to deleting it manually as the packaged uninstall scripts failed. Will be a useful application if it can be fixed.

---

### Post by nalin4linux77 on 2012-02-27
[SIZE=4][COLOR=Blue]**Linux-intelligent-ocr-solution**
[/COLOR][/SIZE][COLOR=Blue] [/COLOR]
LIOS is a free and open source software for converting print in to text  using either scanner or a camera. It can also produce text out of  scanned images from other sources. Program is given total accessibility  for visually impaired. LIOS is written in python and we release it under  GPL3 license. LIOS will work with Debian based operating systems. LIOS  is an effort from the easy-ocr development team. There are great many  possibilities for this program. Feedback is the key to it. expecting  your feedback. 
[B]
[COLOR=Lime]HOW TO INSTALL[/COLOR][/B]

[B]Download deb file from here [http://linux-intelligent-ocr-solution.googlecode.com/](http://linux-intelligent-ocr-solution.googlecode.com/) download the latest deb package and install
What is new in LIOS-1.2
1 Cam-Scan,
2 Cam-Reader,
3 Scan-to-image-only,[/B]:guitar:
[B]4 Scan-to-images-repeatedly,
5 Introduction of py-sane, Glaid library make the program faster and efficient,
6 Multiple arguments are handled effectively,
7 Ocr a single Image,
8 Artha shortcut (alt+control+W),
9 Beta version of spell-checker,
10 Provision for submitting issues in the About Dialog.
Features
1 Single scan & Repeated Scanning,
2 Ocr Folder,
3 Ocr Pdf,
4 Ocr image only,
5 Cam-Scan and Cam-Reader,
6 Scan-for-image-only & repeatedly,
7 24 Language support (Given at the end),
8 Full GUI environment,
9 Selection of starting page number, page numbering mode and number of pages to scan,
10 Selection of Scan area, brightness, resolution and time between repeated scanning,
11 Full Auto Rotation,[/B]:lolflag:
[B]12 Brightness optimizer,
13 Audio converter,
14 Easily Accessible Preferences Window,
15 5 OCR Engines (OCROPUS,CUNEIFORM,TESSERACT,GOCR,OCRAD),
16 Good text manipulation with Find, Go-To-Page, Go-To-Line, Append file, Punch File.
17 Display Preferences for Low vision,
18 Dictionary Support for English(Artha)
19 Beta version of spell-checker,
20 Provision for submitting issues,
21 And more features are in the preferences.[/B]
**How to start using LIOS.**
1. Scanning.

In order to start new scan, first press ctrl+n and then press f9 for  single scan or ctrl+f9 for repeated scanning. To set the scanning  preferences press ctrl+p and set the starting page number, Mode of page  numbering, double page mode if you intend to keep 2 pages at a time,  rotation to select the way in which you want the program to rotate the  images before conversion. In full automatic rotation mode, one can keep  the book in 00 90 180 and 270 degree angle. In partial rotation mode  program will scan once to find out the position of the book and then the  rotation will be kept. In manual mode one should select the angle.  partial and manual mode is faster than full auto rotation mode in ocr  process. One can select the number of pages to be scanned at a stretch  by setting number of pages in the case of repeated scanning. One can  stop all scanning process by pressing ctrl f4.
2. Cam-scan.

one can now use Hovercam or a Webcam to produce text in LIOS.  Adjustments with these devices can be made using LIOS-cam-preferences in  edit menu. This feature will help to read books and other printed  materials such as visiting cards currency and like and also it makes the  ocr process very fast and accurate. Please be specific to use devices  with auto focusing facility. remember that there is no autorotation in  this utility.so for the same reason, support of a stand for the webcam  will be highly appreciated.
3. Cam-reader.

is the utility which will give a continuous output as one moves the  webcam. First it will create the image and then will produce the text  and it will start reading. After the completion of reading, it will  repeat the process automatically. In cam-scan, one has to take the photo  and it will be converted in to text.
4. Ocr Image.

LIOS can convert image file to text which is in jpg, tif, png, pnm and bmp.
5. Ocr folder.

LIOS can convert scanned images from other sources. It can convert jpg,  jpeg, tif, tiff png, pnm, formats. To convert the images in a folder,  select scan from folder option from scan menu and then select the input  folder.
6. Ocr Pdf file.

Select Ocr pdf from scan menu and then select the input file. It is  recommended that one can use ocropus as engine more efficiently in pdf  conversion.
7. scan for image only and scan for images only repeatedly.

Help one to scan only images and it will give the user opportunity to  utilize different ocr engines conveniently. Also it avoids delay between  each scan if one does not want to listen to the output. Images will be  saved in LIOS or one can choose his own destination. Now conversion can  be done using folder option.
8. Brightness checker.

To set a n exact value of brightness or threshold is the best way to  ensure maximum efficiency out of ocr engines. To find out the best  value, go to tools menu and select brightness checker. This utility will  scan for 15 or 17 times to complete the process. After the process,  number of words detected at different values will be shone in tabs. If  you want to know the precise value only, shift tab and then tab to apply  the value.
9. Audio conversion.

LIOS can convert the text opened in LIOS to wav files. To convert the  text in to speech, go to tools menu and select audio converter.
10. Text Manipulation.

To go to page, press ctrl+g and then type the page number, and tab to  OK. In the case of double page type only odd number, for example 1 in  the case of 1-2 and 11 in the case of 11-12. One can go to any line by  pressing ctrl+l and ctrl+f will help to find any word in the document.
11. Display preferences.

display preferences in the edit menu will help to set fond size, color , italic, bold and color of the background.
12. Engines.

There are 5 engines in LIOS.out of these only cuneiform can handle 24  languages, list given at the end. All other engines can handle only  English. Cuneiform is good for speed and picture skipping ,ocropus is  good for layout analysis and pdf conversion.
13. Artha.

In order to find out the meaning of English words, first select the word  and then press alt+ctrl+w and tab to find the meaning. Caution for the  first time one has to press alt+control+w twice so as to switch on artha
14. Spell checker.

A beta version of spell checker is added to the program.press ctrl f7  and all the misspelled words will appear and one can change them.
Cuneiform support Bulgarian, Croatian, Czech, Danish, Dutch, English,  Estonian, French, German, Hungarian, Italian, Latvian, Lithuanian,  Polish, Portuguese, Romanian, Russian, Russian-English bilingual,  Serbian, Slovene, Spanish, Swedish, Turkish, and Ukrainian.
Disclaimer

    Copyright (c) 2011-2012 LIOS Development Team 

    All rights reserved . Redistribution and use in source and binary  forms, with or without modification, are permitted provided that the  following conditions are met: 

    Redistributions of source code must retain the below copyright notice, 

    this list of conditions and the following disclaimer. 

    Redistributions in binary form must reproduce the below copyright notice, 

    this list of conditions and the following disclaimer in the  documentation and/or other materials provided with the distribution. 

    Neither the name of the nor the easyocr team names of its 

    contributors may be used to endorse or promote products derived from  this software without specific prior written permission. 

    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS  "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT  LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A  PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER  OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED  TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR  PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF  LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING  NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS  SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAG:guitar:E." 

**FREE SOFTWARE FREE SOCIETY**:lolflag:

---

### Post by jtarin on 2012-02-27
Now this seems to have a great potential and I will be downloading it and testing soon. I will give feedback as soon as I've run it through its paces. Thanks so much for your endeavor. Keep us posted of any new developments.

---

### Post by russell hedger on 2012-02-29
I have tried version 1.2 and got further than before. The package seems to install and uninstall OK. One dependency probably worth adding is desktop-file-utils as I had to install this to get the package to install.

Scan&OCR -> caused the scanner to run, followed by a fragment of unintelligible speech and then nothing. I tried all the speech engines with similar results. Typical output on the console is as follows:

```
Device : Perfection V330 Photo
('00', 'CUNEIFORM', 'eng')
Cuneiform for Linux 1.1.0
('90', 'CUNEIFORM', 'eng')
Cuneiform for Linux 1.1.0
('180', 'CUNEIFORM', 'eng')
Cuneiform for Linux 1.1.0
('270', 'CUNEIFORM', 'eng')
Cuneiform for Linux 1.1.0
ALSA lib pcm.c:7316:(snd_pcm_recover) underrun occurred
ALSA lib pcm.c:7316:(snd_pcm_recover) underrun occurred
ALSA lib pcm.c:7316:(snd_pcm_recover) underrun occurred
ALSA lib pcm.c:7316:(snd_pcm_recover) underrun occurred
ALSA lib pcm.c:7316:(snd_pcm_recover) underrun occurred
ALSA lib pcm.c:7316:(snd_pcm_recover) underrun occurred
cat: temp.txt: No such file or directory
rm: cannot remove `*.tif': No such file or directory
rm: cannot remove `*.html': No such file or directory
rm: cannot remove `*.wav': No such file or directory
rm: cannot remove `*.png': No such file or directory
rm: cannot remove `*.jpeg': No such file or directory
rm: cannot remove `*.jpg': No such file or directory
rm: cannot remove `scanimage.text': No such file or directory
Found

```Cam-Scan -> The camera light flashed briefly and then no further activity.

Scan-Image-Only-> Scanner runs, voice says 'The page appears to be blank', blank image saved. (The page has clear printed text)

OCR-Image -> Failed to OCR text.

EDIT:

Managed to OCR an image using the tesseract OCR engine but takes several minutes to complete - just a few seconds when done from the command line.

---

### Post by SuB-ZEro on 2012-03-15
Hi,

I've seen that Version 1.3 has been released and I give it a try.

- The Install completes without any errors.
- The speech output is a little bit irritating and I don't find an option to deactivate it.
- I'm missing an progress-bar or something, I only see the cpu-load on my systemmonitor

All in all, it does what it should, it gives my not the feeling of an finished program, but it will be it in future.

---

### Post by nalin4linux77 on 2012-03-19
Dear all lios is in a stable position now. If you have any probleam with scan&ocr  try with the brightness optimizer in the tools menu first. It will scan more than 15-17 times and  then it will show you the brightness statistics and give apply button. Then start scan by pressing F9 or control+F9 :guitar:

---

### Post by ghoest on 2012-09-05
Hello to all ubuntu enthusiasts!
I´m here for the first time and posting first time in a forum at all. so, please, be patient with me.
I just installed lios on Kubuntu 12.04 and found a start button, but it always crashes with the info: lios.py crashed with *ImportError in /usr/share/lios/tools.py: No module named speechd*,  when started in terminal with: *no command found*.
Can you tell me, how to handle this? Thanks.

---

### Post by nalin4linux77 on 2012-09-05
I think you have to install python-speechd 

So try to install it by running 
**sudo apt-get install python-speechd**

---

### Post by tienlbhoc on 2012-09-05
Thank for introduction, but not really good recognize

---

### Post by ktat on 2012-09-23
Hi, I'm using Ubuntu 10.04 LTS - the Lucid Lynx. I've just installed the .deb from nalin's link.  There were no errors during the install process, however, nothing happens when I click on the short cut in the applications menu.

I tried starting from the terminal with the command:
```
lios
```
and got:
```
lios: command not found
```

Then I tried:
```
xxx@ubuntu-10:~$ cd /usr/share/lios/
xxx@ubuntu-10:/usr/share/lios$ ./lios.py
```
and got the errors:
```
import: unable to read X window image `': Resource temporarily unavailable @ xwindow.c/XImportImage/5020.
./lios.py: line 8: global: command not found
from: can't read /var/mail/espeak
from: can't read /var/mail/multiprocessing
from: can't read /var/mail/subprocess
./lios.py: line 13: syntax error near unexpected token `('
./lios.py: line 13: `directory = ("%s/LIOS" % (os.environ['HOME']))'
```

I would really like to test this software out, can anyone help with this, please?

---

### Post by Waddle on 2012-10-27
> **russell hedger said:**
> I could not get this to run properly on kubuntu 11.10. I also had problems uninstalling the package, and had to resort to deleting it manually as the packaged uninstall scripts failed. Will be a useful application if it can be fixed.


I have the same problem in Kubuntu 12.04. How did you actually un-install it? Thank you!

---

### Post by NewAmercnClasic on 2012-11-13
Google Docs will read and convert PDF image texts to editable text files, however it leaves much to be desired as the formatting gets a little crazy and the load times are not quick.  I would definitely prefer a native OS solution out of the box with Ubuntu.

---

### Post by kagashe on 2013-03-27
I was looking for good OCR software to convert scanned PDF files to text and tried ABBYY Fine Reader online but after converting 3 pages the free trial stopped. Before that I had tried pdfocr and tesseract. Then I discovered this thread. This is working very well. Thank you.

---

### Post by M3m3nt0 on 2013-04-15
I downloaded the 1.7 version and installed through Ubuntu Software Center on a Ubuntu 12.04 x64 machine.
When I launch the program I got this error:

```

~$ lios
Traceback (most recent call last):
  File "/usr/bin/lios", line 3, in <module>
    from lios.lios import *
  File "/usr/lib/python2.7/dist-packages/lios/lios.py", line 12, in <module>
    import gnomecanvas
ImportError: No module named gnomecanvas

```

Can someone help try this OCR? :)

---

### Post by kagashe on 2013-04-17
> **M3m3nt0 said:**
> I downloaded the 1.7 version and installed through Ubuntu Software Center on a Ubuntu 12.04 x64 machine.
When I launch the program I got this error:

```

~$ lios
Traceback (most recent call last):
  File "/usr/bin/lios", line 3, in <module>
    from lios.lios import *
  File "/usr/lib/python2.7/dist-packages/lios/lios.py", line 12, in <module>
    import gnomecanvas
ImportError: No module named gnomecanvas

```

Can someone help try this OCR? :)Install python-gnomedesktop and python-gnome2

Kamalakar

---

### Post by Buntu Bunny on 2013-05-01
I have missed OCR with Ubuntu and was delighted to find this thread. Sounds like there are still some quirks, but I hope to give this a try soon.

---

