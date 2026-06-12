---
title: "canon pixma mp610"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by chaka53 on 2007-11-22
Hey

How do I get my Canon pixma mp610 to work in ubuntu 7.10  

I have tried a few of the Canon drivers but no go

Any help appreciated

Thanks

---

### Post by brn on 2007-11-22
Here is a link to some Canon drivers.but does not include the MP610. ```
http://openprinting.org/printer_list.cgi?make=Canon
```
About all you can do is try different drivers.  You might get lucky.

---

### Post by dmizer on 2007-11-22
try these ... the pixus printers are the same as the pixma printers (different in name only).

[http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

ubuntu directions included.  your printer is not explicitly listed, but one of the drivers is likely to give you limited or full printing capability.

---

### Post by phelge on 2007-11-23
Follow instructions here : [http://mp610.blogspot.com/](http://mp610.blogspot.com/)
It should work. Unfortunately there is still no driver for the scanner part.

---

### Post by nicolos on 2007-11-25
Hi, 

Just to inform you that a Sane scanner driver is now available for the MP610 all-in-one. 
Based on the Sane pixma library I've modified.

The files are available at the same address (you can follow my signature).

Any feedback appreciated !

Nicolas

---

### Post by phelge on 2007-11-27
Hi,

Thanks Nicolos for the scanner driver. It works. I had same issue as only root can scan. I've added these 2 lines in /etc/udev/rules.d/45-libsane.rules :
# Canon PIXMA MP610
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="1725", MODE="664", GROUP="scanner"

The MP610 is really a nice all-in-1 printer.

---

### Post by Potemkin on 2007-12-23
Thanks for your work creating these ppd files, Nicolos. They make my new Canon MP610 a joy to use under Linux. However, there seems to be a slight problem with the English version of the ppd file. When I install my MP610 under CUPS using that ppd file, the printer only ever prints out the first page of every document, then stops. In other words, it ignores all but the first page of every document I try to print. I switched to using the French version of the ppd file, and it works perfectly. There may be a glitch in the English version. Maybe you should take a look?

Thanks again for all your efforts on behalf of all us Ubuntuites. It's guys like you who make Ubuntu Linux the great OS it is. :D

---

### Post by nicolos on 2007-12-24
> **Potemkin said:**
> Thanks for your work creating these ppd files, Nicolos. They make my new Canon MP610 a joy to use under Linux. 

Thanks again for all your efforts on behalf of all us Ubuntuites. It's guys like you who make Ubuntu Linux the great OS it is. :D

Thanks Potemkin for your cool comment :cool:

I've just done some additional tests with: 
- latest Canon MP610 ver 2.80 driver (is it the one you're using ?), 
- both English and French MP610 PPD files

but I cannot get the issue you're talking about. 

I've also diff the 2 files English and French MP610 PPDs, but I don't see anything wrong.

However, could you check these points: 
The Canon driver uses sometimes a lot of disk space in /tmp (about 105 Mb for an A4 print, at 600 dpi), in duplex printing. 
If disk space is not large enough, then it prints only the first page of a document. (I already experienced that).
Could you check that you have such available disk space in /tmp (be careful if you have /tmp declared as a tmpfs filesystem...).

Also, could you check in /var/log/cups/error_log if you see any suspect line (error, crash, ...) ?

I'll leave the English MP610 PPD file for a while on my system and see if I get anything wrong.

---

### Post by Potemkin on 2007-12-24
Thanks for your quick response, Nicolos. :)

I tried what you suggest, and it now works perfectly. I keep Ubuntu installed on a 10 Gig partition, separate from my /home partition, and when I checked it, I found that it had been almost completely filled - only about 600 MB space was left. I uninstalled some of the programs I use less often, and it now has about 2 Gigs free. I tried the MP610 with the English version of the ppd file, and it now works perfectly, even in duplex. I feel like such a fool now! :(

Oh well, at least I now know what was causing the problem, and your advice has solved it. I apologise for wasting your time with such a trivial problem (though I still don't understand why the French version worked when the English version didn't). Thanks again for all your hard work. :D

---

### Post by nicolos on 2007-12-27
Never mind, this issue was not easy to trace. 
Thanks for your feedback anyway, this greatly helps to enhance and ease any development work. :cool:

---

### Post by theproc64 on 2008-01-09
Here's how I got my mp610 to work with ubuntu:
1.  go to [http://www.canon-asia.com/index.jsp?fuseaction=support&prod_type=bj_aio&country=SG](http://www.canon-asia.com/index.jsp?fuseaction=support&prod_type=bj_aio&country=SG) and download both the common and the mp610 printer and scanner drivers.
2. install them
3. I just plugged in my printer and it installed automatically.  If that doesn't work, just do a normal printer install.
4. for scanning, just go into the terminal and type    scangearmp

---

### Post by theproc64 on 2008-01-13
I installed the linux drivers from the canon website and at first it worked perfectly:).  Now when I try to print to it it says "The printer may not be connected".  Hmmm.... That's interesting considering the scanning works:confused:.  I tested it with a windows computer and it works fine.  It also works fine on another computer running linux with the same driver.  I think it might have something to do with the permissions on who can access the printer but I'm not sure.  Any ideas?

---

### Post by Kenda on 2008-01-15
]Thanks Nicolos for all your work on this - my MP610 is now working perfectly (including the Scanner) - Your blog  and your advice here has been extremely helpful.:) Merci Beaucoup.

---

### Post by theproc64 on 2008-04-12
The canon asia site is now down but I found the drivers [here]("http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP610%0amenu%3d%3dDownload%0aos%3d%3dLinux&") at the Australian site.  I attached the scanner drive and the common printer driver but you still need to download the mp610 driver because it was too big to attach.

---

### Post by silkstone on 2008-06-06
An old thread, but I thought an update may be useful...

You can now download Linux printer and scanner drivers for the Canon MP610 from the Canon website here...

[http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20MP610%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20MP610%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&)

The drivers are available as both .rpm and .deb.

You need four packages - the **Common package** and the **Package for the MP610 series** for both the Printer Driver v2.80 and Scangear MP v1.10.

Once downloaded, install the Common packages first (just double-click on the .deb file), and then install the MP610 packages.

Switch the printer on and it should show up in the printers list.

To launch Scangear, open the terminal and type **scangearmp**

You can easily add this to the menu system and/or as a launcher on the panel. The command is just scangearmp.

---

### Post by IanW on 2008-06-08
Just a heads-up to say that Canon's drivers have also appeared on their European site [here](http://software.canon-europe.com/products/0010488.asp).
(Edit: Sometimes it's there, sometimes it 404's. WTF?)

Either scroll to the bottom, or select "Linux" as your OS. Both rpm & deb are there.

Re: Scanning - MP610 Blogspot has info on installing the latest SVN version of XSane - probably better for compatability with Gimp, Openoffice, etc.

---

