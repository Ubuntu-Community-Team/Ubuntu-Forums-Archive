---
title: "Printer Sharing With Cups, Help!"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Quickdood on 2007-03-08
Hello,

I have been trying to get my printer which is connected to my ubuntu 6.10 machine to work over my network with my Windows Xp laptop.  I have tried to use both samba and cups but I have had no success.  I was wondering if anyone has a working Cups config file that they can post here which I can edit to my needs.  Also if there are steps beyond just the config file I would appreciate if someone could post that too.  Thank You!

---

### Post by schwascore on 2007-03-08
Click on System --> Administration --> Printing on your host system (the one the printer is attached to).  Click on the "Global Settings" menu and click on "Share Printers."  This will give you a warning to let you know that the action will open up port 631 - click "ok."

On your XP system, go to the Control Panel ---> Printers.  Click on add a printer and then select "add a network printer."  You will use the bottom option to define the printer - the fully qualified URL.  You should type in something like this:

[http://IPADDRESSOFYOURHOST:631/printers/NAMEOFYOURPRINTER](http://IPADDRESSOFYOURHOST:631/printers/NAMEOFYOURPRINTER)

Then click next and select the model and driver for your printer.

Good luck, let us know if there are any more problems.

---

### Post by Quickdood on 2007-03-08
the share printer optioned is greyed out and it cant be checked.  This may be because I already messed up my cups config file.  Can someone please post a working one.  Thanks!

---

### Post by OMRebel on 2007-03-08
I am attempted to do the exact same thing as you are, and mine is grayed out as well. :(

---

### Post by Quickdood on 2007-03-09
hopefully someone can help us!

---

### Post by shaft350x on 2007-03-09
Hey I got a mixed network (printer to Ubuntu box shared with WinXP Sp2 Laptop)

It ain't exactly a how-to, but here is a link to the thread.

[http://www.ubuntuforums.org/showthread.php?t=311518](http://www.ubuntuforums.org/showthread.php?t=311518)

I got it to work, and I didn't end up using a modified cupsd.conf file.  I ended up with the greyed out uncheckable "share printer" option, so I went back to the regular file.

My problems were mostly with the Windows Laptop.  So check all your workgroup and sharing settings on those.

I'm no network expert, so I hope that this can help.  If not well, then maybe keep bumping this thread.

---

### Post by Quickdood on 2007-03-09
How can I restore my original cups file?  I forgot to back it up before I edited it.

---

