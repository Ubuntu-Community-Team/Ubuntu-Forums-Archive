---
title: "Canon MP520 problems"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by flyfisher on 2008-04-11
Absolute beginner! Linux has recognised printer and is default. It seems to download info from PC, paper runs  thru but no printing. any ideas?

---

### Post by ramjet_1953 on 2008-04-11
I'm afraid it doesn't look good with the standard Canon drivers that are currently available.

Check out this link: [http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP520](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP520)

However, Turboprint claim that their driver will support your printer.

Unfortunately, it is not free, but you can download a trial, to make sure that it works for you.

Here's a link: [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

Regards,
Roger :cool:

---

### Post by flyfisher on 2008-04-11
thanks for that. Tried the Turboprint debian package but it tells me that 'dependency not satisfiable'  will keep trying, if i succeed will post it. Cheers

---

### Post by TaTaE on 2008-04-11
Have u recently changed cartridges  or refilled them ? Cannon printers must be reset than.

---

### Post by flyfisher on 2008-04-12
printer prints ok with windows xp

---

### Post by TaTaE on 2008-04-12
u have to try other driver. I had the same problem with a cannon 210 multi and it was the driver, as i recall.

---

### Post by crep4ever on 2008-04-22
I have the same problem with the Canon Pixma MP52O : well detected via usb connection but when trying it the page runs through without printing.

I tried the turboprint driver as mentioned here and yes, it works fine. However, paying for an ubuntu driver makes me sick so I would like to know if there was any (free) alternative solution. 

Thanks.

---

### Post by HabsFanInOz on 2008-05-01
> **crep4ever said:**
> I have the same problem with the Canon Pixma MP52O : well detected via usb connection but when trying it the page runs through without printing.

I tried the turboprint driver as mentioned here and yes, it works fine. However, paying for an ubuntu driver makes me sick so I would like to know if there was any (free) alternative solution. 

Thanks.

You can download drivers for the MP520 from the Canon web site:
cnijfilter-common_2.80-1_i386.deb
cnijfilter-mp520series_2.80-1_i386.deb

I installed them using gdebi-gtk, and then in the 'Printer Configuration' dialog box, I was able to install the .ppd file that comes with the driver.

Good luck.

---

### Post by crep4ever on 2008-05-03
Thanks a lot, it now works ! After downloading and installing the two packages, I created a new printer with the .ppd file and  it was perfectly fine. But I still have a problem with the scanner :D
Indeed, I've installed a few things from canon web site but ... nothing really interesting I guess. When I open gimp and try to make an acquisition, there are 4 choices :
1) paste
2) capture
3) ScanGearMP   ---> does nothing
4) XSane > Device Dialog --> tells "no device available"

Is there a solution to use the scanner ?

EDIT : sorry, the scanner works fine too. Don't forget the two packages "common + specific"

---

### Post by quoick on 2008-05-27
Try going [here]("http://www.linuxquestions.org/questions/linux-hardware-18/canon-printer-and-multifunction-drivers-for-linux-620610/") for help. I have the same printer and this fixes it right up plus gets the scanner to work in a Canon linux app (scangear). Don't worry that the best advice is about KDE, as the Gnome desktop works in a very similar way for installing onto the menu.

---

