---
title: "Dell Printer Help"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by NeverKnovvsbestt on 2006-06-14
I have just recently changed my operating system over to ubuntu and I am having trouble getting my printer to work. It is a Dell Photo Printer 720. Any help would be much appreciated.

:)

---

### Post by The Darkness on 2006-06-14
It is actually a rebadged Lexmark z600 series (probably a z615).
You should be able to get a Linux driver for it from Lexmark.

After installing the driver, I would reboot your Linux box and then try going at it again.

---

### Post by NeverKnovvsbestt on 2006-06-14
I went to the Lexmark website and they gave me a file called CJLZ600LE-CUPS-1.0-1.TAR.gz, but I'm not sure how to install it... :confused:

---

### Post by givré on 2006-06-14
[http://www.ubuntuforums.org/showthread.php?t=49714](http://www.ubuntuforums.org/showthread.php?t=49714) ;) 
Worked great for me

---

### Post by NeverKnovvsbestt on 2006-06-14
when I try to install the z600 executable file as a driver in System > Administrator > Printing it says: Only files ending with .ppd or .ppd.gz will be installed.

---

### Post by givré on 2006-06-15
[http://www.ubuntuforums.org/showthread.php?t=49714](http://www.ubuntuforums.org/showthread.php?t=49714)

You will not be able to install it like that, it's a driver made for redhat originaly, so follow this howto

---

### Post by NeverKnovvsbestt on 2006-06-15
I followed the tutorial up to the point where it says to type:

$ cd /usr/lib/cups/backend
$ ./z600

and I should get:

direct z600:/dev/usb/lp0 "Lexmark Lexmark Z600 Series" "Lexmark Printer"

but I don't.

Then It says:

If you get no output, mount the usb filesystem.
Add this to your /etc/fstab file:
usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0
Then just type: sudo mount usbfs. That should fix it.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Im not clear on how to do this last step. How do you mount the usb filesystem so that I can make the change?

---

### Post by givré on 2006-06-15
ok, so edit first your /etc/fstab
```
sudo gedit /etc/fstab
```
at the end of the file, add
```
usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0
```
close gedit, and mount what you just add with
```
sudo mount usbfs
```
mount will look at your fstab to get the good option.

But don't expect to have something with ./z600, it seams that there were a lot of change between breezy and dapper.
restart cups and try to add your printer

---

### Post by NeverKnovvsbestt on 2006-06-15
Awsome, thanks for all the help!!!:D

---

