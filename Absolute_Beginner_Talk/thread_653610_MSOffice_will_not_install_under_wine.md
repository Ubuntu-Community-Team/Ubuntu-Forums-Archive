---
title: "MSOffice will not install under wine"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-12-30
My copy of MSOffice will not install under wine.  I had all this working when I ran Ubuntu 7.04, but, in version 7.10, the MSOffice install routine complains that my key is invalid.  What's that about?  Am I alone with this problem, or have others experienced the same.

So far, I am regretting my move to 7.10.  My wirless adapter will not work (driver and hardware are recognized, they just don't work - not detected in network manager), and most of my software is not working, either.

I may have to move back to 7.04.

Any suggestions on the cause of my subject problem would be appreciated.

Thanks.

Caruso

---

### Post by ugm6hr on 2007-12-30
Is it Office 2003?

[http://ubuntuforums.org/showthread.php?t=493494&page=2](http://ubuntuforums.org/showthread.php?t=493494&page=2)

Office 2007 doesn't work.

---

### Post by raddellee on 2007-12-30
Go to winehq or wine-wiki.org and find the program you need to put in system 32 (/home/(name)/.wine/drive_c/windows/system32)from a windows partition. To verify the key.

---

### Post by leg on 2007-12-30
Why not install open office or one of the other open source word processors. If your reason is compatability I am sure you can save in .doc format from any of them.

---

### Post by popman on 2007-12-30
:guitar: i need help with tribes

---

### Post by carusoswi on 2008-01-05
> **leg said:**
> Why not install open office or one of the other open source word processors. If your reason is compatability I am sure you can save in .doc format from any of them.

I am not so much in need of MS Word as I am MS Access and Excel.  I am not into bashing OO, but its spreadsheet and especially its relational database is simply not in the same league as the offering from MS (trust that I am not at all in love with MS).

The OO database has never worked properly for me.  I use the wizards to design my tables and forms, but I can never get the wizard to complete the process so that I can actually use my database.

MS Access incorporates excellent database design aids, a powerful set of design settings that allow me to enforce data format and integrity for others who enter data for me.  In my truncated experience with OO, most of those critical features seem to be missing.

I will try the suggesting to install sys32 and see if it helps.

Thanks to all for the replies.

Caruso

---

### Post by isaacj87 on 2008-01-05
> **carusoswi said:**
> My copy of MSOffice will not install under wine.  I had all this working when I ran Ubuntu 7.04, but, in version 7.10, the MSOffice install routine complains that my key is invalid.  What's that about?  Am I alone with this problem, or have others experienced the same.

So far, I am regretting my move to 7.10.  My wirless adapter will not work (driver and hardware are recognized, they just don't work - not detected in network manager), and most of my software is not working, either.

I may have to move back to 7.04.

Any suggestions on the cause of my subject problem would be appreciated.

Thanks.

Caruso

Hello,

Make sure your WINE version is up to date (0.9.52). I was able to install and run Office 2003 with no problems and the product activated like normal, with no workarounds!

---

### Post by theRightNee on 2008-01-05
how can you uninstall windows? i cannot seem to get it to unistall

---

### Post by carusoswi on 2008-01-06
> **ugm6hr said:**
> Is it Office 2003?

[http://ubuntuforums.org/showthread.php?t=493494&page=2](http://ubuntuforums.org/showthread.php?t=493494&page=2)

Office 2007 doesn't work.

no, it's not 2003.  Just 2000

Caruso

---

### Post by carusoswi on 2008-01-06
> **isaacj87 said:**
> Hello,

Make sure your WINE version is up to date (0.9.52). I was able to install and run Office 2003 with no problems and the product activated like normal, with no workarounds!

Mine is 0.9.46.  How do I get the update?  Would it reside in the repositories?

I wonder why I had no problems in 7.04, but have them in 7.10.

Further suggestions appreciated.

Caruso

---

### Post by pdlethbridge on 2008-01-06
wine hq has the proper update you need for 9.52
[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

---

### Post by carusoswi on 2008-01-06
went to winehq.  tried to download the latest file.  Unable to connect to server (following copy/paste terminal commands.

Any suggestions?

Thanks.

Caruso

---

### Post by pdlethbridge on 2008-01-06
Did you paste into terminal the lines given here under your version of ubuntu?
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

1st line:    [COLOR="Red"]wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -[/COLOR]

then the line in terminal for your version. for gutsy 7.10 it would be

2nd line:   [COLOR="Red"]sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list[/COLOR]

The lines that are here should be copied completely including the dash at the end of the first line. just the line of type except 1st line name and 2nd line name. If you got an error 404, maybe their server is down, try again tomorrow.

---

