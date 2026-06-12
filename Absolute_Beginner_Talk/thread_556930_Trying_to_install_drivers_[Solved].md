---
title: "Trying to install drivers [Solved]"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by aja on 2007-09-21
Hello

Can someone please tell what I am doing wrong here ??  I am trying to install this printer driver for my HP laserjet 1018


INSTALLATION
------------
Unpack:
    $ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
    $ tar zxf foo2zjs.tar.gz
    $ cd foo2zjs

(Optional) Uninstall:
    $ su		OR	$ sudo make uninstall
    # make uninstall

Compile:
    $ make

Get extra files from the web, such as .ICM profiles (for color correction)
and firmware.  Select the model number for your printer:
   
    $ ./getweb 1018	# Get HP LaserJet 1018 firmware file
   

Install driver, foomatic XML files, PPD files, and extra files:
    $ su		OR	$ sudo make install
    # make install

(Optional) Install hotplug (for HP LJ 1000/1005/1018/1020):
    $ su		OR	$ sudo make install-hotplug
    # make install-hotplug



I get as far as the "make"  comand  that is where i type  

$ make

and then I get this 

me@me-desktop:~/foo2zjs$ make
#
# Dependencies...
#
      ***
      *** Error: /usr/include/stdio.h is not installed!
      ***
      *** Install Software Development (gcc) package
      ***
make: *** [all-test] Error 1


Not sure what it is telling me ??  I thought  all the required software  was to be included in this package??  Or am I just not typing in the proper command ??  should i be typing 

$ make $ ./getweb 1018	# Get HP LaserJet 1018 firmware file



Thank you in advance

AJA

---

### Post by Maestro23 on 2007-09-22
Do you have "build-essential" installed?

> sudo apt-get install build-essential

*This is needed when compiling something from source.

---

### Post by aja on 2007-09-22
That worked !!!!   Thank You !!!


aja

---

### Post by Sef on 2007-09-22
For those who want a simplier way to install the drivers, do this:

Systems > Administration > Printing

---

