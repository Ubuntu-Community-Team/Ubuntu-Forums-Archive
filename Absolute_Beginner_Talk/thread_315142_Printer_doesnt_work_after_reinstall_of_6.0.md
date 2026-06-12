---
title: "Printer doesnt work after reinstall of 6.0"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by geekygreen on 2006-12-08
This one is driving me a little crazy..
I have been working with Ubuntu for about a week. Just long enough to screw up the first install and start over.  Before the reinstall (which was related to a network problem) I had installed my Konica Minolta Page Pro 1350W and it was working fine.  I even shared it over the network sucessfully.

While dealing with other issues on the network, I thought I had hosed up the set up somehow, and so I reinstalled Ubuntu using the DVD (Ubuntu Live) the same way I did the first time...but now, even though the system recognizes the printer, and claims to be printing to it, it just sits there.  The system knows when the USB cable is unplugged and the printer is not responding, but nothing gets printed.  The first job in the que always says "Printing", but nothing happens.

This is especially frustrating because it worked good the first time, and I am sure i did everything the same.  

After searching for Printer problems, i did not find a similar thread, but if one exists and you can point me to it, or solve my problem in this thread, I would be gratefull...

---

### Post by Sef on 2006-12-08
Read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=KonicaMinolta-pagepro_1350w").

---

### Post by angelago on 2007-01-04
Hi 

I am interested in your problem cos I have a similar one myself. Before Christmas my Canon Pixma ip 3000 which is a network printer hosted on my windows machine, printed fine from the Ubuntu machine. But for the last couple of weeks it won't print. 

It says it is printing on the Linux machine - but on the windows machine nothing shows up in the print jobs and nothing happens.

I tried re-installing the printer on the linux machine, and found there is even a Pixma listed in the Dapper list of printers (which there wasn't before) so chose that. But to no avail. Nothing happens any more. It is very odd indeed.

:confused:

---

### Post by geekygreen on 2007-01-06
The good news (for me, anyway) is that after another complete reinstall of Ubuntu, which included a reinstall of CUPS and thus the printer, everything has worked fine.  However, I Have not attempted to share the printer with my win XP laptop since the reinstall.  Also, I have not removed the USB cable since reinstalling the system.
The first time, I had removed the USB cable to swap to the XP machine sometime during the fiasco.]

The long and short of it is I am not sure why, but it is working fine now.](*,) 

Except that I have a PDF document that will not print using Adobe reader for Linux (Unable to find and select the printer, it tries to print to "/lp" and nothing comes out, even though the printer que shows one job waiting...and other jobs continue to make it through and get printed...:-k 

The non-adobe PDF reader will not open this document, but it has opened and printed others.

---

### Post by petermck on 2007-01-06
It sounds like you had a problem with the CUPS setup; most likely the path to the printer was not correct. I seem to remember having a similar problem where CUPS had the path as usb://localhost/printer and it should have been ipp://localhost/printer or something like that.
Samba was necessary to get it shared and was straight forward. The option is available in System->Admin->Printing->Printer->Add Printer under network printers. I gather it can work with NFS, but I found Samba easier to work with than NFS:)

---

