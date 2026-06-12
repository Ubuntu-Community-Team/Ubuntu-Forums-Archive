---
title: "[SOLVED] Synaptic Package Manager unhappy"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by nuddernuby on 2007-08-07
On Edgy (6.10), just installed, when opening the Synaptic Package Manager I get the following:
QUOTE
E: The package z600cups needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory
UNQUOTE

All panels are blank and reloading does not help.
The z600cups refers to an unsuccessful attempt to install a printer driver for Lexmark.

I'm lost.   Anybody out there with the patience to advise?

Thanks in advance.

---

### Post by 505 on 2007-08-07
Open a terminal (press Alt+F2 and type 'gnome-terminal). Then type
```
sudo aptitude remove z600cups
```
It will now be removed. You should then be able to open Synaptic, or even try to reinstall the printer driver again.

---

### Post by nuddernuby on 2007-08-07
Thank you for your quick response.

[COLOR="Red"]sudo aptitude remove z600cups [/COLOR] could not remove the problem - it was in a bad state -  message recommended that z600cups be re-installed before removal.
SPM still gives this message:
QUOTE
E: The package z600cups needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
UNQUOTE

I tried reinstalling and got the following: (Please note BOLD text)

> p2@p2-desktop:~/lexmark$ sudo dpkg -i z600cups_1.0-2_i386.deb
Selecting previously deselected package z600cups.
(Reading database ... 88794 files and directories currently installed.)
Preparing to replace z600cups 1.0-2 (using z600cups_1.0-2_i386.deb) ...
Unpacking replacement z600cups ...
/var/lib/dpkg/info/z600cups.postrm: 2:** /etc/init.d/cups: not found**
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 2:** /etc/init.d/cups: not found**
dpkg: error processing z600cups_1.0-2_i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 2: **/etc/init.d/cups: not found**
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 z600cups_1.0-2_i386.deb

There is no **/etc/init.d/cups**, (only **/etc/init.d/cupsys**). This is clearly a problem.

Could you please advise?
Thank you once again

---

### Post by dougfractal on 2007-08-07
sudo touch /etc/init.d/cups # create an empty file

---

### Post by nuddernuby on 2007-08-07
Thank you 505 and Dougfractal!

SPM up and running again. Great to have you guys out there.

I don't have the printer working yet, but we'll leave that for another round.
Regards

---

### Post by Harcat on 2007-08-07
Hello. I have the exact same problem and same error messages only with a Brother MFC-8440 printer driver.
message in packet manager reads: E: The package mfc8440lpr needs to be reinstalled but I can't find the archive for it.
E: Internal Error opening cache  1) Please report


I tried the sudo formula recommended and thought I had it licked but alas,no.
Once I remove this sticky bugger, I need to replace the printer driver and hopefully get it to print!

Thanks in advance to anyone with tips on how to accomplish this.

Amico

---

### Post by dougfractal on 2007-08-08
Hi Harcat

Can you start this on a new thread as this one has **solved** at the top. And I find it very confusing.
When you start a new post can you quote all the error message, as the answer is in the detail.  Also put a link to the post in this thread.

---

