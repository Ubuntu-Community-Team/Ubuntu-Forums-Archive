---
title: "Canon pixma mp160?"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by neogamerdrew on 2007-02-18
I bought a canon pixma mp160 from best buy today for my grandfather. He is running ubuntu 6.06, and it is fully up to date. I can't seem to find drivers. I even tried turboprint ([http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)) but for that I can't figure out how to tell it that it is a USB printer. I put the location as /dev/bus/usb/001-005/001, but that didn't work. I don't really mind using turboprint, but I need to know how to tell turboprint that it is a USB printer, or get it working with the ubuntu printer set up. Either one is fine. Thanks in advance.

---

### Post by neogamerdrew on 2007-02-18
Bump...

---

### Post by Xemanth on 2007-03-03
[http://openprinting.org/show_printer.cgi?recnum=Canon-Pixma_MP160](http://openprinting.org/show_printer.cgi?recnum=Canon-Pixma_MP160)

---

### Post by ramjet_1953 on 2007-03-03
I'm afraid that you haven't made a good choice in this printer, as it isn't well supported in Linux. Canon apparently has not released a Linux driver for it.

If you follow this link:

[http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi)

You will see that they have listed it as a paperweight.

Regards,
Roger :cool:

---

### Post by pelo8280 on 2007-04-07
Download this: [ftp://rpmfind.net/linux/fedora/extras/development/i386/gutenprint-5.0.0.99.1-2.fc7.i386.rpm]("ftp://rpmfind.net/linux/fedora/extras/development/i386/gutenprint-5.0.0.99.1-2.fc7.i386.rpm")  to your desktop.  Install "Alien" through the Synaptics Package Manager (it may already be installed).  Open a terminal window and type:
     sudo alien --scripts [*path to rpm file*]
This will create a deb package in your home folder (or the folder that you cd'd to).  Run and install that.  Then, attach your printer, turn it on, Go to System, Administration, Printing, add, etc. and install the printer with the "MULTIPASS MP150" driver.

Your Canon Pixma MP160 should work.

---

### Post by RemmyLee on 2008-01-09
I know this thread is extremely old, but by selecting the Canon MP150 drivers, you can easily make use of the Canon MP160. The only reason I revive this thread is that I just recieved one of these printers today. Also. The source code for the drivers are available, but they currently rely on the 2.0.0 gimp libraires. Porting them over should be easy enough though.

You'll need to search the [Asian Canon]("http://www.canon-asia.com/index.jsp?fuseaction=support&prod_type=bj_aio") site for the source as Linux is more widely used there, they seem to be only distributing them from that site.

They are currently distributed as RPMs only, but converting them over is easy enough and you can simply extract the source RPM.

---

### Post by sonnymk on 2008-02-01
I have to agree with RemmyLee. I just plugged in my printer, ubuntu (7.10 Gutsy Gibbon) immediately recognized it and prompted for a driver. i selected the mp150 driver (Canon PIXMA MP150 - CUPS+Gutenprint v5.0.1 Simplified) and everything is working perfectly. I didn't even need to install anything else.:)

---

### Post by burneverything on 2008-02-25
Hi

I've got one of those. It works fine over the network when plugged into an XP machine but fails to register when plugged into my ubuntu box.
I have Cups running, and I also installed the canon asia drivers after converting them via alien and following all the instructions [here](http://blog.myspace.com/index.cfm?fuseaction=blog.view&friendID=266827065&blogID=345222236&Mytoken=C92A02C6-54AF-42CF-9BA25E1D945FA9EF36284938)
I am getting this:
"/usr/lib/cups/backend/cnij_usb failed"
on the cups web interface for that printer :(
Anyone can tell me what I might be doing wrong ?  (bit of a newbie to linux, make it a dummy guide if you can :) )

[edit]Addendum 29-02-2008 >>
now getting this error in CUPS interface:
"Unable to open USB port device file: No such file or directory"
and the file refenrenced is indeed nowhere to be found, the file is:
/dev/usblp0
as refenreced in:
cnij_usb:/dev/usblp0
{/edit]
Thanks.

---

### Post by burneverything on 2008-03-03
found some drivers here today:
[http://software.canon-europe.com/software/0027403.asp?model=](http://software.canon-europe.com/software/0027403.asp?model=)
the cnij-common is a later version (rpm again) but now weighs 7.1Mb instead of the 40 odd Kb of the previous one, weird as I can't see any MP160 specific driver I'll go for this one I guess and see if it fixes it.

---

### Post by ibbill on 2008-03-03
I have the 160 installed on my  7.10 gutsy and as the above threads suggested use the 150 thats what I chose with no problems.

---

### Post by burneverything on 2008-03-05
Doh
Doh
Doh
and Doh again

works fine, the problem actually lied with a dodgy USB card with not all it's port working 
/me hangs head in shame, 
going to go and test the scanning now.
scanning works fine too

so, the printer driver is available from
[http://software.canon-europe.com/software/0027403.asp?model=](http://software.canon-europe.com/software/0027403.asp?model=)
and you want this file:
 cnijfilter-common-2.70-2.src.rpm, then either follow the instructions with alien, or extract the rpm package and build from the source this gives you.
And you can get the scanner drivers in rpm & source from the australian canon site here:
[http://support-au.canon.com.au/contents/AU/EN/0900706701.html](http://support-au.canon.com.au/contents/AU/EN/0900706701.html)

---

### Post by sam-c on 2008-03-06
> **neogamerdrew said:**
> I bought a canon pixma mp160 from best buy today for my grandfather. He is running ubuntu 6.06, and it is fully up to date. I can't seem to find drivers. I even tried turboprint ([http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)) but for that I can't figure out how to tell it that it is a USB printer. I put the location as /dev/bus/usb/001-005/001, but that didn't work. I don't really mind using turboprint, but I need to know how to tell turboprint that it is a USB printer, or get it working with the ubuntu printer set up. Either one is fine. Thanks in advance.
I also have mp160
and I found the drivers on Canon Asia , Not Europe

[http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/)

---

### Post by Brendo613 on 2008-03-29
Thanks to this page, I've gotten my Canon MP160 working problem free.  Scanner and printer both work.  Follow instructions from: [http://benaiah41.wordpress.com/2007/07/23/installing-a-canon-pixma-mp460-on-ubuntu-feisty/](http://benaiah41.wordpress.com/2007/07/23/installing-a-canon-pixma-mp460-on-ubuntu-feisty/)

=Brendan

---

### Post by orko3001 on 2008-04-11
Hi I found this but I can't paste anything into my Home folder as I don't have permission. How do I do that?

[http://www.ubuntugeek.com/how-to-get-a-canon-all-in-one-printer-working-with-ubuntu.html](http://www.ubuntugeek.com/how-to-get-a-canon-all-in-one-printer-working-with-ubuntu.html)

Cheers

---

