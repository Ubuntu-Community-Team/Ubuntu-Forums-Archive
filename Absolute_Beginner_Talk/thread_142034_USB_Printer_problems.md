---
title: "USB Printer problems"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by B7may on 2006-03-09
I am trying to get a HP Laserjet 1000 printer to work and am having a difficult time.  The computer recognizes it, finds the driver and installs it seemlessly.  However, I cannot get it to print anything.  I searched the forum and found a site called [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)  This site has some instructions on what to do, but it comes to a command called make and my system does not recognize that command.  Does anyone know what this means, or an easier way to get this printer to work.  Here is the commands from the website:

$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
Unpack:
    $ tar zxf foo2zjs.tar.gz
    $ cd foo2zjs
Compile:
    $ make

(Optional) Get extra files from the web, such as .ICM profiles for color
correction, and firmware:
    $ ./getweb 2300	# Get Minolta 2300 DL .ICM files
    $ ./getweb 2200	# Get Minolta 2200 DL .ICM files
    $ ./getweb cpwl	# Get Minolta Color PageWorks/Pro L .ICM files
    $ ./getweb all	# Get all of the above

Install driver, foomatic XML files, and extra files:
    $ su			OR	$ sudo make install
    # make install

(Optional) Configure hotplug (USB; HP LJ 1000/1005/1020):
    # make install-hotplug	OR	$ sudo make install-hotplug

(Optional) If you use CUPS, restart the spooler:
    # make cups			OR	$ sudo make cups

---

### Post by JShadow on 2006-03-09
You need the packace build-essential for the make command. Search for it in synaptic

---

### Post by Sef on 2006-03-09
sudo apt-get install build-essential


From Linuxprinting:

 The firmware of the printer must be uploaded after turning it on. You can use a hotplug/udev script which comes with foo2zjs, or do it manually: "cat /usr/share/foo2zjs/firmware/sihp1000.dl >  /dev/usb/lp0".

[http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000]("http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000")

---

