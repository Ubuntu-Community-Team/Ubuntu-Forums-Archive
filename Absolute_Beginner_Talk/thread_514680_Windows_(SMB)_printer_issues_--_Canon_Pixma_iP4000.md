---
title: "Windows (SMB) printer issues -- Canon Pixma iP4000"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by duncancan on 2007-08-01
Hi Everybody,

This is my last teething problem with Ubuntu, as far as i can tell, so thanks firstly to all those who've helped me get up and running.

Anyway, there's a printer on our study computer (hostname: STUDY, printer name: printer), a Canon iP4000. I'm trying to set it up so i can print things through it from this computer. I've added it as a Windows (SMB) connected printer, and selected the correct driver (Canon iP4000, and i've selected the "High Quality Image (Gutenprint CUPS) (simple)" option.

As far as i can see, there's no problem with the network connection itself, but but no matter what i try to print, or what paper source i select in the printer properties (cassette, auto sheet feeder, etc etc) the windows computer to which the printer is connected comes up with an error on its screen saying:

"a paper size that cannot be fed from the cassette was selected".

linux seems oblivious to the fact that the printing hasn't worked.

the cassette is the paper source from windows, too, and it works just fine when printing from windows.

does anybody have any ideas?

thanks,
-duncan

---

### Post by splintercellguy on 2007-08-01
Um...isn't there a switch on the printer that lets you select which paper source? Throwing something out there.

EDIT: Random comment, but the printing client on Windows/Linux tends to be oblivious to problems on the printer :P.

---

### Post by duncancan on 2007-08-01
yeh, the switch on the printer is pointing to the correct paper source. and as i said, it works from windows.

---

### Post by Inquisitive Alex on 2007-08-30
I have a similar problem with double-sided printing (duplex). I can print documents on single side of paper, but setting duplex option causes error message on Windows computer...
I used Turboprint drivers before and had no problems.

---

### Post by eyoungut on 2007-09-10
I have exactly the same problem. (I 've tried two different printers (a pixma 4000 and an MP780 on two different Windows PC's - exact same results)

Did you find the fix? 
Thanks!

---

### Post by David Mulligan on 2007-09-26
I have to guess that the built in repository for this driver is broken. Has anyone tried to install the driver from the manufacturer? Has anyone tried this with Edgy?

---

### Post by Inquisitive Alex on 2007-09-27
[https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/135311](https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/135311)
Links to the new packages (for Gusty) can be found here.

---

### Post by eyoungut on 2007-10-23
I tried the install per below, but it failed

A possible fix was posted upstream, please test the following packages which have the patch applied:
[http://www.linux-foundation.org/~till/tmp/ubuntu/gutsy/gutenprint/](http://www.linux-foundation.org/~till/tmp/ubuntu/gutsy/gutenprint/)
Download all packages in the binary/ subdirectory and install them with "sudo dpkg -i *.deb".

---

### Post by David Mulligan on 2007-10-23
I cleanly installed Gutsy Gibbon and voila!  Printer problems are gone.

---

