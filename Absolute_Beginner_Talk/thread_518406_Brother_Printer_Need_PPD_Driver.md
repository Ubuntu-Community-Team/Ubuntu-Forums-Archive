---
title: "Brother Printer: Need PPD Driver"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by comjo on 2007-08-05
Brother supplies a Debian Linux driver for my MFC-3360C printer, and I install the package and follow all of their instructions.  When I am done and I go to add a printer, Ubuntu recognizes the printer, but on the next screen (driver screen) there is no mfc-3360 on the list, and there is no PPD driver even listed in the files of the package.  

My question is where can I find a PPD file for my brother printer and is there a generic PPD file that may work?

This is my last big hurdle to switch all the way over.... this printer is detected and installs itself in windows.. (grrrr)...

But loving Ubuntu so far other than that!

Brandon

---

### Post by splintercellguy on 2007-08-05
Have you tried using the GNOME CUPS printer frontend to install? System -> Administration -> Printers I think.

---

### Post by comjo on 2007-08-05
Yes, that's the only way I know to install a printer.  That is the program I was using that says I need a PPD file which is the driver, but I cannot find a PPD driver anywhere.

---

### Post by freebeer on 2007-08-05
I found a driver for my printer - an MFC-3420C - on Brother's site.  (It's been a while since I set it up, so my memory of the event has faded.)  In your driver list, do you see the MFC-3420C?  You might try that one - my guess is that it'll work, assuming that your printer model isn't all that different.

---

### Post by comjo on 2007-08-05
No that one is not listed.. I've tried every MFC driver that is listed in the Printer Setup program and still cannot get my printer to even make a noise :(  I appreciate your help though!

Brandon

---

### Post by comjo on 2007-08-05
Never mind... I added my old HP 5400 series printer and it was recognized, installed and working immediately.  I guess some things just work and other do not.

Seriously though, hardware problems was what turned me off from linux 10 years, a decade later I try again and expect these things would be ironed out...

Brandon

---

### Post by freebeer on 2007-08-06
Oh.. I dunno about that... seems that there is a Linux driver for your model.  I found it here: [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc3360clpr-1.0.0-9.i386.deb&lang=English_lpr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc3360clpr-1.0.0-9.i386.deb&lang=English_lpr")

---

