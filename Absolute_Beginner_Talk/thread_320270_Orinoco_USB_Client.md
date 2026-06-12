---
title: "Orinoco USB Client"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by just_old_bob on 2006-12-17
Hi, brand new here and to Ubuntu/Linux.  I'm trying to get this working and have had no luck. I think that the drivers for the card itself are already in the kernel, it sure looks like it. However the USB part seems to be what is not working. I followed the instructions at

[http://folk.uio.no/oeysteio/orinoco-usb/install.html](http://folk.uio.no/oeysteio/orinoco-usb/install.html)

for extracting the firmware from windows drivers "Kernel 2.6.x and internet access through Windows"  about halfway down and it says to "Put orinoco_ezusb_fw in /usr/lib/hotplug/firmware/" which does not exist and so from some stuff I read I decided to put it in /lib/firmware/.  There was another file created 'orinoco_usb_fw.h', (header?). Where should it go?

I tried ndiswrapper with no luck. I can't post results from suggested commands because my only access is via this card/USB doohicky.

I'm getting very frustrated which is compounded by the fact that a 2006 edition book on Ubuntu I've been waiting for at the lie-berry was reported 'lost' by the bozo that checked it out last.

---

### Post by just_old_bob on 2007-01-08
Well I got it going. I just needed to find the correct source files and combine three “how tos” . 

I found the source files at [https://svn.sourceforge.net/svnroot/orinoco/branches/usb/](https://svn.sourceforge.net/svnroot/orinoco/branches/usb/). After screwing it up the first time I made sure to retain the directory structure and to make sure to save everything in a way that it kept it's file type as well. I'm sure a more knowledgeable person would have found a better way, but for everything except the source and headers I opened the file with firefox and chose “save page as”. After that it was pretty simple.

I've done this two ways just to make sure it works both ways and that the computer did not have to be on line at the time of the install. 

The firmware extraction utility that I found with the good source files required me to be on line when I ran the script. I found another one that allows downloading the firmware extractor and windows drivers from windows (or any other way) so does not require you to be online while running it.

For the second way the needed files  can be found at [http://folk.uio.no/oeysteio/orinoco-usb/get_ezusb_fw](http://folk.uio.no/oeysteio/orinoco-usb/get_ezusb_fw) for the firmware utility and [ftp://ftp.avaya.com/incoming/Up1cku9/tsoweb/avayawireless/AV_WINXP_PC_USB_SR0201.zip](ftp://ftp.avaya.com/incoming/Up1cku9/tsoweb/avayawireless/AV_WINXP_PC_USB_SR0201.zip) for the windows driver. I just downloaded them into a directory by themselves.

The first (on line) method to extract the firmware:

Entered the firmware directory within the orinoco-usb directory and ran the script.
```
 sudo sh get_ezusb_fw
```
It downloaded the windows driver and extracted the firmware from it. I copied it to /lib/firmware. I didn't do anything with the orinoco_usb_fw.h file. 
```
sudo cp orinoco_ezusb_fw /lib/firmware
```
Since my only connection is wireless I had to hang my computer out the window so my PCI card could get a signal. I think you can see why I wanted to find another way.

The second (off line) method to extract the firmware was the same as the first except that it was in whole different directory, didn't have to download the windows driver and was of course off line.

After that it was the same. Went to the orinoco-usb directory and ran make and make install.
```
sudo make
sudo make install
```
When it was done, (no errors—finally) I just restarted my computer and configured the connection in Networking.

The firmware directory has extraction utilities for more than just the Hermes chipset.

I did it both ways on two different computers, that is of course if you consider the minimal working innards laid out on a table a computer. If anyone had some tips on how I could have done it more efficiently, I would sure appreciate them.

Oh yeah, I still wanna find the SOB that stole that book from the library.

---

### Post by deadgobby on 2007-01-09
> **just_old_bob said:**
>  Oh yeah, I still wanna find the SOB that stole that book from the library.
 The Hamburgler from MC Donalds stole it. Sorry could not resist that. :mrgreen: 
GObby

---

### Post by caldorean on 2008-05-09
Hi, I know this is a few years later but still, been trying to get this card to work with the USB connection, but when I try to make the driver 
it replies with:

> sudo make
make -C /usr/src/linux-headers-2.6.22-14-generic M=/home/caldorean/orinoco-0.15 KERNELRELEASE=2.6.22-14-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
/home/caldorean/orinoco-0.15/Kbuild:34: *** Wireless extensions are not enabled.  Stop.
make[1]: *** [_module_/home/caldorean/orinoco-0.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2


I know it's an old card, but it would still be fun to get it to work properly..

---

