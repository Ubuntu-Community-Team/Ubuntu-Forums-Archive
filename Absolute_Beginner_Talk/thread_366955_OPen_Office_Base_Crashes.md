---
title: "OPen Office Base Crashes"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by bobaj on 2007-02-21
HI:

Has anyone gotten Open Office Base to work on Lunux Ubuntu?  I found the thread to uninstall 2.0 and install 2.1.  I did that and things didn't improve.

Any suggestions?

Or does anyone know of a Linux replacement to MS Access/Open Office Base that may work better in Ubuntu?

Thanks
Bobj

---

### Post by macogw on 2007-02-21
Can you use alien to convert the OOo rpm's into debs?  OOo has been known to be buggy on Ubuntu because the debs come from Debian and something's wrong with them.  I heard it has something to do with Java and whoever built those .deb files

---

### Post by bobaj on 2007-02-21
HI:

Thanks for the information.  I did use Alien to convert the rpm's to deb's.  It doesn't seem to make any difference to Open Office Base.

Thanks
Bobj

---

### Post by keithpeter on 2007-02-21
Hello

I'm not a big desktop database user, but I have just cranked up Base 2.1 and it seems to open OK and let me create tables and add some data.

I'm using Xubuntu 6.06.1 (Dapper), converting the OpenOffice.Org 2.1 RPMs to debs using alien, and installing using dpkg. No error messages, no crashes.

Cheers

---

### Post by The Mekon on 2007-02-21
I had problems with OO Base until I installed the correct Java environment.

This is quoted from a neet website:
"If Base just won't start, or is being very weird, check your Java RTE as follows:

Start an Open Office text document. (Yes... text document!)
Click on the menu entry Tools
Click on the sub menu entry Options
If the "OpenOffice.org" heading has a + ion front of it, click
     on the + to make it a -, and display the tree of sub-options
Click on "Java", and hold your breath! Don't be alarmed if no JAVA RTEs show
After a moment or two, you should see one or more RTEs.
Select the one with a version id starting 1.5... or higher.
Close everything.
Try Base again!"

By the way it's link is:

[http://sheepdogguides.com/fdb/fdb1main.htm]("http://sheepdogguides.com/fdb/fdb1main.htm")

Brian

---

### Post by bobaj on 2007-02-21
Thanks for the information.

Selecting the Java helps.  But the program is still unstable.  Many errors in creating tables and inserting data.

Appreciatively,
Bob

---

