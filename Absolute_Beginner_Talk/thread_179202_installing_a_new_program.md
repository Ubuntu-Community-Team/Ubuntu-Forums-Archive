---
title: "installing a new program?"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by gpw1 on 2006-05-19
This is the program, I have downloaded it as a Tarball, when I extracted it there is a folder called "installation", opening that folder there are a series of files with the first one called "autostart" (see there instructions below) How do I complete this installation?

The web site is: [http://www.amyuni.com/en/support/downloads.html#linux](http://www.amyuni.com/en/support/downloads.html#linux)

PDF Converter for Linux

The PDF Converter or Printer Driver allows you to create a PDF document from any application running under Linux operating systems. It can be installed on your system like any standard printer.

An automatic installation software is provided for an even easier installation. Instead of printing to your standard printer, you will just select our printer.


  	>>> Click here to start downloading the PDF Converter for Linux

---

### Post by xXx 0wn3d xXx on 2006-05-19
[QUOTE=gpw1]This is the program, I have downloaded it as a Tarball, when I extracted it there is a folder called "installation", opening that folder there are a series of files with the first one called "autostart" (see there instructions below) How do I complete this installation?

The web site is: [http://www.amyuni.com/en/support/downloads.html#linux](http://www.amyuni.com/en/support/downloads.html#linux)

PDF Converter for Linux

The PDF Converter or Printer Driver allows you to create a PDF document from any application running under Linux operating systems. It can be installed on your system like any standard printer.

An automatic installation software is provided for an even easier installation. Instead of printing to your standard printer, you will just select our printer.


  	>>> Click here to start downloading the PDF Converter for Linux[/QUOTE]
Read [ this guide on installing software. ](http://www.psychocats.net/ubuntu/installingsoftware.php) From what you stated, read section 4. Install from source.

---

### Post by mjm115 on 2006-05-19
This can be done natively in OpenOffice, KOffice (thru export filters), and many other applications in linux.

You can also try [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by Sef on 2006-05-19
Here's another site:

[http://monkeyblog.org/ubuntu/installing.html]("http://monkeyblog.org/ubuntu/installing.html")

---

### Post by mostwanted on 2006-05-19
To run a executable file, simply type in the path to the file into a terminal (or double-click if it's a graphical installer... which it rarely is though).

You might have to change permissions so that it becomes executable, here is a short video I've made showing you how to do that:

[http://monkeyblog.org/ubuntu/videos/Changing_permissions.gif](http://monkeyblog.org/ubuntu/videos/Changing_permissions.gif)

It's also described in detail here:

[http://monkeyblog.org/ubuntu/installing.html#installer](http://monkeyblog.org/ubuntu/installing.html#installer)

---

### Post by mostwanted on 2006-05-19
[QUOTE=MasterChief1234]Read [ this guide on installing software. ](http://www.psychocats.net/ubuntu/installingsoftware.php) From what you stated, read section 4. Install from source.[/QUOTE]

It doesn't look like he's installing from source, so that wouldn't be the way to go.

**To the original poster:** the autostart file is probably a binary executable, you need to run it (see my previous post). If there is a file called "Makefile" in the installer folder, disregard what I said and go with his suggestion.

---

### Post by gpw1 on 2006-05-19
[QUOTE=mostwanted]It doesn't look like he's installing from source, so that wouldn't be the way to go.

**To the original poster:** the autostart file is probably a binary executable, you need to run it (see my previous post). If there is a file called "Makefile" in the installer folder, disregard what I said and go with his suggestion.[/QUOTE]

Yes the "autostart" is a bin file (no "makefile"), BUT it already had permissions set per you cool video. You were right I did try almost everything that was discribed on these threads. I sent an e-mail to the software company I got this program from to see what they say.
There are 12 bin files all set like you suggested. There is an install.sh and uninstall.sh both scripts. Can I run the install.sh scrip? That was suggested in the above threads. I just kept going back to the program directions to run the "autostart". Is it possible this program is not valid with Dapper Drake? I had a simular issue with the Gnome NetworkManager, loaded in just fine with Synaptic but would not show up in "applications" tool bar, I tried everything I could think of till I just gave up (I ended up useing a KDE version that works just fine). Even with all the faults WinXP has, installing programs was real slick. Maybe someone needs to put there foot down and force a compatability issue with installing all Linux programs. Sure would make it easier for us newbes, I want to learn, I do, but I need a working PC with MY programs to do that... Chicken and Egg situation...
Will see what I get out of the company who created this program.

Thanks for your help
george

---

### Post by mostwanted on 2006-05-19
[QUOTE=gpw1]Yes the "autostart" is a bin file (no "makefile"), BUT it already had permissions set per you cool video. You were right I did try almost everything that was discribed on these threads. I sent an e-mail to the software company I got this program from to see what they say.
There are 12 bin files all set like you suggested. There is an install.sh and uninstall.sh both scripts. Can I run the install.sh scrip? That was suggested in the above threads. I just kept going back to the program directions to run the "autostart". Is it possible this program is not valid with Dapper Drake? I had a simular issue with the Gnome NetworkManager, loaded in just fine with Synaptic but would not show up in "applications" tool bar, I tried everything I could think of till I just gave up (I ended up useing a KDE version that works just fine). Even with all the faults WinXP has, installing programs was real slick. Maybe someone needs to put there foot down and force a compatability issue with installing all Linux programs. Sure would make it easier for us newbes, I want to learn, I do, but I need a working PC with MY programs to do that... Chicken and Egg situation...
Will see what I get out of the company who created this program.

Thanks for your help
george[/QUOTE]


Yes, running shell script (.sh) files is pretty simple. Just run it like you would run the binary file (or with sh, like this: [http://monkeyblog.org/ubuntu/installing/#script](http://monkeyblog.org/ubuntu/installing/#script) )

---

### Post by macdo on 2006-05-19
Even easier: create a special/pseudo printer in the main printer screen (in kubuntu, that's in the system settings). 
Then :

Name: Print to PDF (or whatever you want)
Description: Make pdf (or anything you like)
Location: local file (or something else, if you're feeling creative...)

Then tick 'use command' and select 'postscript to PDF converter' in the drop-down box.

Next, tick 'Enable Output file', and select 'application/PDF'.
And finally, in the 'filename extension' box, type "pdf" - without the quotes.

Then click OK.
Sorted! You can now print to pdf from any app that uses the main system settings, by choosing the printer 'Print to PDF' in the print dialog.

(Note that this is for Kubuntu - Ubuntu is broadly the same, with a different graphical interface.)

---

