---
title: "EPSON 660 Scanner - Error during device IO"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by LuftFan on 2007-12-17
I have given this problem the time and effort I can afford.  I have even waited for 7.10 (plus a few months) with the hope that the problem would have been solved since Feisty. I installed Gibbon today, same issue.

On opening XSane and selecting Epson Scanner I get this error message:

[COLOR="Red"]"Failed to open device 'snapscan:libusb:001:006': Error during device I/O."[/COLOR]

The following information I can add:

[COLOR="Blue"]gjohanl@Ubuntu7:~$ scanimage -L
device `v4l:/dev/video0' is a Noname Logitech QuickCam IM/Connect  virtual device
device `snapscan:libusb:001:006' is a EPSON EPSON Scanner flatbed scanner[/COLOR]

Also

[COLOR="Blue"]gjohanl@Ubuntu7:~$ scanimage -L
device `v4l:/dev/video0' is a Noname Logitech QuickCam IM/Connect  virtual device
device `snapscan:libusb:001:006' is a EPSON EPSON Scanner flatbed scanner[/COLOR]

Also, this excerpt from sane-find-scanner -v
[COLOR="Blue"]found USB scanner (vendor=0x04b8 [EPSON], product=0x0114 [EPSON Scanner]) at libusb:001:006
found USB scanner (vendor=0x046d, product=0x08d9) at libusb:001:005[/COLOR]


Finally, from other thread ([http://ubuntuforums.org/archive/index.php/t-26911.html](http://ubuntuforums.org/archive/index.php/t-26911.html)) I've done this:
[COLOR="Blue"]gjohanl@Ubuntu7:~$ sudo gedit /etc/sane.d/snapscan.conf[/COLOR]

Changed to
[COLOR="Blue"]firmware /etc/sane.d/ESFW30.BIN[/COLOR]

Having read more and more over the months I've realised that some have had success with reloading the kernel without the USB_Suspend.  From [http://ubuntuforums.org/archive/index.php/t-26911.html](http://ubuntuforums.org/archive/index.php/t-26911.html) 

"USB selective suspend/resume and wakeup (EXPERIMENTAL) (USB_SUSPEND)" that is enabled in the Feisty kernel. If you recompile the kernel with this option disabled then you will be able to scan normally again. Even better, if you compile the 2.6.21 vanilla kernel with this enabled things will work as they should. There was a bug in the 2.6.20 kernel that has been fixed."
___________________

[COLOR="Blue"]gjohanl@Ubuntu7:~$ uname -r
2.6.22-14-generic[/COLOR]

Surely this should have been fixed in 7.10?  Recompiling kernel is well above my technical ability and now I need step by step help.  Any takers?

Oh - the green light goes on and the scanner works beautifully in Win2K.

Thank you in advance for your help.

Regards

LuftFan

---

### Post by dstew on 2007-12-17
According to the SnapScan site, the firmware file for the Epson 660 is named tail_058.bin. The file ESFW30.BIN is specific for the Epson 1670.
See [http://www.chinwong.com/index.php/site/article/epson_scanning_on_linux/](http://www.chinwong.com/index.php/site/article/epson_scanning_on_linux/)

---

### Post by LuftFan on 2007-12-20
Thank you!

This might by an obvious error on my side.  I'll give it a try.

LuftFan

---

