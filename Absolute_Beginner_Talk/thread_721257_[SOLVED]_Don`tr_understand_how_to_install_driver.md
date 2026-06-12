---
title: "[SOLVED] Don`tr understand how to install driver"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by nothingspecial on 2008-03-11
Someone in these forums has kindly posted a tar file that is a driver for a webcam. There are instructions in a read me file included. I don`t understand them propperley. 
The file has been extracted to my desktop. Should it be there? I also don`t understand the bit about the kernel or interface headers:confused:
I especially don`t understand this bit 
"make KDIR=/path/to/kernel"
  If someone has a few spare minutes, could they give me step by step instructions on how to do this. If you could also explain what I`m doing in each step I would be eternally grateful. Also I won`t have to ask next time.:)
Here are the instructions - 


Ricoh R5U870 Linux Driver
Version 0.10.0, 2007/4/7

Requirements
============

To build/install this driver, you must have a set of configuration and
interface headers, or the complete build directory, for your running kernel,
or the target kernel for which the driver is to be built.  This should
include most files in the include/linux directory, and specifically
include/linux/autoconf.h and include/linux/version.h.

The required interface headers are usually located at or symlinked from:
/lib/modules/<version>/build

Your kernel must be 2.6.17 or newer.


Supported Hardware
==================

This driver supports the following OEM webcams:

05ca:1810 HP Pavilion Webcam - UVC
05ca:1830 Sony Visual Communication Camera VGP-VCC2 (for VAIO SZ)
05ca:1832 Sony Visual Communication Camera VGP-VCC3 (for VAIO UX)
05ca:1833 Sony Visual Communication Camera VGP-VCC2 (for VAIO AR1)
05ca:1834 Sony Visual Communication Camera VGP-VCC2 (for VAIO AR2)
05ca:1835 Sony Visual Communication Camera VGP-VCC5 (for VAIO SZ)
05ca:1836 Sony Visual Communication Camera VGP-VCC4 (for VAIO FE)
05ca:183a Sony Visual Communication Camera VGP-VCC7 (for VAIO TZ)
05ca:1870 HP Pavilion Webcam / HP Webcam 1000


Installation Process
====================

To attempt to build against the running kernel:

make

To build against a specific kernel:

make KDIR=/path/to/kernel

To install the modules to the appropriate location:

make install

-or-

make install KDIR=/path/to/kernel

Installed modules will be automatically probed for supported devices by the
udev coldplug component at boot, and the driver should be automatically
loaded on subsequent reboots.

NOTE: Previous releases of this driver have produced modules named
ry5u870.ko.  With the current release, the module name was changed to
r5u870.ko.  Ensure that any old versions are deleted after installing a
new version.


Loading the Driver
==================

If you installed the driver, you can just run:

modprobe r5u870

If you wish to load the driver without installing it, you must load the
prerequisite modules:

modprobe videodev
modprobe video-buf
modprobe v4l1-compat
modprobe v4l2-common
modprobe compat_ioctl32		(on 64-bit platforms)

You must also copy the microcode files (r5u870_*.fw) to /lib/firmware.

Then you may load the module manually:

insmod r5u870.ko


Driver Options
==============

Below is a list of module parameters that may be used with the r5u870 module:

dv1000 -- HP Webcam handling mode
	HP has done it again and used ID 05ca:1870 for two distinct pieces
	of hardware: the HP Webcam 1000, found in HP Pavilion dv1000 series
	machines, and the HP Pavilion Webcam, found in other HP Pavilion
	machines that don't have Microdia cameras, and don't have the 
	05ca:1810 Ricoh UVC camera -- which is not actually any different 
	from the 05ca:1870 HP Pavilion webcam.  These two devices have
	different image sensors and require different microcode.
	0: Assume HP Pavilion Webcam
	1: Assume HP Webcam 1000
	2: Check DMI product name field (DEFAULT)

video_nr -- list of favored minor numbers
	A list of video capture minor numbers (/dev/videoX) to try to
	associate devices with, in order, before resorting to the first
	available minor number.

debug -- bit field integer
	Set bits described in usbcam.h (USBCAM_DBG_XXX) to enable trace
	messages.

fixed_fbsize -- integer
	Sets the size in bytes of fixed-length frame buffers.  The default
	value is 1MB.  This is a compatibilty feature for buggy programs
	that use the V4L1 VIDIOCGMBUF call to allocate a frame buffer
	based on the current capture size, choose a larger capture size,
	and then attempt to capture frames.


Bugs
====

Send bug reports to [email]samr7@cs.washington.edu[/email]

Kopete 0.12 and earlier can be used with this driver, but colors may appear
distorted.  This is a problem with Kopete's YUV decoder, and should be fixed
in a future version.  Kopete may also set the gamma picture control to 0
for no apparent reason, causing the image to appear too dark to Kopete and
to other applications that subsequently open the camera.


Copyright and License
=====================

Copyright (C) 2007 Sam Revitch <samr7@cs.washington.edu>

This driver is licensed to you under the terms of the GNU GPL v2.  See
the included file 'COPYING'.

The Makefile and Kbuild components are derived from the ivtv project.

The files:
	r5u870_1810.fw
	r5u870_1830.fw
	r5u870_1832.fw
	r5u870_1833.fw
	r5u870_1834.fw
	r5u870_1835.fw
	r5u870_1836.fw
	r5u870_1870.fw
	r5u870_1870_1.fw

were derived from usbsnoop/sniffusb tracing of various Windows drivers, 
including some named Mvc25u870.sys, 5U870CAP.sys, and R5U870FLx86.sys.


Acknowledgements
================

Thanks to Geert Willems for extensive testing and bug reporting, for general
driver issues and issues specific to the HP Webcam.

Thanks to Beno&#65533;t Canet for updating this driver to work with the Sony VAIO
AR webcam (05ca:1834).


Any help will be gratefully appreciated.

---

### Post by chewearn on 2008-03-11
Firstly, can you post the link to where you obtain the tar file?  This is so I can follow along the same instruction on my PC.  In case you encounter error, I might see the same thing, and it will be easier to help.

Secondly, the instructions itself.  I am assuming you are running Ubuntu (with Gnome desktop).

1. Open a command terminal: Top Panel Menu > Applications > Accessories > Terminal

2. Install all tools needed for this.  Run this command:
```
sudo aptitude install build-essential
```

3. Untar the file in a subdirectory, under your home directory.

4. Navigate to that subdirectory (replace <subdir> below):
```
cd ~/<subdir>
```

5. Build the module:
```
make
```

I think you can omit the parameter KDIR; the default should already be correct for ubuntu. 

6. Install the module:
```
sudo make install
```

7. Activate the module:
```
sudo modprobe r5u870
```

8. Test the webcam. I don't have the hardware itself, so you have to figure this out.

9. Make the module load at start-up:
```
gksu gedit /etc/modules
```

The text editor will pop-up with the /etc/modules file.  Add "r5u870" as a single line at the bottom of the file.  Save and exit.

10. Restart

11. Check that the module has been loaded:
```
lsmod | grep r5u870
```

That's it.  Post any error messages encountered.

---

### Post by nothingspecial on 2008-03-11
Absolutely brilliant. Thankyou. Here`s the link - 
[http://ubuntuforums.org/showpost.php?p=3489801](http://ubuntuforums.org/showpost.php?p=3489801)
One question - When you say this -
4. Navigate to that subdirectory (replace <subdir> below):
Code:

cd ~/<subdir>

If I extracted the file to my desktop, is the command

cd ~/Desktop

---

### Post by nothingspecial on 2008-03-11
Figured it out -
 cd ~/Desktop/r5u870-0.10.0-tz17
Thanks eveything`s working

---

### Post by send2toonie on 2008-03-15
Hi, many thanks for posting this how to, with this i've made the most headway to getting the webcam working, but its still not perfect.

Here's the issue, i've followed the steps, then installed Camorama to test.  Its showing a picture now, yay! But the picture is looking all screwy: i'll try to describe it, its showing 1 1/2 picture (full picture and beside it on the right half of the same image) and its in black and white but very streakly (with vertical lines).

any ideas?

---

### Post by Shazaam on 2008-03-15
Can't help you with the cam but I can give you a tip for future source installs. Install checkinstall with Synaptic. Then when you want to install from source you would substitute this....
```
sudo make install
```
with this......
```
sudo checkinstall
```
This will make a .deb package making it easier to uninstall the program later.

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by send2toonie on 2008-03-16
i think it was a camorama issue, because amsn handled webcam perfectly.  thanks.

---

