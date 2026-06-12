---
title: "how to install addlogix usb dongle wifi drivers from CD?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by neatokino on 2007-12-17
I bought an addlogix wireless-G usb network adaptor, which comes with Linux drivers on a CD (the box says that the dongle is Linux-Redhat v7.1 and later compatible).

I didn't know how to install the linux drivers from the CD, but I tried to just 'plug and play' the device, and it worked pretty well... at first.   Although the wifi adaptor worked out of the box for a while, it started dropping signals badly, which had also been a problem with my previous wifi adapter, a netgear WG111.

Since the addlogix device comes with Linux drivers, I thought they might solve the problem.  But I don't know how to install them.

there are two 'linux' driver files on the cd

1) RT73_Linux_STA_Drv1.0.3.6.tar.gz

2) RT25USB-SRC-V2.0.7.0.tar.gz

Can anyone tell me how to install them?  Do I need both?  Is there any reason to believe they'll work better than the drivers that are already on Gutsy?  Having the signal drop the way it did with the built-in Gutsy drivers is pretty lousy, so I hope these files from the cd will help.

The adapter comes with no Linux-related instructions, only Mac and Windows.

TIA
Michael

---

### Post by rkd on 2007-12-18
I don't know anything about installing those particular drivers, but I can suggest that you expand the .tar.gz files they gave you and see whether there is a text file with installation instructions in them somewhere.

In case you aren't familiar with expanding those files, you can do it by copying those .tar.gz files to your hard disk, opening a terminal, using cd to get to the directory where you put the files, then entering the command:

tar xvzf <name of file>

There probably is a way to do the expansion from the GUI, but I'm too new with Linux to know how to do that.

Once you have expanded the files, you should find it created directories matching the names of the files (without the .tar.gz).  Look in those directories for README files, or any other files whose names make you think they might have installation instructions.

I can't guarantee there are instructions there, but it should be easy for you to check.  Good luck!

---

### Post by neatokino on 2007-12-18
Thanks for your help!  I was able to extract the folders and read the 'read me' files, but the instructions for compiling the drivers are too complicated for me to figure out, so I guess I'm out of luck.  

The dongle sort of works 'out of the box,'  but it drops the signal randomly, and once the signal starts dropping, I have to unplug the adapter, then plug it back in, then wait and pray a lot, and sooner or later have to restart.  That's not a great situation.  This seems to be an issue with wifi adapters and Ubuntu.

If anyone can help me decipher the instructions to compile and configure, please feel free!!! 

Here they are:

===============================================================================================
ModelName:
===========
RT2500USB

===============================================================================================
Driver lName:
===========
rt2570.ko

===============================================================================================
Ralink Hardware:
===========
Ralink 802.11b/g wireless network card.

===============================================================================================
Description:
=============
This is a linux device driver for Ralink RT2500USB b/g WLAN Card.
This driver implements basic 802.11 function. 
Infrastructure and Ad-hoc mode with open or shared or wpapsk or wpa2psk authentication method.
WEP-40 and WEP-104 or tkip or aes encryption. 


===============================================================================================
Compatibility:
===================
Testing has been done with LinEX kernel 2.6.9, Fedora Core 3.
You may encounter some rough edges when working with recent other Linux kernels branch.


===============================================================================================
FILE LAYOUT:
=============
*.c		    : c files
*.h		    : header files                   
Makefile.6		:Makefile for kernel 2.6
Makefile.4		:Makefile for kernel 2.4
./LINUX_RACONFIG_Vx.x.x.x  : source code for utility RaConfig2500 version x.x.x.x
./LINUX_RACONFIG_Vx.x.x.x/bin/LINUX/RaConfig2500  : utility RaConfig2500

===============================================================================================
Build Instructions:  
====================
0) $dos2unix *
      $chmod 644 *
      $chmod 755 Configure

1) cp Makefile.x Makefile               // x is your kernel

2) $make
3) $insmod rt2570.ko     # Insert driver module
4) $ifconfig rausb0 up  # Bring up device 
5) $dhclient rausb0  # Get network IP address

  Note: Script functionality:
  Configure       retrive linux version 
6) ./LINUX_RACONFIG_Vx.x.x.x/bin/"Linux"/RaConfig2500

if lack of libstdc++.so.6, cp ./LINUX_RACONFIG_Vx.x.x.x/libstdc++.so.6 /usr/lib

7)Edit(or add the line) in /etc/modules.conf
   alias rausb0 rt2570

