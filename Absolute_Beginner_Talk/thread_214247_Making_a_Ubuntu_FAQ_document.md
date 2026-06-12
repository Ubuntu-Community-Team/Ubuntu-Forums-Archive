---
title: "Making a Ubuntu FAQ document"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by bento on 2006-07-12
Hi everyone, I am making a how to document of many useful things in Ubuntu and Linux in general with many easy to follow pictures.

Though this document is getting pretty long I am thinking about saving different chapters in different files. I've been using .odf as main format and makes PDFs for printing and see how everything turns out.

My question is:
Is it possible to make and organise one PDF document out of many .odf files and how?

I will add the FAQ here on the forums hopefully soon, maybe this weekend, if not, after my vacation.

---

### Post by aysiu on 2006-07-12
If you have the Universe repositories enabled, you should be fine: > Package pdfjam

    * warty (text): collection of PDF document handling utilities [universe]
      1.02-1: amd64 i386 powerpc
    * hoary (text): collection of PDF document handling utilities [universe]
      1.10-1: amd64 i386 powerpc
    * breezy (text): collection of PDF document handling utilities [universe]
      1.20-1: all
    * dapper (text): collection of PDF document handling utilities [universe]
      1.20-1: all
    * edgy (text): collection of PDF document handling utilities [universe]
      1.20-2: all ```
pdfjoin(1) - Linux man page
NAME 
pdfjoin - join together multiple PDF files
SYNOPSIS 

pdfjoin [OPTION]... SRC [SRC]...

DESCRIPTION 

pdfjoin concatenates the pages of multiple Portable Document Format (PDF) files together into a single file.

pdfjoin is a front end to some of the capabilities of the pdfpages package for pdflatex. A working installation of pdflatex with the pdfpages package is required.

pdfjoin is part of the "PDFjam" package of tools, whose homepage is at http://www.warwick.ac.uk/go/pdfjam.

SETUP 

See http://www.warwick.ac.uk/go/pdfjam, or the file PDFjam-readme.html included with the PDFjam package.

USAGE 

For the available options and local/user defaults, see the output of

    pdfjoin --help

For further information and some examples see http://www.warwick.ac.uk/go/pdfjam or the file PDFjam-readme.html included with the PDFjam package.

CONFIGURATION FILES 

Configuration of pdfjoin involves specifying the location of pdflatex, the location of temporary files, specification of default page size, etc. This is done in a block of lines at the top of the pdfjoin shell script itself; settings made there are over-ridden by any that are found at a site-wide configuration file (at /etc/pdfnup.conf, /usr/share/etc/pdfnup.conf, /usr/local/share/pdfnup.conf, or /usr/local/etc/pdfnup.conf), which in turn are over-ridden by any that are found in a user-defaults file at ~/.pdfnup.conf.

LIMITATIONS AND BUGS 

pdfjoin does not work with encrypted PDF files, and does not preserve hyperlinks.

Please report bugs! See the website at http://www.warwick.ac.uk/go/pdfjam.

LICENSE 

PDFjam is distributed under the GNU public license. See the file COPYING for details.

AUTHOR 

pdfjoin is written and maintained by David Firth as part of the PDFjam package.
```

---

### Post by az on 2006-07-12
> **bento said:**
> Hi everyone, I am making a how to document of many useful things in Ubuntu and Linux in general with many easy to follow pictures.

...

I will add the FAQ here on the forums hopefully soon, maybe this weekend, if not, after my vacation.

Anything you can add to this?:
[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)

or this?:
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by aysiu on 2006-07-12
> **azz said:**
> Anything you can add to this?:
[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)

or this?:
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
Probably.

I can think of two things already--not having to click three links deep to get to MP3 playback and other restricted formats, and including screenshots, which is what the OP mentioned in the first post.

---

### Post by az on 2006-07-12
> **aysiu said:**
> Probably.

I can think of two things already--not having to click three links deep to get to MP3 playback and other restricted formats, .

You can't have what is important to everybody on the front page, can you?  And if you write a simple howto, how many clicks does it take to find that particular howto?

> **aysiu said:**
> 
and including screenshots, which is what the OP mentioned in the first post.

You can include screenshots on the wiki.  Its done all the time:

Example:
[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

[https://help.ubuntu.com/community/HelpOnActions/AttachFile](https://help.ubuntu.com/community/HelpOnActions/AttachFile)

---

### Post by aysiu on 2006-07-12
> **azz said:**
> You can't have what is important to everybody on the front page, can you? Actually, you can, which is what I love about the Ubuntu Guide. > And if you write a simple howto, how many clicks does it take to find that particular howto? Well, apparently, it took three clicks, and that's because I knew what I was doing.

---

### Post by bento on 2006-08-15
bah, all my files exeeds the limits for this forum.

it is documents in both .odt and .pdf, and each chapter gives new users insight and easy explenation with pictures on how things are done.

Though I think I need some help, I would love to have this done by the next relesase so I can print magazines i can give with CDs.

So far:
Chapter 1: Welcome to Ubuntu
Chapter 2: What is a live CD?
Chapter 3: How to install Ubuntu
Chapter 4: Your newly installed Ubuntu
Chapter 5: Installing additional software
Chapter 6: Costomizing

---

