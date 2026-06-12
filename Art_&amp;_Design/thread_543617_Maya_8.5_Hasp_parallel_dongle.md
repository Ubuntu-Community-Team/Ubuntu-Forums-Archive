---
title: "Maya 8.5 Hasp parallel dongle"
date: 2007-09-05
forum: Art &amp; Design
---

### Post by fordey42 on 2007-09-05
Installed Maya on my Ubuntu workstation, seems to have installed ok, but fails to load.  I get the Welcome to Autodesk screen up, saying no appropriate licenses installed on this machine.  I know this not to be true  because it works on my windows machine.  

I think the problem is with the Hasp parallel dongle, Ubuntu is not seeing it.  If I work through the Autodesk screen and point it to the license, i get the error the file contains invalid data, again this is not true.

So anyone know a fix

#-o

---

### Post by cepogue on 2007-11-20
I had the same issue using a dongle for some forensic software.  This worked for me for Gutsy in a VMware session...

1. Make sure your version of Ubuntu has all of the latest patches.  Run the update manager from the top right hand corner of the screen.  The icon looks like
a sun in a small orange box.

2. Open a shell (Applications - Accessories - Terminal)

3. sudo apt-get update

4. You are now going to install a utility called Alien.  It will allow you to convert Redhat Package Manager (RPM) files into Debian package (DEB) files.

5. sudo apt-get install alien (make sure that you still have the Ubuntu dvd .iso mapped to a cdrom.
	MAC (can be done while VM is powered on) Virtual Machine - Settings - CD/DVD - Use disk image - map to image
	Win (VM has to be powered off) VM - Settings - Add - CD/DVD - Use .iso - Map tp ISO

6. Download the RPM HASP drivers from:
[http://www.aladdin.com/support/hasp/hasp4/linuxdrv.aspx](http://www.aladdin.com/support/hasp/hasp4/linuxdrv.aspx)
   Under the tab labeled, "Device Drivers for USB and parallel port HASP keys", download "HDD_RPM_RedHat_i386_AllDrv.tar.gz"
	The file will be downloaded to your desktop.../home/username/Desktop

7. Move the tarball to /tmp
	cp *.gz /tmp

8. unpack the tarball
	tar -xzvf *.gz

9. cd to the new directory
	cd HDD*

10. change the RPMs to DEBs
	alien -k aksparlnx-redhat-1.05-1-i386.rpm
	alien -k aksusbd-redhat-1.5-1.i386.rpm

11. Install the DEBs
	sudo dpkg -i name-of-deb-file.deb

12. mount the usbfs filesystem
	mount -t usbfs none /proc/bus/usb

13. start the aksusbd service
	/usr/sbin/aksusbd

14. Plugin the HASP dongle

15. You should be good

Good Luck...

Chris

---

