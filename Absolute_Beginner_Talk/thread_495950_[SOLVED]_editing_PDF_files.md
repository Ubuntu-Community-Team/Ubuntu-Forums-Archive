---
title: "[SOLVED] editing PDF files"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by nbv4 on 2007-07-08
Theres this form I have to fill out. The form is here: [http://forms.faa.gov/forms/faa8710-1a.pdf](http://forms.faa.gov/forms/faa8710-1a.pdf)

In windows, you just click on the link, a window pops up with the pdf in it, and then there are text boxes right where you need to enter the information.

I need to be able to fill out the boxes, then put it on a floppy (or upload it to my webspace), then print it out on a windows computer.

I tried opening it in OO.o, but all that came up was gibberish. The default PDF viewer that comes with ubuntu doesn't support the text boxes. I'd try the Adobe Acrobat Reader, but I know at least in windows, theres was no way to save the content of the edited form (I think they make you pay for the full version of acrobat before they'll let you save modified PDF's)

---

### Post by qamelian on 2007-07-08
You could install the cups-pdf driver and use it to  print your completed form as a new PDF file.

---

### Post by nbv4 on 2007-07-08
> **qamelian said:**
> You could install the cups-pdf driver and use it to  print your completed form as a new PDF file.

I've read the how-to's on cups-pdf, but that won't work. The form is in PDF right now. I need to be able to actually go in and edit the PDF's, then save (with cups or not) and print somewhere else.

---

### Post by omrsafetyo on 2007-07-08
with cups-pdf, you add a new generic, postscript printer.  Then when you print, print to that printer, and it will save it as a new pdf.

What he is saying is that IF you can edit the PDF with acrobat, then you can simply use the cups-pdf to print the finish result - even if acrobat does not support that functionality.  Once it is saved as a pdf through cups-pdf, it is in standard pdf format, and you can port it to windows to print, as you desire.

---

### Post by forrestcupp on 2007-07-08
Try scribus.  It's a desktop publishing app, and you can edit pdf's with it.

```
sudo aptitude install scribus
```

---

### Post by nbv4 on 2007-07-08
> **omrsafetyo said:**
> with cups-pdf, you add a new generic, postscript printer.  Then when you print, print to that printer, and it will save it as a new pdf.

What he is saying is that IF you can edit the PDF with acrobat, then you can simply use the cups-pdf to print the finish result - even if acrobat does not support that functionality.  Once it is saved as a pdf through cups-pdf, it is in standard pdf format, and you can port it to windows to print, as you desire.

yes, I understand what cups-pdf does. But I need a program that will edit the PDF file in the first place.

So far it seems my only option is to convert the PDF to a jpg, fill out the form in gimp, then use cups to convert that into a PDF. I'd rather not do that, but I may have no choice.

I already tried scribus, but it wouldn't open the PDF file. I tried importing it as a postscript file - which worked - but there were no words. Is there some kind of special PDF plugin I need?

---

### Post by aysiu on 2007-07-08
You misundestand.

You don't need a program the edit the PDF.

What omrsafetyo says is true.

Just use Adobe Acrobat to fill out the form.

Then "print" it, but "print" to PDF instead of to an actual printer.

This will essentially save what you've filled out by making a new PDF out of your filled out form.

---

### Post by nbv4 on 2007-07-08
> **aysiu said:**
> 
Just use Adobe Acrobat to fill out the form.


which "Adobe Acrobat"? The default one that comes with Ubuntu (Evince) does not have the ability to change anything on the PDF. its just a static display. I can't even overlay a text box over where I need to add text. I even tried xpdf but I get the same results.

Earlier I mentioned the official acrobat program that will let me add text to the frame; that was for Windows. I don't even know if there is an official adobe reader for Linux. Even of there is, I'd rather use a free alternative.

---

### Post by aysiu on 2007-07-08
Evince is not Adobe Acrobat any more than Firefox is Opera.

They are two completely separate PDF reader programs.

There is an official Adobe Reader for Linux and it is cost-free.

Have you decided you'll use only open source applications? If so, it seems weird that you'd want to use Windows to print the document later.

Here are the steps to install Adobe Acrobat for Linux:

**Step 1**: Follow [these instructions to add the Medibuntu software repositories](http://medibuntu.sos-sts.com/repository.php).

**Step 2**: Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update
sudo apt-get install acroread
```

---

### Post by gpilkay on 2007-07-08
If you don't mind installing a program from a deb file (just download it and then double-click it, like an exe in Windows) there's this:

[http://www.getdeb.net/app.php?name=PDF+Editor](http://www.getdeb.net/app.php?name=PDF+Editor)

It seems to work well for me, anyway.

I should mention, like all new programs, I'd test it out on soemtning non-essential first, or at least make an unaltered backup copy fo the PDF.  You never know...

---

### Post by nbv4 on 2007-07-08
> **aysiu said:**
> 
Have you decided you'll use only open source applications? If so, it seems weird that you'd want to use Windows to print the document later.

Here are the steps to install Adobe Acrobat for Linux:

**Step 1**: Follow [these instructions to add the Medibuntu software repositories](http://medibuntu.sos-sts.com/repository.php).

**Step 2**: Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update
sudo apt-get install acroread
```

I have to print it at work (windows) since I don't own a printer.

I tried installing acroread, but that wouldn't do it either. All it would do was display the file; no editing. The windows version I know allowed you to do this...

There HAS to be a program out there that can open a PDF file, then ALLOW YOU TO ADD STUFF TO IT. At this point it seems my only option is to open the file with the acroread, display it at 50% (so it all fits on the screen), take a screenshot, open the png screenshot in gimp, add the text to it, then "print" using cups-pdf.:mad:

---

### Post by nbv4 on 2007-07-08
> **gpilkay said:**
> If you don't mind installing a program from a deb file (just download it and then double-click it, like an exe in Windows) there's this:

[http://www.getdeb.net/app.php?name=PDF+Editor](http://www.getdeb.net/app.php?name=PDF+Editor)

It seems to work well for me, anyway.

I should mention, like all new programs, I'd test it out on soemtning non-essential first, or at least make an unaltered backup copy fo the PDF.  You never know...

I installed that program, and got this:
```

Loaded file : /home/nbv4/faa8710-1a.pdf
Warning: This document is linearized PDF!
Warning: This document is encrypted!
Encryption filter: /Standard
Encrypted content will show up as garbage and many operations will be impossible

```

then a blank page showed up. This file worked fine for the other readers...

---

### Post by p_quarles on 2007-07-08
Just a minor point of clarification: I think what you're talking about is using an Adobe interactive PDF, and not actually "editing" it. 

And the problems you're encountering are due, I think, to the fact that Interactive PDF forms are just a weird, proprietary format. Even the Windows version of Acrobat Reader won't allow you to save them to a file (you can only print the filled out form). Basically, I don't think you could accomplish what you're trying to do without buying the full version of Acrobat and using Windows.

That said, I think printing the file to a document, editing it with another program and then saving it is actually a really good workaround. Not convenient, but proprietary formats usually aren't.

In any case, I would try editing with Scribus rather than GIMP, just because the former is better suited for text.

---

### Post by HermanAB on 2007-07-08
Another trick:
Using Acrobat, you can also print to a file - just go print and select a little tick box to print to a file somewhere in the print dialogue.  That file will be a Postscript file, which is an older format that can be converted to PDF using ps2pdf.

Otherwise, use Scribus.

Cheers,

Herman

---

### Post by aysiu on 2007-07-08
I'm sorry. There's an additional package you have to install in order to use interactive fields: ```
sudo apt-get install acroread-plugins
```

---

### Post by nbv4 on 2007-07-09
> **aysiu said:**
> I'm sorry. There's an additional package you have to install in order to use interactive fields: ```
sudo apt-get install acroread-plugins
```

aw yeah, thats the stuff

thanks

---

### Post by psyopper on 2007-07-09
You have to be kidding me! 

I was all over this (I troll this forum for good tips), I was so happy to see that Adobe actually did SOMETHING on Linux! Until Aptitude told me acroread + acroread-plugins + acroread-escript was 111 megs!

How can this be 111 megs? That's insane!

---

### Post by aysiu on 2007-07-09
Looking at the actual repositories, it seems that the download is quite hefty, but it should be 40 MB, not 111 MB: ```
Index of /pool/non-free/a/acroread/
Name	Last Modified	Size	Type
Parent Directory/	 	-  	Directory
acroread-escript_7.0.9-0.0.ubuntu0.7.04+medibuntu2_amd64.deb	2007-May-28 22:07:33	972.4K	application/octet-stream
acroread-escript_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb	2007-May-28 22:08:24	**973.1K**	application/octet-stream
acroread-plugins_7.0.9-0.0.ubuntu0.7.04+medibuntu2_amd64.deb	2007-May-28 22:07:34	17.1M	application/octet-stream
acroread-plugins_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb	2007-May-28 22:08:25	**17.1M**	application/octet-stream
acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2.diff.gz	2007-May-28 22:04:29	29.6K	application/x-gzip
acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2.dsc	2007-May-28 22:04:27	0.7K	text/plain
acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2_amd64.deb	2007-May-28 22:07:32	23.8M	application/octet-stream
acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb	2007-May-28 22:08:21	**21.8M**	application/octet-stream
acroread_7.0.9.orig.tar.gz	2007-May-28 22:04:29	42.1M	application/x-tgz
mozilla-acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb	2007-May-28 22:08:31	2.0M	application/octet-stream
``` **Edit**: Never mind. I just tried it. It is 111 MB, but that's after unpacking. It's "only" 41 that needs to be downloaded (which is still a lot): ```
Need to get 41.9MB of archives.
After unpacking 111MB of additional disk space will be used.
```

---

### Post by nbv4 on 2007-07-09
> **psyopper said:**
> You have to be kidding me! 

I was all over this (I troll this forum for good tips), I was so happy to see that Adobe actually did SOMETHING on Linux! Until Aptitude told me acroread + acroread-plugins + acroread-escript was 111 megs!

How can this be 111 megs? That's insane!

yeah, I installed it all, only to realize it doesn't work.

acroread without the plugins will read the PDF, but no interactive text boxes. When I print using cups-pdf, it works fine, just no added text.

Then, when I installed the plugins, the interactive text boxes work, but when I try to use cups-pdf to print, all I get is a blank page. So I guess the tradeoff is you sacrafice printing ability to get the interactive text boxes :(

---

### Post by aysiu on 2007-07-09
Worked fine for me.

For some reason, though, the file turned out huge (1.7 MB after I filled out only one field). You can see the result [here](http://www.psychocats.net/ubuntu/test.pdf).

I've attached screenshots of the process.

---

### Post by nbv4 on 2007-07-09
> **aysiu said:**
> Worked fine for me.

For some reason, though, the file turned out huge (1.7 MB after I filled out only one field). You can see the result [here](http://www.psychocats.net/ubuntu/test.pdf).

I've attached screenshots of the process.

oh, now it works. I was printing using the cups-pdf virtual printer. I didn't see that print to file option there. again, thanks for the help

---

### Post by hugmenot on 2007-07-11
This just came in: Forms support in Evince.

[https://launchpad.net/ubuntu/gutsy/+source/evince/0.9.2-0ubuntu1](https://launchpad.net/ubuntu/gutsy/+source/evince/0.9.2-0ubuntu1)

---

### Post by mak123 on 2007-08-11
> **aysiu said:**
> Looking at the actual repositories, it seems that the download is quite hefty, but it should be 40 MB, not 111 MB: ```
Index of /pool/non-free/a/acroread/
Name	Last Modified	Size	Type
Parent Directory/	 	-  	Directory
acroread-escript_7.0.9-0.0.ubuntu0.7.04+medibuntu2_amd64.deb	2007-May-28 22:07:33	972.4K	application/octet-stream
acroread-escript_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb	2007-May-28 22:08:24	**973.1K**	application/octet-stream
acroread-plugins_7.0.9-0.0.ubuntu0.7.04+medibuntu2_amd64.deb	2007-May-28 22:07:34	17.1M	application/octet-stream
acroread-plugins_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb	2007-May-28 22:08:25	**17.1M**	application/octet-stream
acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2.diff.gz	2007-May-28 22:04:29	29.6K	application/x-gzip
acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2.dsc	2007-May-28 22:04:27	0.7K	text/plain
acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2_amd64.deb	2007-May-28 22:07:32	23.8M	application/octet-stream
acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb	2007-May-28 22:08:21	**21.8M**	application/octet-stream
acroread_7.0.9.orig.tar.gz	2007-May-28 22:04:29	42.1M	application/x-tgz
mozilla-acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb	2007-May-28 22:08:31	2.0M	application/octet-stream
``` **Edit**: Never mind. I just tried it. It is 111 MB, but that's after unpacking. It's "only" 41 that needs to be downloaded (which is still a lot): ```
Need to get 41.9MB of archives.
After unpacking 111MB of additional disk space will be used.
```

How did you view the sizes of all the acroread components?

---

### Post by aysiu on 2007-08-11
> **mak123 said:**
> How did you view the sizes of all the acroread components?
Here:
[http://packages.medibuntu.org/pool/non-free/a/acroread/](http://packages.medibuntu.org/pool/non-free/a/acroread/)

---

