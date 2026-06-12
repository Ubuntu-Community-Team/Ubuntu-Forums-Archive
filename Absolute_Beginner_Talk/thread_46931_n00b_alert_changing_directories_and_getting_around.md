---
title: "n00b alert: changing directories and getting around long file names"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by nocitizen on 2005-07-06
Hi, I've recently installed Ubuntu and am in general completely new to linux.  I am currently teaching myself how to use operate the system via the command line, and right now I just have a fairly simple question: how do I get from one directory to another without having to first "cd ../../.." to the root directory?  For example, if I'm in, let's say, /media/cdrom/server/apache/linux and want to get *directly*  to, for example, /usr/local/bin, how do I do this?  It would sure save a lot of time.  Also, is there any way to output long file names to programs?  For example, I installed apache yesterday, and is there an easier way than typing out in full the command "gzip -d httpd-2.0.50-pc-linux-i686.tar.gz"?  Can I somehow output the filename and pipe it directly to the program?  Again, this could save a lot of time.  Any help is greatly appreciated and hopefully these questions aren't too dumb.  Thanx for your time -Lee  O:)

---

### Post by Kvark on 2005-07-06
To change directory from /media/cdrom/server/apache/linux to /usr/local/bin in one step you type "cd /usr/local/bin".

To get around long filenames you type the first letters of the filename and then hit tab to auto complete.

Btw, you went through some uneccessary work when you downloaded and installed apache. You could have gotten it up and running by just putting a checkbox for the package "apache2" (plus checkboxes for some php or whatever package if you want that too) in synaptic and hit apply.

---

### Post by nocitizen on 2005-07-07
hey, thanx for your patience, feel kind of dumb now that I know the easy answer, but THANK YOU!  much time will be saved, and thanx also for the synaptic tip, have a good one :razz:

---