8) Create and edit 'ifcfg-rausb0' file in /etc/sysconfig/network-script/
   DEVICE='rausb0'
   ONBOOT='yes'
   BOOTPROTO='dhcp' 

===============================================================================================
CONFIGURATION:  
====================
RT2500 driver can be configured via following interfaces, 
i.e. i)RaConfig2500, ii)wireless extension,
i) RaConfig2500 is utility for rt25usb.

ii)  Wireless extension usage please refer to man page of 'iwconfig', 'iwlist' and 'iwpriv'. 
     Here is definition for private command 'iwpriv'
-------------------------------------------------------------------------------------------------------
NAME
       iwpriv - configure optionals (private) parameters of a wireless network
       interface
	
SYNOPSIS
       iwpriv [interface]
       iwpriv [interface] [parameters] [val]


DESCRIPTION 
[interface]      [parameters]             [val]                    explaination
-----------    -----------------     ----------------         --------------------------------
rausb0		    auth		  1~5			 1:Open
								 2:Shared
								 3:WPAPSK
								 4:WPA2PSK
								 5:WPANONE
								
rausb0		    psm		  	  0~1			 0:Continuous wake up
								 1:power safe mode

rausb0		    enc			  1~4			 1:none
								 2:wep
								 3:tkip
								 4:aes
								
rausb0		    wpapsk		  8~64 chars		 WPAPSK password


===============================================================================================
EXAMPLE:  
====================
Example I: Config STA to link with AP and OPEN/NONE(Authentication/Encryption)
	1. iwconfig rausb0 mode Managed
	2. iwconfig rausb0 key off
	3. iwconfig rausb0 essid "AP's SSID"

Example II: Config STA to link as Ad-hoc mode and OPEN/NONE(Authentication/Encryption)
	1. iwconfig rausb0 mode ad-hoc
	2. iwconfig rausb0 key off
	3. iwconfig rausb0 essid "Desired SSID"
	
Example III: Config STA to link with AP and OPEN/WEP(Authentication/Encryption). 
            Default Key ID = 3
	1. iwconfig rausb0 key [3]
	2. iwconfig rausb0 key s:abcde
	3. iwconfig rausb0 essid "AP's SSID"
	
Example IV: Config STA to link with ad-hoc mode and WPAPSK/TKIP(Authentication/Encryption)
            WPA PreShared-Key is 12345678
        1. iwconfig rausb0 mode ad-hoc
        2. iwpriv rausb0 auth 4
	3. iwpriv rausb0 enc 3
	4. iwconfig rausb0 essid "Desired SSID"
	5. iwpriv rausb0 wpapsk 12345678
	6. iwconfig rausb0 essid "Desired SSID"
	
Example V: Config STA to link with AP and WPAPSK/AES(Authentication/Encryption)
            WPA PreShared-Key is 12345678
	1. iwpriv rausb0 enc 4
	2. iwpriv rausb0 auth 3
	3. iwconfig rausb0 essid "AP's SSID"
	4. iwpriv rausb0 wpapsk 12345678
	5. iwconfig rausb0 essid "AP's SSID"
	
Example VI: Config STA to link with AP and WPA2PSK/TKIP(Authentication/Encryption)
            WPA PreShared-Key is 12345678
	1. iwpriv rausb0 enc 3
	2. iwpriv rausb0 auth 4
	3. iwconfig rausb0 essid "AP's SSID"
	4. iwpriv rausb0 wpapsk 12345678
	5. iwconfig rausb0 essid "AP's SSID"
	
p.s Step 2 is part of generating wpapsk password and is necessary.

---

### Post by rkd on 2007-12-18
I believe you are right that those are the instructions for compiling and installing the driver.  They make some sense to me, but I have a feeling that these might not be the instructions intended for you and me, but for other programmers.

So far, I'm only an Ubuntu observer.  I'm a professional programmer on mainframes and some on Windows, but nothing so far on Linux.  If no one else joins this thread to help out, I think I could coach you through compiling and installing that driver, but it would be slow, and we might make several mistakes along the way. If you'd like to proceed on those terms, I'm willing to give it a try.  Post a reply to say whether you want to try that course.  If so, I'll take a little more time to study the directions, then post with what I think the first steps you need to do are.

---

### Post by neatokino on 2007-12-21
Hi RKD--

Thanks for your offer!  I'm currently out of town, away from my desktop computer, but when I'm back home in a couple of weeks I may very well take you up on your offer, which I very much appreciate.

I also can't figure out which of the two drivers that are on the CD (one is a 2500 the other a 73) is the one I need.  I will definitely check back in with you when I'm back home.

Thanks!

Michael

---

