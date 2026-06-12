---
title: "Brother MFC 4800 Linux driver"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by granade on 2007-03-29
Hi,

1.This is my first post but not my first time on this forum. So far i have been able to solve most of my small problems from research here. This however has me stomped. Im trying to get printing going on my wifes laptop using latest Ubuntu CE distro.

I downloaded mfc4800lpr-1.1.2-1.i386.rpm but the file i found has a .rpm extension. Below is my output from terminal.


Thank you for any help.


@toshiba:~$ sudo dpkg -i --force-all ./Desktop/mfc4800lpr-1.1.2-1.i386.rpm
dpkg-deb: `./Desktop/mfc4800lpr-1.1.2-1.i386.rpm' is not a debian format archive
dpkg: error processing ./Desktop/mfc4800lpr-1.1.2-1.i386.rpm (--install):
subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
./Desktop/mfc4800lpr-1.1.2-1.i386.rpm

---

### Post by Cathead Fred on 2007-03-29
Hi granade,

Sorry to hear about your problem. I believe you want to convert the .rpm file into a .deb file. You will need something called, "Alien". Here are a couple of links that should help you get your printer working on your wife's laptop. 

(1). Here is a link that goes into detail on how to use Alien to convert .rpm to .deb.

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)


(3). This is a fantastic link called, "How to install ANYTHING in Ubuntu! This covers anything you want to install in Ubuntu. Add it to your favorites list.

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)


Kudos to you for getting your wife to use Linux! I'm still trying to get my wife to give it a shot.

Good luck and post your progress

Cathead Fred

---

### Post by Dirk_McJerk on 2007-10-19
I have finally got my Brother MFC 4800 working. I am connecting to the printer via windows network. The  driver responsible fo this success is the Brother MFC-8300 - H17x0 ppd which can be found at the following url.

[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-MFC-8300](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-MFC-8300)

---

### Post by chronos00 on 2007-10-23
Thanks so much for posting back the solution u found!
I have been battling with the same problem for over a month!!
I tried Brother RPM drivers, alienated RPMs from brother, windows drivers, and an awful lot of similar ubunutu builtin drivers... with no luck.

On the other hand, your solution worked flawlessly!!
By the way, the driver u described is buitin in ubunty gusty; no need to download.

One down, two to go :-p (Scanner and Fax). If u already have a solution for this too I would love to know about it.

Regards and thanks for posting back!

---

### Post by froy02 on 2007-10-30
Here' the website for the Brother printers, mfc, scanner, fax machines drivers.  They  have both the debian and rpm lpd and cups drivers. They also have the instructions for the installation. Make sure you install the lpd driver first for the printers. 

The scanner drivers and instruction are there too. Just find the deb drivers for your scanner and download them then install with gdebi installer.
Just make sure you install the brscan drivew before the brscan-key.

Here's the brother website:
[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

By the way you can setup your printer by using your browser (firefox). Type 'http://localhost:631' and a dialog box for printers will come out.

Froy

---

