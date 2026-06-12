---
title: "Convert2PDF"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-10
I downloaded this tarball (where did that interesting designation for a compressed package come from??) and can click "open" in Firefox's download dialog box to see the contents.  I can (and have) extracted it into a directory.  I can see the various files in the package, one of which is an executable called Convert2PDF, but it has an orange Lock icon next to it and does nothing when I double click.  There is a file called Install.sh, but double clicking it also does nothing.

I tried to execute terminal commands to extract the tarball, but that didn't work, either.  Something about a child and an error 2, I don't know what all that means.

So, how do I go about installing this package.

I hate to keep relating to my many years of Windows experience, but, in XP, I use a neat little program called PrimoPDF that looks to and works on my system like just another printer, but, when I invoke it to print a document, it creates a PDF at any location of my choice which I can then attach to emails, etc.

This program appears to serve the same function.  I just need to install it.

One of Ubuntu's strongest features (that by default you can only download from the repos) also proves frustrating to new users who (like me) would be willing to compromise their system in order to try new things.  I feel like, if I mess things up, I'll just tear everything down and rebuild it.

That said, I must say, I do enjoy the security and stability of Ubuntu.  It is now my OS of choice except when I have to do work using XP aps for which I have yet to find substitutions.  The day will come when I will convert my entire enterprise to Ubuntu.  

Already, I can surf the net in Ubuntu and rarely get pop-ups.  Firefox works without being constantly interrupted by Internet Explorer's persistent attempts to establish itself as my default browser (that is a new windows problem . . . and one that prompted me to explore for other operating systems . . . recently, something has happened that causes explorer to just rear up at anytime.  I wiped my system and reinstalled XP, but the problem was not solved, so I assume it is MS induced).

Sorry to have gone on a rant.  I would really like to learn how to install programs that I just go out and download from the net.  I did successfully install Lightzone by just extracting it using the package manager to its own directory, then, clicking on the executable - that was simple.

I'm not having much luck with Convert2PDF.

Help would be appreciated.

Caruso

---

### Post by Sef on 2007-05-10
Open Office Word Processor can export as PDF.   Either click the button or look under File on the menu.

If you really want to use Convert2PDF, could you provide a link to it.

---

### Post by useResa on 2007-05-10
If you would like to have the same functionality (that is printing to PDF), please read this article "[Print to PDF with CUPS]("http://doc.gwos.org/index.php/Print_to_PDF_with_CUPS")".
 
**NOTE:** AFAIK the only difference is that currently it is "Postscript Color Printer (Rev 4)" instead of Rev 3b as indicated.

---

### Post by hyperair on 2007-05-10
The orange lock icon means that the file is only read-only to you. Besides that it would seem that you do not have execution permissions on the file. So, what you need to do is change the permissions of the file. Right click it and click properties. Then go to permissions and check "Allow executing as a program".

---

### Post by carusoswi on 2007-05-10
> **Sef said:**
> Open Office Word Processor can export as PDF.   Either click the button or look under File on the menu.

If you really want to use Convert2PDF, could you provide a link to it.

I know that I can export as PDF from OO, thanks (and that's a pretty neat feature - can't do that in MS Word!), but, I need to be able to export other non word processing files as well. For instance, there are occasions when I want to export a spread sheet, or a report from my relational database (Ms Access running on Ubuntu for now).  

That's why I'm looking for a pdf printer.

Here's the link: [http://www.amyuni.com/en/support/downloads.html](http://www.amyuni.com/en/support/downloads.html)

Thanks,
Caruso

---

### Post by kamillozo on 2007-05-10
> **carusoswi said:**
> There is a file called Install.sh, but double clicking it also does nothing.
So, how do I go about installing this package.
Open terminal, go to the folder with extracted content, then  type:
sudo chmod +x Install.sh
then:
sudo sh Install.sh

---

### Post by hyperair on 2007-05-10
PDF Printer eh? Why don't you get one that's more integrated with Ubuntu?
```
sudo apt-get install cups-pdf
``` or install package "cups-pdf" in Synaptic. Once installed, I think it'll automatically configure CUPS during installation and then you can just print from any application by choosing the Virtual_Printer. I use that and I think it's pretty cool. It works flawlessly for me.

---

### Post by dca on 2007-05-10
The OO spreadsheet has a convert to PDF option...

---

### Post by shuttleworthwannabe on 2007-05-10
> **hyperair said:**
> PDF Printer eh? Why don't you get one that's more integrated with Ubuntu?
```
sudo apt-get install cups-pdf
``` or install package "cups-pdf" in Synaptic. Once installed, I think it'll automatically configure CUPS during installation and then you can just print from any application by choosing the Virtual_Printer. I use that and I think it's pretty cool. It works flawlessly for me.

