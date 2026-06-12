---
title: "Can't Find Openoffice.org Calc"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by leetcharmer on 2007-07-15
When I installed Ubuntu 7.04, I never found Openoffice.org Spreadsheet (Calc) in the office menu.  When I try to open an xls file, a menu pops up to search for software that can open it and Openoffice.org Spreadsheet shows up in the list already checked.  As if it's already installed.  I went to terminal and types ooffice -calc, but it opened writer.  I tried opening the .xls in writer and it had an input/output error when trying to open the files.  Anyone know how I can find/get/install calc?  I thought it was supposed to come w/ Ubuntu.  This particular install has been a little funky as well.  Segmentation fault (core dump) happens whenver I try to install a program via Add/Remove or synaptic.  Any ideas?

---

### Post by p_quarles on 2007-07-15
That's awful. If this happened to me, I'd have probably already thrown my computer out the window.

Anyway, I've installed 7.04 five times now (two of those on one machine), and have not encountered this problem. The first thing I'd try is reinstalling OpenOffice. Second, I would make sure the Feisty installation disk was good. It sounds like you did a fresh install -- rather than upgrading -- so I'm guessing you already have everything backed up and could go for another round.

---

### Post by Hagar Delest on 2007-07-16
Check in Synaptic if all the main packages have been installed (Calc, Impress, ...). This is not the first time I see this issue, some packages lacking at installation.

---

### Post by leetcharmer on 2007-07-17
That worked, reinstalling from synaptic, but I still have a segmentation fault at the beginning of all application installations. :/  I don't know how to get rid of it.  I checked the original install CD for errors and that checked out, but it sure was a pain to install.  It kept freezing during drive formatting, but finally got passed it.

---

### Post by Hagar Delest on 2007-07-17
Basically, I don'ttrust the Ubuntu version of OOo (severely bugged). Try this : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

---

