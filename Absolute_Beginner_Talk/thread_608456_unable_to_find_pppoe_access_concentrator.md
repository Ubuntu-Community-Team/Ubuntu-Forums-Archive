---
title: "unable to find pppoe access concentrator"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by westcoasteagles on 2007-11-10
Originally loaded 7.10 on a dedicated drive by itself with no problem - was able to connect to the internet.

Got brave and decided to create a dual boot drive for the same machine. Installed XP first then installed 7.10. Can connect to the internet without any problem in XP BUT can't in 7.10 despite it having worked on the same machine on a dedicated drive.

I noticed that the network icon in the top right corner of the screen has an exclamation mark icon on it.

When I do the "sudo ifconfig" it sees eth0 - but the output doesn't show any stats (or I should say - all stats are 0).

When I do the sudo pppoeconf it timesout and says sorry, check the cable, bla bla bla...

Anyone know why the dual boot system would corrupt this?

cheers
:confused:

---

### Post by racedo on 2007-11-10
I have the same problem. Sudenly my internet connection stop working and when I run pppoeconf says the same.

---

### Post by westcoasteagles on 2007-11-11
as a follow up, I reinstalled 7.10 and the problem persists.

:confused:

---

### Post by westcoasteagles on 2007-11-12
This thread solved my problem

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

