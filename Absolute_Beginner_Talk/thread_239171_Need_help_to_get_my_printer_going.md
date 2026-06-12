---
title: "Need help to get my printer going"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by metalaxesucks on 2006-08-18
I'm trying to get my printer going, but my model # isn't listed in the "Add a Printer" box. I'm using a Lexmark printer model number Z705.
Actually, I saw the directions on another thread, but it was over my head.
It said -

Code:
$ mkdir lexmark
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
$ tail -n +143 z600cups-1.0-1.gz.sh > install.tar.gz # the sh script is broken for newer systems. use `tail` to extract the binary portion of the script.
$ tar -xvzf install.tar.gz # extract the contents produced by tail
$ alien -t z600cups-1.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ alien -t z600llpddk-2.0-1.i386.rpm # convert unusable rpm packages to tgz.
$ sudo tar xvzf  z600llpddk-2.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo tar xvzf z600cups-1.0.tgz -C / # extract the tgz's to / putting the files in their right place
$ sudo ldconfig # DO NOT SKIP THIS STEP or your printer backend won't find required libraries
$ cd /usr/share/cups/model
$ sudo gunzip Lexmark-Z600-lxz600cj-cups.ppd.gz # unzip the ppd, which should _not_ be gzipped

What exactly am I supposed to do with all this? Where do I punch it in?
Please be specific.

And what is this?

The driver is now installed. Restart the cups daemon:
Code:
/etc/rc2.d/S19cupsys restart

And this?

Check whether the printer backend works;
Code:
$ cd /usr/lib/cups/backend $ ./z600

Etc...Etc...Etc...Etc...

As you can tell, I'm completely stupid when it comes to Linux, but if somebody could explain how to do this step by step it would be a big help.  

Thanks in advance

---

### Post by awkward1234 on 2006-08-18
have just looked on Lexmarks website, and they have a download for a linux driver for your printer, although whether it will work under Ubuntu? Also has details on installation.....good luck! Mark:???: 

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=78:1:0:387:0:0&emeaframe=&fileID=1030&searchLang=en](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=78:1:0:387:0:0&emeaframe=&fileID=1030&searchLang=en)

---

