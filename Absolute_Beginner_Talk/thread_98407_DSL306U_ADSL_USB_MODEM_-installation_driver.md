---
title: "DSL306U ADSL USB MODEM -installation driver"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by slashlink on 2005-12-03
HI

I just installed ubuntu yesterday and I have no idea how linux works. I am a window guy. So, please patient with me.

I am using [DSL306U]("http://www.aztech.com.sg/DSL-306U.htm") modem and I have no idea how to install and use it. 

I have the modem driver CD and under the file LINUX there are 3 rpm files:
[IMG]http://i7.photobucket.com/albums/y288/lifg/archive/desktophelp.jpg[/IMG]

and a readme.txt file :
> This document describes the steps of installing the E2 or Hasbani on the Linux.
Driver Version 062802_REL1.4.

1) Installing.
	
	Redhat 7.1:
		#rpm -i USBENDPOINT-1.4-2_Redhat7.1.i386.rpm

	Redhat 7.2:
		#rpm -i USBENDPOINT-1.4-2_Redhat7.2.i386.rpm

	Redhat >= 7.2:
		#rpm --rebuild USBENDPOINT-1.4-2.src.rpm
		#cd /usr/src/redhat/RPMS/i386
		#rpm -i USBENDPOINT-1.4-2.i386.rpm
	
	Mandrake :
		#rpm --rebuild USBENDPOINT-1.4-2.src.rpm
		#cd /usr/src/RPM/RPMS (Notes: the binary format RPM 
			should locate in one of its subdirectory according to your CPU type.)

		Find the binary RPM package, and execute the following command:
		#rpm -i USBENDPOINT-1.4-2.ixxx.rpm

	The driver should be installed in directory "/usr/local/e2/".

2) Working.
	#cd /usr/local/e2
	#insmod e2.o
	#dhcpcd hsb0 (Note: Run this command after the ready LED begins to blink.)

3) Upgrading the E2 firmware.
	cp NewFirmware.bin /etc/CnxE2Fw.bin (Note: file name should be case sensitive.)

4)Uninstalling
	#rpm -e USBENDPOINT

I tried to useterminal and follow the instruction above but I unsuccessfully. I also tried to double click the rpm file but can't open the file.

Dont know what to do. please help.. thanks

---

### Post by Jason7fd on 2006-01-31
I have the same problem with you but I think i have found the solution(didn't test it yet)
**Convert .RPM to .DEB**
> sudo alien USBENDPOINT-1.4-2.src.rpm

**Installation**
> sudo dpkg -i USBENDPOINT-1.4-2.src.deb

---

