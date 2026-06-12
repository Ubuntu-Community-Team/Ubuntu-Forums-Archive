---
title: "Problem with my scanner HP Scanjet 3970"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by nashnash on 2006-10-30
Hello :p  ,
I installed ubuntu 6.10 yesterday and i have problems installing my scanner ](*,) 
First, i tried to install kooka , tho i cant find there the "Scan Now" Button lol :mrgreen: 
then i tried Xsane , and it told me "Device is not available"
i searched abit , googled, ubuntu forums ---> and found a guide:
[http://ubuntuforums.org/showthread.php?t=152762](http://ubuntuforums.org/showthread.php?t=152762)
i installed sane:
sudo apt-get install sane
sudo apt-get install sane-utils
and i installed hp3900-series Driver from this website:
[http://sourceforge.net/projects/hp3900-series/](http://sourceforge.net/projects/hp3900-series/)
:cool:  ...... :cool: 
then it has changed from "Device is not available" to "Failed to open Device - access to resource has been denined"
as you can see in that picture:
[http://img214.imageshack.us/img214/3449/screenshot3aq0.png](http://img214.imageshack.us/img214/3449/screenshot3aq0.png)
......... 
at the end of the guide [http://ubuntuforums.org/showthread.php?t=152762](http://ubuntuforums.org/showthread.php?t=152762)
there is this guy saying "I have a fix for my problem. I had to go into /dev/bus/usb/005 and do a chmod a+w on 002 and all worked out well! " , i dont have any /005 , i have only 001 002 003 004 Devices, and i tried sudo chmod a+w on 002, nothing happened.
at later on the guide, someone said: "Thanks for the tip Ben. This works great with my Scanjet 3970"
eeh.. i have the same thing ! Scanjet 3970 !
so i went to #ubuntu @ irc.freenode.com and asked for help there, and people told me its probably a problem of my access settings.
they told me to go to System ---> Administration --> Users and Groups and fix there Scanner access to my user.
but i cant see there any scanner access, i dont understand what i have to do there. here is a picture:
[http://img247.imageshack.us/img247/259/screenshot7xt7.png](http://img247.imageshack.us/img247/259/screenshot7xt7.png)
i marked my user on "Properties" @ Scanner , but its not working and i dont think its the right.
If someone knows how to fix it or give scanner access to a user,
Please help me to solve this problem!
I will appriciate it :) 

Thanks alot,
nashnash

---

### Post by ayryq on 2006-11-03
Permissions are probably your problem still. To figure out which device is your scanner, open device manager:
System > Administration > Device Manager
The tree probably has several USB controllers, each with devices under them. Dig down until you find your scanner. Under your scanner is "USB Raw Device Access." Select this, and look at the Advanced tab on the right. One of the entries should be linux.device_file which will show you the filename for this device. On my system, my 3970 is /dev/bus/usb/001/002. Yours is probably different. So, on my system, I type in a terminal
```
sudo chmod a+w /dev/bus/usb/001/002
```
which does the trick for me.

Eric

---

### Post by VividHazE on 2006-11-18
Thank you so much you guys! I read somewhere a while ago that my Scanjet 3970 would never work on Linux and I got disheartened, but after following both of your advice its now working with XSane! thank you! Another reason I don't have to go back into windoze now :)

---

### Post by MoebusNet on 2007-03-30
This was the missing piece of the puzzle for me! Sane finally sees my HP Scanjet 4370 flatbed scanner! I know I'm asking a favor, but would someone _please_ organize and turn this into a how-to? If I knew what-in-the-world I was doing, I'd do it myself, but at this level I'm doing well to copy-and-paste into Terminal to get my scanner to work at all.  Thank you to everyone involved in this effort!

---

### Post by Princey on 2007-05-06
> **MoebusNet said:**
> This was the missing piece of the puzzle for me! Sane finally sees my HP Scanjet 4370 flatbed scanner! I know I'm asking a favor, but would someone _please_ organize and turn this into a how-to? If I knew what-in-the-world I was doing, I'd do it myself, but at this level I'm doing well to copy-and-paste into Terminal to get my scanner to work at all.  Thank you to everyone involved in this effort!

Hi, I am having problems getting my HP ScanJet 4370 running under Fiesty X86_64 and I'm running Kubuntu. I've tried everything in the both threads mentioned but nothing. Does that mean that sane doesn't work or run well on X86_64 machines or it's something I'm not doing wrong? 

The only change I made was to use --force-architecture as I'm running 64Bit. I can't get the chmod stuff to work as I don't have a device manager. Kinfo center yield the following:

---

### Post by ewing on 2007-05-07
This is what I did and my scanjet 3970 is working now (Feisty 64bits)

1. download
sudo apt-get install sane sane-utils libsane-extras
sudo apt-get install xsane xsane-common

2. download hp3900-sane1018_src_0.8.tar.gz from [http://sourceforge.net/projects/hp3900-series/](http://sourceforge.net/projects/hp3900-series/)
and [http://alioth.debian.org/frs/download.php/1669/sane-backends-1.0.18.tar.gz](http://alioth.debian.org/frs/download.php/1669/sane-backends-1.0.18.tar.gz)

3. decompress
tar xfz sane-backends-1.0.18.tar.gz
tar xfz hp3900-sane1018_src_0.8.tar.gz

4. Patch the sane project with hp3900 backend
cd sane-backends-1.0.18 
patch -p1 < ../hp3900-sane1018_src_0.8/hp3900-sane1018_0.8.diff

5. Configures SANE in order to compile only the driver for hp3900 backend:
export BACKENDS=hp3900
./configure

6. For compilation, it is necessary installed project SANE. In normal time, that would be done with make install, but as SANE is already installed by a system of package (rpm or deb), it is better to copy manually the file of the backend hp3900:
cp ./backend/libsane-hp3900.la /usr/lib/sane/
cp ./backend/.libs/libsane-hp3900.so.1.0.18 /usr/lib/sane

[COLOR="Red"]7. If you obtain an error of the type: Failed to open Device - access to resource has been denied, it acts of a problem of right of access.
To determine which bus usb uses the scanner (under gnome, Système - Preferences - Hardware Information) and throw the order: sudo chmod a+w /dev/bus/usb/001/002 where 001 and 002 is the indication of the bus and varies according to your system.
[/COLOR]

8. Run Xsane

Source [http://www.frinix.com/Scanner-hp-scanjet-3970-sur-linux](http://www.frinix.com/Scanner-hp-scanjet-3970-sur-linux)
Sorry my Altavista english :lolflag: :)

---

### Post by Princey on 2007-05-08
Thanks for the help, ewing but I run into problems when installing libsane-extras. This is what I get: > Unpacking libsane-extras (from .../libsane-extras_1.0.18.5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libsane-extras_1.0.18.5_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/sane/libsane-hp3900.so.1.0.18', which is also in package hp3900-sane
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package sane.
Unpacking sane (from .../sane_1.0.14-1_amd64.deb) ...
Selecting previously deselected package sane-utils.
Unpacking sane-utils (from .../sane-utils_1.0.18-3ubuntu1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libsane-extras_1.0.18.5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas?

Edit: Found the problem. Had to remove the hp3900-sane i386 deb first. Crossing my fingers now

---

### Post by Princey on 2007-05-08
Update: Completed steps 1-5 with no problems. However, on step 6 where I had to issue the commands > cp ./backend/libsane-hp3900.la /usr/lib/sane/
cp ./backend/.libs/libsane-hp3900.so.1.0.18 /usr/lib/sane separately, I'm getting the following: > cp: cannot stat `./backend/.libs/libsane-hp3900.so.1.0.18': No such file or directory


When I try running xsane , I get the error message that access will to the device has been denied. I'll try later as I have to leave for work now.

P.S. As posted a few posts above, I can't get the /bus/device listings as explained several times by different posters. See a few posts up what I'm getting.

---

### Post by Princey on 2007-05-08
Nevermind, I did the > lsusb command and got the device listing. It's working now. Thanks a million:lolflag: :popcorn:

---

### Post by Princey on 2007-05-10
Update: 

The scanner works, sort of. You can hear it come on and scan but all I get is a black box that grows in size according to the dpi resolution set as my output image. Nothing else. I've gone through all the settings, nothing. I remember when performing step 6 of the how to, I got this > cp: cannot stat `./backend/.libs/libsane-hp3900.so.1.0.18': No such file or directoryerror message. Is that what that's causing it or is it something else? When I look manually, the file isn't there.

---

### Post by ewing on 2007-05-12
what model is your scanner?
you need to do all the process like root

---

### Post by Princey on 2007-05-18
> **ewing said:**
> what model is your scanner?
you need to do all the process like root

I've got an HP ScanJet 4370. Sane says is uses the same drivers for the 3970 and other folks have reported that theirs work using the same backend drivers, ie 3970

---

### Post by Princey on 2007-05-18
Update. Deleted everything and did it as root, that is, using Sudo. Same message as before> emmjay@speedy1:~/sane-backends-1.0.18$ sudo cp ./backend/.libs/libsane-hp3900.so.1.0.18 /usr/lib/sane
cp: cannot stat `./backend/.libs/libsane-hp3900.so.1.0.18': No such file or directory


I also get errors when I type in > sudo make

I guess that's why it can't complete that final step. It's a long error message that I get.> emmjay@speedy1:~/sane-backends-1.0.18$ sudo make
making depend in include
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/include'
make[1]: Nothing to be done for `depend'.
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/include'
making depend in lib
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/lib'
makedepend -I. -I../include *.c 2>/dev/null
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/lib'
making depend in sanei
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/sanei'
makedepend -I. -I../include *.c 2>/dev/null
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/sanei'
making depend in backend
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/backend'
makedepend -I. -I. -I../include -I../include *.c 2>/dev/null
makedepend -a -o.lo -I. -I. -I../include -I../include *.c 2>/dev/null
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/backend'
making depend in frontend
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/frontend'
makedepend -I. -I. -I../include -I../include -I/usr/local/include *.c 2>/dev/null
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/frontend'
making depend in tools
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/tools'
makedepend -I. -I. -I../include -I../include *.c 2>/dev/null
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/tools'
making depend in doc
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/doc'
make[1]: Nothing to be done for `depend'.
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/doc'
making depend in po
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/po'
make[1]: Nothing to be done for `depend'.
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/po'
making all in include
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/include'
making all in lib
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/lib'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/lib'
making all in sanei
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/sanei'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/sanei'
making all in backend
make[1]: Entering directory `/home/emmjay/sane-backends-1.0.18/backend'
 gcc -c -g -O2 -W -Wall -DHAVE_CONFIG_H -I. -I. -I../include -I../include -D_REENTRANT -DPATH_SANE_CONFIG_DIR=/usr/local/etc/sane.d -DPATH_SANE_DATA_DIR=/usr/local/share -DPATH_SANE_LOCK_DIR=/usr/local/var/lock/sane -DV_MAJOR=1 -DV_MINOR=0 -DBACKEND_NAME=hp3900 -DLIBDIR=/usr/local/lib/sane hp3900.c  -fPIC -DPIC -o .libs/hp3900.o
In file included from hp3900_sane.c:55,
                 from hp3900.c:53:
hp3900_rts8822.c:67:37: error: tiffio.h: No such file or directory
In file included from hp3900_rts8822.c:75,
                 from hp3900_sane.c:55,
                 from hp3900.c:53:
hp3900_usb.c: In function 'Read_Bulk':
hp3900_usb.c:317: warning: format '%i' expects type 'int', but argument 4 has type 'size_t'
In file included from hp3900_sane.c:55,
                 from hp3900.c:53:
hp3900_rts8822.c: In function 'TIFF_Save':
hp3900_rts8822.c:13910: error: 'TIFF' undeclared (first use in this function)
hp3900_rts8822.c:13910: error: (Each undeclared identifier is reported only once
hp3900_rts8822.c:13910: error: for each function it appears in.)
hp3900_rts8822.c:13910: error: 'image' undeclared (first use in this function)
hp3900_rts8822.c:13913: warning: implicit declaration of function 'TIFFOpen'
hp3900_rts8822.c:13918: warning: implicit declaration of function 'TIFFSetField'
hp3900_rts8822.c:13918: error: 'TIFFTAG_IMAGEWIDTH' undeclared (first use in this function)
hp3900_rts8822.c:13919: error: 'TIFFTAG_IMAGELENGTH' undeclared (first use in this function)
hp3900_rts8822.c:13920: error: 'TIFFTAG_BITSPERSAMPLE' undeclared (first use in this function)
hp3900_rts8822.c:13921: error: 'TIFFTAG_SAMPLESPERPIXEL' undeclared (first use in this function)
hp3900_rts8822.c:13923: error: 'TIFFTAG_PHOTOMETRIC' undeclared (first use in this function)
hp3900_rts8822.c:13923: error: 'PHOTOMETRIC_RGB' undeclared (first use in this function)
hp3900_rts8822.c:13924: error: 'TIFFTAG_FILLORDER' undeclared (first use in this function)
hp3900_rts8822.c:13924: error: 'FILLORDER_MSB2LSB' undeclared (first use in this function)
hp3900_rts8822.c:13925: error: 'TIFFTAG_PLANARCONFIG' undeclared (first use in this function)
hp3900_rts8822.c:13925: error: 'PLANARCONFIG_CONTIG' undeclared (first use in this function)
hp3900_rts8822.c:13927: error: 'TIFFTAG_XRESOLUTION' undeclared (first use in this function)
hp3900_rts8822.c:13928: error: 'TIFFTAG_YRESOLUTION' undeclared (first use in this function)
hp3900_rts8822.c:13929: error: 'TIFFTAG_RESOLUTIONUNIT' undeclared (first use in this function)
hp3900_rts8822.c:13929: error: 'RESUNIT_INCH' undeclared (first use in this function)
hp3900_rts8822.c:13932: warning: implicit declaration of function 'TIFFWriteRawStrip'
hp3900_rts8822.c:13933: warning: implicit declaration of function 'TIFFClose'
make[1]: *** [hp3900.lo] Error 1
make[1]: Leaving directory `/home/emmjay/sane-backends-1.0.18/backend'
make: *** [all-recursive] Error 1


---

### Post by ewing on 2007-05-20
heres the file,
```
http://www.egoshare.com/3814af2389c22dac64b0943fd0ff2ba3/libsanehp3900so1018targz.html
```
I hope this will solve your problem ;)

---

### Post by Princey on 2007-05-20
> **ewing said:**
> heres the file,
```
http://www.egoshare.com/3814af2389c22dac64b0943fd0ff2ba3/libsanehp3900so1018targz.html
```
I hope this will solve your problem ;)

Thanks a million ewing!!! :popcorn: that did the trick. It now works perfectly \\:D/

---

### Post by couzin2000 on 2007-12-30
> **ayryq said:**
> Permissions are probably your problem still. To figure out which device is your scanner, open device manager:
System > Administration > Device Manager
The tree probably has several USB controllers, each with devices under them. Dig down until you find your scanner. Under your scanner is "USB Raw Device Access." Select this, and look at the Advanced tab on the right. One of the entries should be linux.device_file which will show you the filename for this device. On my system, my 3970 is /dev/bus/usb/001/002. Yours is probably different. So, on my system, I type in a terminal
```
sudo chmod a+w /dev/bus/usb/001/002
```
which does the trick for me.

Eric

First, sorry if I'm late in posting this. Second, thank you all for the nice work you've done in helping everyone find the missing link in making the HP Scanjet 3970 work! Mine works well...

However, I do want to point out I figured out another problem I had: *my scanner was connected to a USB self-powered hub*. 

I connected the scanner, and followed every instruction to a tee. Then I did the CHMOD on my scanner dev file, but I still got the same problem with permissions. This was because the** USB port on the hub ALSO needed to be CHMODded**. I figured out which device it was when I tried to run Xsane and got the same error but with addresses for device 001:006. I just went back and ran the same terminal command ```
sudo chmod a+w /dev/bus/usb/001/006
``` and all of it went perfectly fine after that. No more error messages!

Just make sure that you run permissions authorizations on all the devices in the line of connection - that should do the trick for you. Did for me!

---

### Post by figgles on 2008-02-05
All -- thanks to this thread, I checked out synaptic and the hp3900 drivers are there, pre-baked. I selected and applied the library and "viola" my scanner works! No need for chmod or downloading drivers outside of the updating manager's loving oversight.

---

### Post by skralljt on 2008-03-02
Here is what worked for me on 7.10 amd64 in xubuntu:
chmod a+w the /dev/usb/001/007 or whatever your device path is as reported in system information (for me applications>settings>hardware information)

install sane, xsane, libsane-extras (this is the one that did it for me and installed the driver, i know because it asked if it wanted to replace the one i compiled from the sourceforge 3900 driver that didn't work), sane-utils,  Don't bother with the sourceforge driver, the one in libsane-extras does better for me.

Finally I can use my scanner without installing a 300+MB "driver".  What gave HP the idea that 300 MB drivers are ok?  Who in their right mind wants to use their scanner software for organizing pictures?  /rant

---

### Post by Princey on 2008-03-31
As posted elsewhere, it now works once you install xsane in Hardy Heron. (using the beta version at the moment)

---

