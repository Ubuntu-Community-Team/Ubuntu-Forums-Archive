---
title: "Gutenprint and Canon"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by measekite on 2007-09-21
Once you get the IP4200 print driver working (if it is possible) can you use Gutenprint with this driver?  It seems when you just use Gutenprint it uses its own driver and the resolution is low and the results are poor.

Printing and Scanning are keeping me from using Linux as a primary OS.  Printing is so important and seems to be neglected by the developers who promote Linux.

---

### Post by Daveth on 2007-09-21
not sure whether Gutenprint supports, but Turboprint does. See

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

---

### Post by Yettie on 2007-09-21
I think the answer is yes but you have to set it up as a Postscript Printer. That's the way I  got my IP4300 working with Gimp. For 'Make' and 'Model' I chose 'Adobe' and 'Postscript 2', then I was able to select the correct driver by navigating to it in PPD file selection box. It should be at /etc/cups/ppd.

This works for Gimp, although I had to adjust the gamma settings in the 'Output options'. It gives all the driver options, such as resolutions up to 4800 dpi and all the paper types. I think it allows duplex  printing although I haven't tried that, but it won't print borderless.  

I tried the same thing with Photoprint but I haven't been able to get that to work.

Incidentally, this 'How to' is the best guide I have come across for installing a Canon IP4200/4300 -  

