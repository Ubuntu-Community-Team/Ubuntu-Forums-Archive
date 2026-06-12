---
title: "Print to Speech Reader"
date: 2012-02-13
forum: Assistive Technology &amp; Accessibility
---

### Post by russell hedger on 2012-02-13
I have been investigating Print-to-Speech-Readers for someone who has lost their sight, and having balked at the price and performance of the commercial devices I have seen, wondered whether it would be possible to put together a system based on a flatbed scanner and Linux.

It sounds simple: scan image --> clean image --> ocr image --> speak ocr text. If I can get all these components working well, then I should be able to make a system that can read and speak the front of envelopes, letters, flyers, and perhaps magazines. So far, I have managed to get a clear text-to-speech voice using a patched version of the festival speech engine together with ****Nitech HTS voices, and reasonable OCR performance using the latest tesseract (3.01) engine. Scanning is simple using the SANE scanimage command, and I have found best results scanning at 600dpi in greyscale and then using scantailor to clean up and deskew the image prior to OCR.

What I have not found yet is a decent layout analysis application that can be run from the command line. The latest tesseract is supposed to perform some kind of layout analysis, but it still gets confused by much of the material that I would like to OCR. For example, local newsletters often include a variety of bizarre fonts, blocks of text enclosed by various solid and dotted borders and often with embedded images. Something that could strip the text areas out of such an image for OCR would be ideal. I have tried OCRFeeder, which sometimes helps although the CLI version does not yet output plain text for text-to-speech.

The other problem I have is with scanning time. I get best results scanning at 600 dpi, but this takes 40s just to scan the page on an Epson V330. I haven't managed to find anything with Linux drivers that is faster.

It would be good to hear from anyone who has also looked at this problem, or anyone with any suggestions to improve the performance. I am sure there are many people who could benefit from a reliable Ubuntu-based print-to-speech system.

Russ

---

### Post by drdos2006 on 2012-02-13
I have been experimenting with espeak. The ocr needs to be converted into text though. For help type  espeak --help.

For instance I copied your post, went into terminal mode, typed   espeak -s120 "  and pasted your post plus the end quote ", hit enter.

Perhaps that might help.

regards

---

### Post by russell hedger on 2012-02-21
The clearest free voices that I have found are the Nitech HTS ones, which I have been running using the festival speech engine.

It took a bit of work to get the Nitech voices running because the current version of festival in Ubuntu 11.10 is no longer compatible with the old versions of the Nitech voices. A patch to festival allowing the old Nitech voices to work is available, but requires patching and compiling the source code as detailed here:

[http://ubuntuforums.org/showpost.php?p=11507322&postcount=148](http://ubuntuforums.org/showpost.php?p=11507322&postcount=148)

It is possible to rebuild the Nitech HTS voices to be compatible with the current version of festival, but it looked rather complicated and takes a day or so to complete the processing according to someone who managed to build a voice (as detailed on the thread linked to above).

Some of the voices on the demo page for festival are really good. Unfortunately, these voices are not yet available.

[http://www.cstr.ed.ac.uk/projects/festival/morevoices.html](http://www.cstr.ed.ac.uk/projects/festival/morevoices.html)

Cepstral make some festival compatible voices. I tried the demo, but didn't think they were as good as the Nitech ones.

---

### Post by blaineclrk on 2012-02-22
Hi Russel, take a look at Vinux. It's Ubuntu that's been scripted to augment the features needed for many types of visual impairments. There's a Speedy-OCR package and an Easy-OCR package that have been put together just for what you're looking for. Mail, magazines, books, newspapers, what have you are scanned on a document scanner and processed right through to Orca reading the results. And I believe even files such as PDFs can be fed into these OCR packages. Start at [http://distrowatch.com/table.php?distribution=vinux](http://distrowatch.com/table.php?distribution=vinux) and follow the links to the home site and the support group list. Somewhere in the mix is a utility that's called unpaper if I recall right, or something similar. Unpaper(?) should strip out the non-text elements that give you trouble. Whatever it is, it's built right into the special OCR packages. At any rate, the Vinux project is the one to check out and ask question about. It might be just what you and your friend are looking for.

---

### Post by blaineclrk on 2012-02-22
I forgot to mention voice packages; [http://voxin.oralux.net/index.php](http://voxin.oralux.net/index.php) has many realistic packages and they run about $7 each. Not expensive at all.

---

### Post by russell hedger on 2012-02-22
Hi blaineclrk, thanks for your suggestions. I'll have a go with vinux and see what it is like.

The  person I am trying to set this up for is not computer literate and  needs a very simple interface. At the moment, I have a script that waits  for a key press before scanning and speaking the document. If I can get  acceptable print-to-speech working, then I will progress to adding my  functions, but the interface will need to be simple - perhaps an  external controller of some kind.

I have tried both easyocr and  its current incarnation LIOS without success - could not get either  application to run and the uninstall scripts don't work, so had to  manually remove the packages and associated files from my system. Others  report similar trouble, but perhaps these work OK in vinux.

OCR  is my current sticking point - the best open source OCR engine seems to  be tesseract. Tesseract works quite well for reading regular magazine  print for example, and can recognise text columns. However, I want to  set something up that can read the front of envelopes, fliers and local  pamphlets. Tesseract often gets confused. I'll attach a scan of a simple  page that illustrates the type of formatting that trips up tesseract.  Many of the local pamphlets are much worse, with a mix of bizarre fonts,  dotted and dashed boxes etc.

I have tried unpaper, and it works  OK to de-skew a scan and enhance contrast but is not able to analyse  layout so that relevant image sections can be passed to the ocr engine.  Scantailor performs a similar job to unpaper and has both a gui and cli  interface - seems to work well.

OCRfeeder attempts to perform  layout analysis, but in my experience is not much better at this than  the latest release of tesseract (3.01). The tesseract developers say  that it can be tuned to get better performance so I will see if they  have anything to say about processing this kind of material.

Of  course, there is the ABBYY Finereader OCR engine for linux, but this is  rather expensive, although I am prepared to pay if this works and is the  only solution.

I have installed the Voxin add-on with IBM Viavoice. The voice isn't bad, but I find the Nitech HTS ones to be clearer.

The  other thing is a faster scanner - current EPSON V330 takes 45 seconds  to scan a page. The canoscan 9000F looks much faster but is fairly  expensive for a flatbed scanner and has no SANE driver yet.

Russ


[http://ubuntuone.com/16ZChlmlip5o4VONuChMpL](http://ubuntuone.com/16ZChlmlip5o4VONuChMpL)

---

