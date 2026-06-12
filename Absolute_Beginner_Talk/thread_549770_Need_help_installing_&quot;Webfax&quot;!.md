---
title: "Need help installing &quot;Webfax&quot;!"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by housekid on 2007-09-13
I have Mepis 6.5 and I downloaded Webfax form KDE-APP.ORG and want to set it up.
I have used efax and CUPS, but thats it for me.

Webfax is a email to fax program. I have found one other email to fax program
and after reading how to set them up found that I don't know or understand what
they are talking about. For sure Webfax had the less to do to set it up.

If someone knows and understands what I'm to do to get Webfax working from the below README file below please tell me, there are things talked about here that I've never heard of.

Starting with #Installation below: Put the "webfax" script into a location
accessible in your PATH. But, after looking up "Path" I think it's telling me to put
the "webfax" script into my /home/user/webfax, right? Please, help with the rest!

The README FILE:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# Webfax
# version: Linux-Magazine UK 
# date  : 16. September 2004
# GNU GENERAL PUBLIC LICENSE (GPL)
# bela bargel (brainguardian-kde[at]yahoo.de)

# In short:
Using kprinter and this virtual printer will convert a printjob on the fly to a multipage TIFF (G3) file using ghostscript.

This TIFF-file will be automatically attached to a kmail-message including the receivers fax-number.

The "real" faxnumber is generally part of the email-address sent to your Internet2Fax-gateway.
This is done by a small kdialog.

#Installation:
Put the "webfax" script into a location accessible in your PATH.

Put the 2 other files (.desktop and .xml) into $KDEDIR/share/apps/kdeprint/filters/.

Then create a pseudo-printer that use the command "Send to fax (web service)"
(check the "Use command" box and select it from the command list).

When printing to such a printer, you can go to the printer properties
dialog (Driver Settings tab) to tune some settings, like the fax number.
the fax server, the resolution and the mail confirmation (not used yet).

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  List of all the files in the package:
  gpl.txt                  text file
  readme.txt            text file
  webfax                 shell script
  webfax.desktop   desktop config file
  webfax.xml          xml document
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Go here for three screenshots showing using and configing Webfax:
[http://www.kde-apps.org/content/preview.php?preview=1&id=15341&file1=15341-1.png&file2=15341-2.png&file3=15341-3.png&name=Webfax](http://www.kde-apps.org/content/preview.php?preview=1&id=15341&file1=15341-1.png&file2=15341-2.png&file3=15341-3.png&name=Webfax)

---

