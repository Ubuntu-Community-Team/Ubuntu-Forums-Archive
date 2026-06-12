---
title: "installing, printer, brother, dcp 120c, ubuntu 6.01.6"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by truth_forum on 2006-10-11
i recently installed ubuntu 6.01.6. i am happy with this os except that i have a problem with my printer brother dcp 120c. i have tried to add said printer using the add printer of ubuntu to no avail. error in printing message, although my printer would be receiving data but nothing happens.  


I have check the website of brother and it suggested that i use the driver of mfc210c. I installed the same and the log is as follows: 


log installlation mfc 210 root 
:/home/xxxx /Desktop# ls
book-toc.html  gnome-terminal.desktop  linux softwares third party
root@xxxxxxx:/home/xxxxxxxxx/Desktop# ls
book-toc.html           linux softwares third party
gnome-terminal.desktop  mfc210clpr-1.0.2-1.i386.deb
root@xxxxxxxxxxlubuntu:/home/xxxxxxxxxDesktop# dpkg -i --force-all mfc210clpr-1.0.2-1.i386.deb
Selecting previously deselected package mfc210clpr.
(Reading database ... 73067 files and directories currently installed.)
Unpacking mfc210clpr (from mfc210clpr-1.0.2-1.i386.deb) ...
Setting up mfc210clpr (1.0.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC210C': No such file or directory
chown: cannot access `/var/spool/lpd/MFC210C': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC210C': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC210C': No such file or directory
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1.0' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
root@xxxxxxxxxxxxxubuntu:/home/xxxxxxxxxx/Desktop#


I also tried to look for the .PPD file in my installer disck of dcp120c but i cannot find the same. i found instead a file pdd.  

any ideas? 

thanks.

---

### Post by mengox on 2006-10-24
you must install lpr package first.
I got the printer working following these steps:

sudo apt-get install lpr
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
sudo dpkg -i mfc210clpr-1.0.2-1.i386.deb cupswrappermfc210c_1.0.0-1_i386.deb

hope this helps

---

### Post by jadedjay on 2006-11-22
Sounds like the correct driver isnt being used. Similar to another persons problem Ive seen tonight.

Try this how to as it has worked for quite a few people in your situation

[http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)

---

### Post by Sef on 2006-12-03
Read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Brother-DCP-110C").  This is for 110c, so should work with yours.

---

