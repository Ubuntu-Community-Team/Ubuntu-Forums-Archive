---
title: "Print to PDF - Ubuntu 6.06"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by moshuptrail on 2006-07-29
How do you print to a PDF file from Firefox (or any other non-PDF enabled program) 

I was trying to follow the instructions found in an earlier thread for setting up a cups-pdf printer, but they don't seem to work any more.  Can someone shed some light on this?

I am getting the following error when installing cups-pdf:
$ sudo apt-get install cups-pdf
Reading package lists... Done
Building dependency tree... Done
Package cups-pdf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cups-pdf has no installation candidate

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by 5-HT on 2006-07-29
cups-pdf would be the easiest way to go.

It is available in Dapper's repos.  There may be something amiss with you sources.list. I'd suggest commenting out everything but the official Ubuntu repos, updating the package list, and trying again. Furthermore, some of the ubuntu mirrors have been having problems lately; is your sources.list using the main servers (i.e., [U][http://archive.ubuntu.com...)?]("http://archive.ubuntu.com...%29?")
[/U] 
Alternatively, you could wander over to packages.ubuntu.com,  download the cups-pdf .deb, and install using: ```
 sudo dpkg -i /path/to/the/cups-pdf-deb 
``` The dependencies should already be installed if you have a default Ubuntu setup.

Another option would be to forgo the cups-pdf route and to simply use the 'print to a file' option in apps to generate a postscript file. 
You could then convert the postscript to a .pdf using [I]ps2pdf.

[/I] HTH

---

### Post by moshuptrail on 2006-07-29
I ended up wandering and locating the package by hand.

When I installed it, I got the following message:

$ sudo dpkg -i cups-pdf_2.2.0-1_i386.deb
Selecting previously deselected package cups-pdf.
(Reading database ... 78328 files and directories currently installed.)
Unpacking cups-pdf (from cups-pdf_2.2.0-1_i386.deb) ...
Setting up cups-pdf (2.2.0-1) ...
 * Restarting Common Unix Printing System: cupsd

"previously deselected"????

Can you explain what is going on?  Did I do something?

TIA

---

### Post by 5-HT on 2006-07-29
> **moshuptrail said:**
> I ended up wandering and locating the package by hand.

When I installed it, I got the following message:

$ sudo dpkg -i cups-pdf_2.2.0-1_i386.deb
Selecting previously deselected package cups-pdf.
(Reading database ... 78328 files and directories currently installed.)
Unpacking cups-pdf (from cups-pdf_2.2.0-1_i386.deb) ...
Setting up cups-pdf (2.2.0-1) ...
 * Restarting Common Unix Printing System: cupsd

"previously deselected"????

Can you explain what is going on?  Did I do something?

TIA

The 'previously deselected' message is perfectly normal as you are installing a package that was not previously selected for installation.

See [HOWTO: Install Cups-PDF]("http://ubuntuforums.org/showthread.php?t=188860") for a walkthrough on how to configure the PDF printer.

HTH

---

