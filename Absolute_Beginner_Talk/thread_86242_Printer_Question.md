---
title: "Printer Question"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by pet on 2005-11-04
My dad being in a generous mood just went out and bought me a printer/copier/scanner all in one without asking me.  Problem is of course it came with windows software and I have no idea how or if it will work on here since I only have linux (ubuntu).  It is HP PSC 1401.

Anyone know if it will work or how to make it work?  Please keep in mind I know very little about computers or how to do things in linux.  Im trying to learn but it has been a very slow and tedious process for me.  Any help appreciated.  Also, if it wont work does anyone know a specific printer that does set up and work easily with linux?

---

### Post by jrib on 2005-11-04
try to see if your printer is on [http://www.linuxprinting.org](http://www.linuxprinting.org)

---

### Post by Cufishing on 2005-11-04
It appears there is Linux support.
[http://www.linuxprinting.org/show_driver.cgi?driver=hpijs&fromprinter=HP-PSC_1400](http://www.linuxprinting.org/show_driver.cgi?driver=hpijs&fromprinter=HP-PSC_1400)

---

### Post by pet on 2005-11-04
Thank you for the link

---

### Post by pet on 2005-11-04
hmm that link didnt work but I did find this [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1400](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1400)
and this
[http://hpinkjet.sourceforge.net/](http://hpinkjet.sourceforge.net/)
Which to me they look promising but now only if I understood what a driver was.....

---

### Post by Joe_lurker on 2005-11-04
Install the package hpoj using the package manager.  It is in the 'Universe' so you will need to have that enabled.  Please post if you need specific instructions on installation of packages.

Once the package install is complete run the command:
```
sudo ptal-init setup
```
You can see the complete documentation at [http://hpoj.sourceforge.net/doc.shtml](http://hpoj.sourceforge.net/doc.shtml) (click on doc/index.html).  I believe that you can then use the System | Adminstration | Printing dialog to finish the setup.

-Joe

---

### Post by pet on 2005-11-04
Thank you very much.  No time right now but will do it all in the morning just wanted to say thanks for that info.

---

### Post by pet on 2005-11-09
It wouldnt print so I ended up doing this because a friend told me to [http://hpinkjet.sourceforge.net/install.php#download_install](http://hpinkjet.sourceforge.net/install.php#download_install)
I am under debian on step 2 Download and install the HP printing software, step 6 on that part and I keep getting stuck.  Right now I am stuck because of this

configure: error: "cannot find libjpeg support"
configure: error: /bin/sh './configure' failed for prnt/hpijs

Is there a command I can use to find this?  Thanks for any help.

---

### Post by Joe_lurker on 2005-11-09
You need to install libjpeg62-dev with the package manager.

-Joe

---

### Post by pet on 2005-11-09
Thank you for all the help so far and I hate to keep being a pain but dont have anyone else to ask...

bash: /etc/init.d/cups: No such file or directory

Cups is installed so argh what am I doing wrong?

---

### Post by Joe_lurker on 2005-11-09
Try /etc/init.d/cupsys

-Joe

---

### Post by pet on 2005-11-10
thank you that did work.  I messed something else up though out of frustration tried to do a step before a previous step was done and of course that didnt work so....now when i go to the page it says to go to  [http://localhost:631](http://localhost:631)   I get this error message at the top saying Administrative tasks have been disabled for security reasons. Please use Menu System > Administration > Printing

I tried setting up the rest of the printer thru my admin menu that didnt work either.  It is showing up in there and says ready but it is not printing and I have no HP device toolbox like that page said I should have so now I am totally lost as to what to do.  I dont know how to get [http://localhost:631](http://localhost:631)  to accept my username and pword since I messed it up and I even tried cleaning out the cache and stuff and rebooting but nothing is working.

---

### Post by pet on 2005-11-11
Anyone have any ideas of what I should do next?  Thanks for any help.

---

### Post by pet on 2005-11-11
Ok well I got it to print finally.  But the HP toolbox wont open I keep getting this error

 File "/usr/share/hplip/base/async_qt.py", line 201, in connect
    raise socket.error, err
socket.error: 111


How do I fix this?

---

### Post by Master Shake on 2005-12-11
Yes!  Thanks!  This worked for me!

---

### Post by arphe_el on 2005-12-13
i have an hp deskjet 3650 i installed on the server computer the driver and also with the client computer the driver and it's working for network printing both are running perfectly my question is when i notice to print at client computer when i click on the properties there is no draft mode is there a way to install draft option?

thank you and GODspeed!

---

### Post by hesee on 2005-12-13
HP all-in-one printers are pretty well supported in Breezy. I added my own (PSC 2355) from Printing(or something likethat) menu. It was really easy to install it, took only 10 seconds. Are you sure you cannot install your printer from there?

---

### Post by arphe_el on 2006-02-27
what version are you using is it hoary (5.04) or breezy (5.10)?

---

### Post by PaDV on 2006-02-28
The PSC 1400 should work from a standard Breezy Badger 5.10 installation with HPLIP.
But there is a bug preventing "hp" backend devices to be detected (see Ubuntu bug #3841).
You can solve this by following this HOWTO: [https://wiki.ubuntu.com/HPPrinterInstallation](https://wiki.ubuntu.com/HPPrinterInstallation).

---