YEs, I have just installed cups-pdf it si great and exactly what I needed; does what PRIMOpdf does in XP; except for securing the documents. [Here]("http://doc.gwos.org/index.php/Print_to_PDF_with_CUPS") is a detailed instructions on how to install and set up the virtual pdf printer cups-pdf

---

### Post by carusoswi on 2007-05-11
> **shuttleworthwannabe said:**
> except for securing the documents.

What do you mean, "except for securing the documents"?

Caruso

PS: and, thank for the tips, by the way.  I am not dead set on any particular ap, picked Convert2PDF from a list I found when I searched the forum for PDF Printers.  I'll try CUPS.  Sounds like it will do the job.

---

### Post by hyperair on 2007-05-11
I suppose he means password protection of PDF files? I don't know, I haven't seen a password protected PDF file, but since MS Office and Open Office documents have that feature I suppose PDF documents should as well.

---

### Post by carusoswi on 2007-05-12
> **shuttleworthwannabe said:**
> YEs, I have just installed cups-pdf it si great and exactly what I needed; does what PRIMOpdf does in XP; except for securing the documents. [Here]("http://doc.gwos.org/index.php/Print_to_PDF_with_CUPS") is a detailed instructions on how to install and set up the virtual pdf printer cups-pdf

The link did not open for me.  I have downloaded/installed Cups-PDF.  I can get it to print to file (PS document), but, do not see how to configure it to print as PDF or convert to PDF.

I know you provided a how-to link, but, as I mentioned, it will not open for me.  My browser stalls.

Thanks for any advice.

Caruso

---

### Post by useResa on 2007-05-12
> **carusoswi said:**
> The link did not open for me.
The link won't open anymore for me also.
AFAIK the identical text is indicated on [this page]("http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/") (which does open for me).

Additionally also information can be found on [this Wiki page]("https://help.ubuntu.com/community/PDFPrinting").

Hope that will help you get it up and running.

---

### Post by carusoswi on 2007-05-12
> **useResa said:**
> The link won't open anymore for me also.
AFAIK the identical text is indicated on [this page]("http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/") (which does open for me).

Additionally also information can be found on [this Wiki page]("https://help.ubuntu.com/community/PDFPrinting").

Hope that will help you get it up and running.

Well, it looked promising, except that, when I went to add the printer, there was no generic option.  I must have done something wrong.  Left a message an my email on that blog.  Thanks for pointing me in a positive direction.
Caruso

---

### Post by mak123 on 2007-08-11
> **useResa said:**
> The link won't open anymore for me also.
AFAIK the identical text is indicated on [this page]("http://ubuntu.wordpress.com/2006/03/23/print-to-pdf-using-cups-pdf/") (which does open for me).

Additionally also information can be found on [this Wiki page]("https://help.ubuntu.com/community/PDFPrinting").

Hope that will help you get it up and running.

I followed what it said in the Wiki page, but I have a few issues:
1) There's no PDF folder in my Home folder
2) When I print using the newly created printer, I get a .ps file.  When I double click that file, I get a largely blank white page, except for the info I typed in, and a few empty check boxes.

HELP ME!!!  THANKS!

---

### Post by kyrhash on 2007-08-11
check this link out:

[http://www.arsgeek.com/?p=1720]("http://www.arsgeek.com/?p=1720")

is that what you want?

---

### Post by mak123 on 2007-08-11
YES!!!

I think I figured it out.

At first, after choosing my pdf printer, I was selecting the "Print to file" option, which gave me a .ps file that when I opened looked like crap.

This time, I just selected my pdf printer and let it print.

A PDF folder popped up in my Home folder, and the file opened up like a regular pdf file.

---

### Post by JEBB on 2007-08-23
I want to be able to print some files to PDF files much as I can do with my Mac and Windows machines.  

I tried to install CUPS-PDF via Synaptic and according to Synaptic I was successful.  I can not otherwise find it to use it for printing.  I expected it to show up in my System>Administration>Printers list but it isn't there.  Now what do I do?  Thanks.

---

### Post by asmoore82 on 2007-08-23
> **carusoswi said:**
> I downloaded this tarball (where did that interesting designation for a compressed package come from??)
...

The standard print dialog has a "print to file" option that will allow you to create a PostScript (*.ps) file.

then there is a well-supported extremely common tool called 'ps2pdf' that can turn this into a pdf.

-------------------------
"tarballs" are created and extracted on the command line with the program **tar**.
tar, by default does not do compression of archives so if you use it straight up you will
actually be wasting space.

Why would one specifically need to roll multiple files into one in this way?
for backup systems that can hold a glob of data but not a true filesystem: tape drives!

tar orginally stood for "tape archiver." :KS

---

