---
title: "Can't make mtink work"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by MickS on 2007-02-17
I want to clean my printer head so I installed mtink through synaptic but when I switch my printer on and do sudo mtink all that happens is a panel pops up that says "Port choice" /dev/usblp0 with a button on the bottom saying next, when I click on next nothing happens. I'm using Dapper and an Epson Colour stylus 880, other than this problem the printer works fine.
TIA

Mick

---

### Post by 67GTA on 2007-02-17
You should try gutenprint. It supports Epson printers, and has command line options to align-clean printer heads.

MANUAL:
[http://gutenprint.sourceforge.net/gutenprint-users-manual.pdf](http://gutenprint.sourceforge.net/gutenprint-users-manual.pdf)

FIND YOUR DOWNLOAD VERSION:
[http://gutenprint.sourceforge.net/p_Download.php3](http://gutenprint.sourceforge.net/p_Download.php3)

---

### Post by kiwigander on 2007-02-22
Mick, that was my initial experience with mtink on this machine, but it began to work properly the third time I opened it (as root of course).  In the "Port choice" window, highlight the correct port (I assume your printer is at /dev/usblp0 ?), click next and wait (as in several minutes) until the arrow cursor returns.  If you get an error message, or all the ink levels appear to be zero, close the mtink window and try again.  (I'm running Dapper on an amd64 system with a Stylus Photo R210.)

---

### Post by MickS on 2007-02-22
Yep that got it going thanks, I am almost embarrassed to admit I never realised I had to highlight the entry before clicking on next, done that and it worked and like you said it took ages first time for it to connect but after that it's straight away. Had it not been your message warning of the time I would have assumed it had failed.
I am now a happy bunnie I have checked the head, cleaned it and can now go and print some photos.

Mick

---

