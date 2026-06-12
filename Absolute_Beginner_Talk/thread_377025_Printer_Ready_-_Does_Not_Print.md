---
title: "Printer Ready - Does Not Print"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by rsnow on 2007-03-05
My Alps MD-1000 printer is connected to the parallel port. When I go to Administration/Device Manager, I see MD-1000 Ready. When I try to print a test page nothing happens. I click on jobs and it shows the job-stopped. When I click on properties/driver it shows the MD-1000 highlighted and recommends the ppmtomd driver. I've downloaded that driver but am not sure if I installed it correctly. On the connections tab it shows Local Printer selected, Also checked is Use another printer by specifying a port. The drop down menu shows hp no_device_found, LPT #1, Parallel Port #1(Canon), Parallel Port #1(Epson). I have tried all but the no_device_found. Can anyone suggest what I need to do next?

---

### Post by lyceum on 2007-03-07
You should just have to go to (I think it is) Systems/Administration/Printers (I am not on my Ubuntu box) and click on new printer to install. Once all the steps are done, you should see you printer there next to the install new printer icon. Can you see your printer there?

---

### Post by rsnow on 2007-03-07
Yes, I did that. That is where I found the icon saying the printer was '
ready'. Then I right clicked on the icon and then clicked on  'Properties'. Next I clicked on the 'Driver' tab and saw where it recommended the ppmtomd driver. I clicked on 'Install driver' and got a message that the ppmtomd driver was not available and so I downloaded it from the web and tried to install it. I am not sure I did that correctly.

Next, I clicked on the 'Connection' tab. It showed that "use local printer" was selected and also use printer connected to LPT#1. I tried to print a test page with these settings. Nothing happened. I went back and checked the status of the job and it said the job was stopped. I then tried printing a test page using both the Parallel Port #1(Canon) and Parallel Port #1(Epson) settings. I got the same result. I also do not understand why it says Canon/Epson when neither brands are connected. 

The Alps printer is connected to the parallel port and it reacts when I boot up the computer so I know it is getting some kind of signals that make it do its routine to get ready to print.

---

### Post by 67GTA on 2007-03-07
Go to system>administation>printing. You said you could see the printer? Right click on the printer icon and then click on print test page at the bottom to see if it will print.

---

### Post by rsnow on 2007-03-07
That is what I have done. No, it doesn't print. I don't understand how it can recognize and show that the printer is ready but then not be able to print.

---

### Post by 67GTA on 2007-03-07
If you go to sys>admin>printing and click on printer button in top left>add printer, does it show your printer? If it does you should be able to configure it without a driver installed by using cups.  I would delete the printer and start over without installing a driver.

---

### Post by steven8 on 2007-03-07
Here is the page at the OpenPrintingDatabase:

[http://openprinting.org/show_printer.cgi?recnum=Alps-MD-1000]("http://openprinting.org/show_printer.cgi?recnum=Alps-MD-1000")

---

### Post by ramjet_1953 on 2007-03-07
You can also follow this link:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Alps-MD-1000](http://www.linuxprinting.org/show_printer.cgi?recnum=Alps-MD-1000)

It has lots of info and says that your printer should work perfectly.

Regards,
Roger :cool:

---

### Post by rsnow on 2007-03-08
OK I tried the suggestion to start over and add the printer without installing the driver. Now when I click on jobs it shows the job as printing but the printer is not doing anything.

I know that even on my fast machine it sometimes takes awhile for a print job to be processed and actually start printing. This is an old 400Mhz clunker that I am using to try out Ubuntu and see if I want to put it on my other computer. How long should I have to wait for a small text message to actually begin printing?

---

### Post by lyceum on 2007-03-08
> **rsnow said:**
> OK I tried the suggestion to start over and add the printer without installing the driver. Now when I click on jobs it shows the job as printing but the printer is not doing anything.

I know that even on my fast machine it sometimes takes awhile for a print job to be processed and actually start printing. This is an old 400Mhz clunker that I am using to try out Ubuntu and see if I want to put it on my other computer. How long should I have to wait for a small text message to actually begin printing?

Adding the printer is installing the driver in Linux. I am not sure how well that works with a live CD thoguh. If things are moving too slow you may want to Xubuntu. If your printer is on the list, it should be working no problems. Unfortunetly that is all I know. I am sure you can go to the termenal and gather some data to help move things along, but I am not sure where to start there. Sorry.

---

### Post by rsnow on 2007-03-09
Thanks for trying to help. I will keep working on this as time permits. In the meantime, I have some other issues that need my attention. Thanks again.

---

### Post by lyceum on 2007-03-09
> **rsnow said:**
> Thanks for trying to help. I will keep working on this as time permits. In the meantime, I have some other issues that need my attention. Thanks again.

When you get the time, check out psycocat's Ubuntu page. There is a link to it in the top of my signature. It can be very helpful. Sorry we could not do more. It sounds like you are trying to install the Windows way, I am not sur ewhy the Linux way would not be working. :confused:

---

