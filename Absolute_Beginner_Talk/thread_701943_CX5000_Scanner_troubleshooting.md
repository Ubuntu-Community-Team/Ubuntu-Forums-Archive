---
title: "CX5000 Scanner troubleshooting"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-02-19
I posted earlier today about an Epson CX5000 all-in-one. Gutsy found the printer, once the usb cable was connected. It prints. Well, it printed a test page.

GIMP can't find the scanner.

Similar posts about this device as a scanner are 2 and more years old, as in this post

[http://ubuntuforums.org/showthread.php?t=576594&highlight=recent+epson](http://ubuntuforums.org/showthread.php?t=576594&highlight=recent+epson)

which asks for installing of:

sane sane-utils libsane-extras

before I try this post from June 2005, is this necessary? I'm OK with adding the sane stuff, but is there a better way. Damn, I know I'm short on facts here, but I'm begging, a little help, please. It says to go to Device Manager in System/Administration. kinda outta date.

My former scanner, an Epson Perfection 1250 has worked without adding anything. That is, Once gutsy was installed, the 1250 worked.

---

### Post by Jewfro_Macabbi on 2008-02-19
I think the current packages you'll need are just sane and xsane. It's perfectly fine to install these - you cannot scan without them. 

I'm not familiar with your particular printer - but w/my all in one unit scanning only works if the printer is connected via network/ethernet

---

### Post by kriukov on 2008-02-19
Please read [http://ubuntuforums.org/showthread.php?t=38445](http://ubuntuforums.org/showthread.php?t=38445)

It helped me today and my scanner worked (though from root so far). I also have CX5000 all-in-one.

---

### Post by Jewfro_Macabbi on 2008-02-19
Try adding yourself to the group scanners.

---

### Post by Mark_in_Hollywood on 2008-02-20
> **Jewfro_Macabbi said:**
> Try adding yourself to the group scanners.

HUh?

mark@Lexington-19:~$ sudo adduser mark scanners
[sudo] password for mark:
adduser: The group `scanners' does not exist.

---

### Post by Mark_in_Hollywood on 2008-02-20
> **kriukov said:**
> Please read [http://ubuntuforums.org/showthread.php?t=38445](http://ubuntuforums.org/showthread.php?t=38445)

It helped me today and my scanner worked (though from root so far). I also have CX5000 all-in-one.

From:
HOWTO: Setup the Epson CX6600
[http://ubuntuforums.org/showthread.php?t=38445](http://ubuntuforums.org/showthread.php?t=38445)

I have a "default" Ubuntu Gutsy Gibbon v. 7.10 verson on this drive. 

First, I installed sane. Strange it wasn't there. Then I looked to see if xsane needed installation. It was already installed. go figure. Reboot to load sane.

I then read: [http://www.clasohm.com/blog/one-entry?entry%5fid=12616](http://www.clasohm.com/blog/one-entry?entry%5fid=12616) and [http://www.freecolormanagement.com/sane/libusb.html](http://www.freecolormanagement.com/sane/libusb.html), which the HOWTO links into.  Not seeing anything in those two posts that would lead me another way, I returned to the Ubuntu post HOWTO. 

It calls for modifying:  sudo gedit /etc/hotplug/usb/**libsane.usermap**

which returns an empty file. As the HOWTO says the file has stuff in it, I cd /etc/hotplug/usb and 

mark@Lexington-19:/etc/hotplug/usb$ ls
libmtp.sh  libmtp.usermap

NO libsane.usermap to be found there.

Out of curiosity I tried:

mark@Lexington-19:~$ sane find-scanner
bash: sane: command not found

mark@Lexington-19:~$ sudo sane find-scanner
[sudo] password for mark:
sudo: sane: command not found

and lsusb

Bus 001 Device 006: ID 04b8:082b Seiko Epson Corp. 

So I am stopped before starting. Anybody got a CLUE?

---

### Post by Mark_in_Hollywood on 2008-02-20
I have it working! Hooray!

Hours of fiddling later:

From:

Setup of Epson Stylus DX6050 multifunctional  ([http://ubuntuforums.org/showthread.php?t=599673](http://ubuntuforums.org/showthread.php?t=599673))

I did not and could not follow all the instructions as I was uncertain I could.

I did do the following and the scanner started working.

lsusb | grep Epson

which for an Epson Stylus CX5000 3-in-1, returned:

Bus 001 Device 008: ID 04b8:082b Seiko Epson Corp.

Next:

gksugo gedit /etc/udev/rules.d/45-libsane.rules

and at the bottom of that file I added:

SYSFS{idVendor}=="04b8",SYSFS{idProduct}=="082b",M ODE="664",GROUP="scanner"

the above as one line (even though the files lines of code were sometimes in more than one line

Saved the file. Exited.

Next:

gksudo gedit /etc/sane.d/epson.conf

and added:

usb 0x04b8 0x082b

saved and exited that file.

Next:

for my scanner sitting on the USB bus so:

sudo chmod a+w /dev/bus/usb/001/008

and next:

scanimage -L

scanned an image. Then under GIMP, the device dialog found the scanner.

---