[http://www.erlandertervueren.com/ubuntu/ip4300_guide/](http://www.erlandertervueren.com/ubuntu/ip4300_guide/)

---

### Post by measekite on 2007-09-21
Thanks

I assume it will work for the IP4000 as well.

Would you please post a HowTo clarifying the steps used to get this driver to work with Gimp and how to configure it.  I do not understand gamma settings nor do I understand how to set it up as a Postscript printer.

---

### Post by Maestro23 on 2007-09-21
From OpenPrinting.org for Cannon IP 4000: [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-iP4000](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-iP4000)

---

### Post by Yettie on 2007-09-21
> **measekite said:**
> Thanks

I assume it will work for the IP4000 as well.

Would you please post a HowTo clarifying the steps used to get this driver to work with Gimp and how to configure it.  I do not understand gamma settings nor do I understand how to set it up as a Postscript printer.

The following guide works for a Canon IP4300 printer, using the driver from the Canon Australia web-site. I think the same method should work for other IP4300 series printers.

Open an image in Gimp and select 'File - Print', this will open a printing dialogue.
Select the 'Printer settings' tab and then ' Setup Printer'.
In the new box which opens choose the 'Printer Make' as 'adobe' and the 'Printer Model' as 'Postscript 2'.
In the box for 'PPD File' browse to the location for your printer driver. If you have it installed correctly in CUPS it will be at /etc/cups/ppd/iP4300-Ver.2.70.ppd
Choose the option for 'Standard Command'.
In the 'Printer Queue' box choose the name that you have given to your printer when you installed it.
Click 'OK' to close the window.
Back in the main printing window the 'Printer Name' should now show as 'Printer' and the 'Printer Model' as 'Postscript Level 2'.
Click on 'Save Settings' at the bottom and you should be set up for printing.

Prints seem to be pretty good for colour and quality, but if you want to you can adjust the settings. Choose the 'Output' tab at the top of the window, and then click on 'adjust output'. This opens a window with a number of advanced adjustments - click on the little boxes on the left to access the greyed out options. Close the box to return to the main window.
When you are happy with the setup, click on 'Save Settings' or 'Print and Save Settings' and you won't have to set everything up again next time.

---

### Post by measekite on 2007-09-21
> **Yettie said:**
> The following guide works for a Canon IP4300 printer, using the driver from the Canon Australia web-site. I think the same method should work for other IP4300 series printers.

Open an image in Gimp and select 'File - Print', this will open a printing dialogue.
Select the 'Printer settings' tab and then ' Setup Printer'.
In the new box which opens choose the 'Printer Make' as 'adobe' and the 'Printer Model' as 'Postscript 2'.
In the box for 'PPD File' browse to the location for your printer driver. If you have it installed correctly in CUPS it will be at /etc/cups/ppd/iP4300-Ver.2.70.ppd
Choose the option for 'Standard Command'.
In the 'Printer Queue' box choose the name that you have given to your printer when you installed it.
Click 'OK' to close the window.
Back in the main printing window the 'Printer Name' should now show as 'Printer' and the 'Printer Model' as 'Postscript Level 2'.
Click on 'Save Settings' at the bottom and you should be set up for printing.

Prints seem to be pretty good for colour and quality, but if you want to you can adjust the settings. Choose the 'Output' tab at the top of the window, and then click on 'adjust output'. This opens a window with a number of advanced adjustments - click on the little boxes on the left to access the greyed out options. Close the box to return to the main window.
When you are happy with the setup, click on 'Save Settings' or 'Print and Save Settings' and you won't have to set everything up again next time.
Apreciate the resoinse.

My goal is to print high quality photos.  I have read on various forums that people who used this driver can only get 600x600 dpi which does not produce great photo results.

How do you get what the printer is capable of?

Also, I am planning on getting a Canon Pro 9000.  I do not see drivers for that anywhere.  Is the only solution having to buy Epson like an R1800?

I just cannot believe that Linux (all distros but especially Ubuntu) is a first class OS that works better than Windows and the hardware mfg (expecially Printer and Scanning mfg) do not want to support it.

According to what I read that Mark Shuttleworth said the number one bug in Ubuntu is MS Windows.  I cannot see that the bug will be solved without solving the hardware problem.

I am not the only one having problems.

---

### Post by Yettie on 2007-09-22
If you follow the guide at - [http://www.erlandertervueren.com/ubuntu/ip4300_guide/](http://www.erlandertervueren.com/ubuntu/ip4300_guide/) - for installing the driver, the section towards the end under 'Advanced Features' explains how to enable higher resolutions. These should then be available in any application which uses the driver correctly. With the Canon driver you definitely should be able to get 4800 dpi.

I have only recently been able to get my printer working and so far the results have been mixed. As explained, Gimp seems to work pretty well now. I haven't been able to do anything with Photoprint yet. F-spot works but there is no colour adjustment and the prints are too yellow. Gthumb is Ok for quick jobs and the prints look reasonable, although there is no colour adjustment again. The same for Eye of Gnome. Gnome Photoprinter stalls and doesn't print anything. Firefox looks as though it should be OK but I haven't tried it yet.
Really, for serious photo printing, Gimp seems the best bet. The results seem pretty good to me and there are lots of adjustments that you make, so I hope you can get the sort quality you are looking for.

I can't help with the Canon Pro 9000 I'm afraid. I think Canon printers are very good with Windows, but If I was looking for a replacement now I think I would have to seriously consider getting a printer which was better supported, like an HP or an Epson. Having said that, I have heard that setting up printers will be made more straightforward in Gutsy, so things may improve soon.

---

### Post by babakan on 2007-09-23
> **Yettie said:**
> I think the answer is yes but you have to set it up as a Postscript Printer. That's the way I  got my IP4300 working with Gimp. For 'Make' and 'Model' I chose 'Adobe' and 'Postscript 2', then I was able to select the correct driver by navigating to it in PPD file selection box. It should be at /etc/cups/ppd.

This works for Gimp, although I had to adjust the gamma settings in the 'Output options'. It gives all the driver options, such as resolutions up to 4800 dpi and all the paper types. I think it allows duplex  printing although I haven't tried that, but it won't print borderless.  

I tried the same thing with Photoprint but I haven't been able to get that to work.

Incidentally, this 'How to' is the best guide I have come across for installing a Canon IP4200/4300 -  

[http://www.erlandertervueren.com/ubuntu/ip4300_guide/](http://www.erlandertervueren.com/ubuntu/ip4300_guide/)

I got PhotoPrint to work with Turboprint (the Gutenprint drivers for my ip5200 are for text only). Need to use the latest verssion of PhotoPrint, not in Ubunto repos. I had to install from source, quite hard, there are a lot of dependencies.

---

