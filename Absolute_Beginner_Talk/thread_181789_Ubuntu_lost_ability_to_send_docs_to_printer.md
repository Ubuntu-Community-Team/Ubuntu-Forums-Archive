---
title: "Ubuntu lost ability to send docs to printer"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-05-24
No application will print a page. Not GEdit, not Adobe Reader, not OpenOffice 2.0.

Nothing appears out of order. Nothing  has been changed.

It just died!

The printer, a Brother HL-1440 has worked for 6 months w/o problem. It prints a test page w/o problem. I have plugged the USB cable directly into the computer.

Anybody know how to "ping" the printer?

---

### Post by yager on 2006-05-24
I will most likely not be able to help you but I am sure that those who can will need more information.

When you say the printer, prints a test page, is this the test page that the printer control window sends from inside Ubuntu or are you referring to the internal test page in the printer that you trigger inside the printer itself?  If it is the printer's own self test page, then you have only proven that there is nothing wrong with the printer, which is a good thing.

Do the print jobs that you send from inside Ubuntu move through the cups queue as shown from the printer's properties control window?  If the jobs are piling up in the queue, then you may have a driver issue I believe.  Check the following link for some help.

[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1440](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-1440)

If the jobs pass through the queue, but do not show up at the printer, you might have a cups problem.  I never quite figured out how I fixed my identical problem to this with my HP printer, but I followed the instructions at this link.  You will need to adjust them of course as you don't have an HP printer.

[http://www.ubuntuforums.org/showthread.php?t=169099&highlight=hplip](http://www.ubuntuforums.org/showthread.php?t=169099&highlight=hplip)

Good Luck.  All I can tell you is that printing issues in Ubuntu apparently are one of the tougher issues to resolve.  My challenges were quite daunting as I had my printer stop working 3 times until I finally followed the directions at the link I gave you.

---

### Post by Mark_in_Hollywood on 2006-05-25
SUCCESS!!


The printer prints a test page from it's internal ROM or firmware.

Ubuntu's test page printed after I "reset" the "paused" to "resume"

Go figure!!!

Thanks, Ubuntu community!!

---

