---
title: "Need printing help"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by esl1885 on 2007-08-26
I have a HP A516, which is a dedicated 4x6 photo printer. Works perfect in Windows. 

I installed it in Ubuntu with HPLIP and used the correct PPD file. When I open the HPLIP manager, my printer shows all the correct settings that should be there, such as paper type, full page printing, resolution, picture adjustments (brightness, hue, saturation, etc.). I would think that thase should be the default settings for the printer.

When I use Digikam, Gimp, or Pcture Viewer to print a picture, it appears they completely ignore any settings made in HPLIP. They give you 2 or 3 generic settings to pick from, and then appear to print whatever they feel like printing. You can't print borderless. If you set all margins to 0, you still get a border, except Gimp, where you get a big 1/2 stripe down one side.

You can go into HPLIP manager and set the brightness so high that any pic would be totally washed out, and the effect never shows up in any picture you print.

I have tried setting the printer up in HPLIP, Cups, and even downloaded KDEPrint. Nothing makes any difference.

Anyone got a suggestion.

Sam

---

### Post by Malta paul on 2007-08-26
Hi 
I had an HP  printer problem at first:
I had to install some firmware and a new driver to replace the default Ubuntu one.
Try this link it may help:  [http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)
Hope this helps:wink:

---

### Post by esl1885 on 2007-08-26
Thanks for the info, but have already been there. This where I got my PPD file from.

Sam

---

### Post by Malta paul on 2007-08-26
Is you printer listed in this database:
[http://openprinting.org/driver_list.cgi](http://openprinting.org/driver_list.cgi)
Take a look at my printer info it may give you some clues? Regards firmware.
file:///media/sda2/HP1018%20printer/show_printer.cgi.html
Good luck:(

---

### Post by Malta paul on 2007-08-26
Sorry I sent you the wrong link, this is my driver info:
[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

---

### Post by esl1885 on 2007-08-26
Yes, this is where I got my PPD file. I may be wrong, but it appears that my printing applications (Digikam, Gimp) are not communicating with the HPLIP manager.

Please understand that while I am Windows competent, I am new to Linux and don't know where to look for things like your printer info.

Sam

---

### Post by Malta paul on 2007-08-26
Hi Sam,
Yes I Know what you mean Linux is different, but when you start getting the hang of it its great so don't give up, it can be fun when you crack your problem.
Here some more help links I use  (sorry) :    [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

Hope this helps! :(

---

### Post by Malta paul on 2007-08-26
Hi Sam
I found some info about your printer:[http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_A510](http://openprinting.org/show_printer.cgi?recnum=HP-PhotoSmart_A510)
It say it will work OK with Linux, 
If you are using Ubuntu, the printer can be enabled: System >Administration >Printing >add printer
Good luck
Paul

---

### Post by Yettie on 2007-09-05
I don't know whether this will help you, but I found that my Canon IP4300 wasn't working with Gimp. The answer for me was to set it up as a generic printer in Gimp.
 In the 'Printer Setup' dialogue in Gimp choose 'Adobe' as the Printer Make and 'Postscript Level 2' as the model.  Then in the PPD box browse to the correct PPD file, mine was at /etc/cups/ppd but I don't know where yours would be. Lastly, if the print command contains 'oraw' delete that part.
In my case I now have all of the Canon driver options available in Gimp.
I hope this helps you or gives you some ideas.

---

### Post by PsycoGeek on 2007-10-09
If you are still having trouble with your HP printer you might want to try this...

1. remove HPLIP in Synaptic Package Manager (System > Administration > Synaptic Package Manager).

2. download the latest HPLIP from [here]("http://hplip.sourceforge.net/downloads.html").  I had to download the regular tarbal (down further on the page), extract it, then run the HPLIP-install file (i just double clicked it and told it to rin in a terminal window).

3. follow the instructions to set up your printer.

With this version of HPLIP I was able to get faxing and scanning over my network working.  It is way better than the installed one that Ubuntu comes with.

---

