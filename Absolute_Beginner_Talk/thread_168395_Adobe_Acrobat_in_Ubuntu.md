---
title: "Adobe Acrobat in Ubuntu?"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by Costas on 2006-04-30
Hi everybody, 

i know that you can read .pdf files in Ubuntu using the "Document Viewer" ...but what i sometimes miss from windows is Adobe Acrobat  which  allows you to change/edit your pdf files (e.g. highlight text, mark text, etc...) ...before Ubuntu i used Suse for 4-5 days and the acrobat reader they had there had no tools at all... how come such tools are not available in linux in general?  does anyone know of a program that allows you to edit pdf files? any help would be appreciated since i am using pdf all the times and it's a pain in the ....neck to have to swith to XP!

thanx

---

### Post by tonyr on 2006-04-30
The acrobat reader packages are **acroread**, **acroread-plugins** and **mozilla-acroread**.  From the command line, or **Run** menu entry
```

sudo apt-get install acroread acroread-plugins mozilla-acroread

``` I don't know if there are applications for pdf creation
(other than the Adobe commercial product).  I suspect that there may be,
but I don't know what they are.

---

### Post by muep on 2006-04-30
I don't know about editing, but many programs, OpenOffice.org for example, can save documents as pdf files, so pdf file creation is not a problem. 

Pdf files are mainly for distributing finished documents, so it may be that no one has created a program for editing them, though I believe there are also programs for editing.

---

### Post by tonyr on 2006-04-30
The public domain word processor **abiword** has a **Save As** option for **.pdf**.

---

### Post by Costas on 2006-04-30
Thanx tonyr, but still this version of acroread you suggested me has no options for editing pdf files. I can create pdf's in general...it;s just that when someone sends me one i can not make any additions, corrections, etc...also, most of the time i download pdf files from the net (part of my job) and in XP i can change them and forward them to colleagues etc....but in ubuntu (or linux etc) i can not figure out how!

---

### Post by tonyr on 2006-04-30
[QUOTE=Costas]Thanx tonyr, but still this version of acroread you suggested me has no options for editing pdf files. I can create pdf's in general...it;s just that when someone sends me one i can not make any additions, corrections, etc...also, most of the time i download pdf files from the net (part of my job) and in XP i can change them and forward them to colleagues etc....but in ubuntu (or linux etc) i can not figure out how![/QUOTE]

You must be using **Adobe Acrobat** (the full version) or one of the 
other third party editors (e.g. **Jaws**).  As far as I can see, after a brief
search, there is no similar WYSIWYG product in the Unix/Linux world.

---

### Post by jetpeach on 2006-05-04
There is a lot of discussion about this [on this Ubuntu thread]("http://www.ubuntuforums.org/showthread.php?t=94878&page=4").  I am also trying to get the full version of adobe acrobat to work using WINE, but it won't install because it complains "adobe acrobat 7 required internet explorer 5.5".  so retarded.

anyway, I signed up on the [acrobat WINE page here]("http://appdb.winehq.org/appview.php?appId=847") to be a helper maintainer for acrobat, maybe we can get it working in linux with some tweaks.  version 5 used to install, but people said it crashed when you tried to save.

oh, I emailed two of the developers for KPDF about whether they will add editing support, since obviously this would be a better solution.  one replied that he doesn't have time.

---

### Post by MartinJ on 2006-05-04
KWord can open and edit pdf files.  It's not perfect yet but if you don't have complex formatting it should work ok.

---

### Post by nursegirl on 2006-05-04
pdftk works for editing pdf files as well.

It's not as good as Acrobat, but it also doesn't cost $450.

---

### Post by megabyte405 on 2006-05-26
AbiWord has a Summer of Code participant who will be creating a plugin to import PDF's preserving style as much as possible (an existing plugin can import the text).  However, direct editing of a PDF is restricted at the moment to the actual Acrobat application and possibly a few others.

(Oh, and for the record, AbiWord is GPL, but just as free to download and use!)

Good luck!

-- Ryan, AbiWord Dev and Win32 Maintainer

---

### Post by jetpeach on 2006-07-11
Just an update on the Wine progress for Acrobat - they've been working hard over there.  I got Acrobat 7 installed (this is the FULL version we're talking about, there is a native reader already for Ubuntu), but it crashed after startup.  The new version of Wine (.9.17) makes it run as well but Scott Ritchie will hopefully in a day or two add it to the Wine repository (see [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) for install instructions  for Wine on Ubuntu, then installing Acrobat should just be clicking the setup.exe).

Then [file your bugs with acrobat here]("http://appdb.winehq.org/appview.php?iVersionId=4922") or post your test results if you're running Acrobat full with Wine.  I'm impressed with how much that wine deveopers have done in a couple months!

Of course, I'm hopeful someday for better editing support in KPDF, but for now...

---

