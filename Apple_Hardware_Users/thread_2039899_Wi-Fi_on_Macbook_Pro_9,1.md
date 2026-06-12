---
title: "Wi-Fi on Macbook Pro 9,1"
date: 2012-08-09
forum: Apple Hardware Users
---

### Post by Fi5hy on 2012-08-09
I painstakingly spent about 3 days getting a triple-boot working and all the apps I wanted installed on my new Macbook Pro, and so far most things are working just fine, but wi-fi and one other thing aren't working. Any suggestions?
I'm not really sure what to provide here, if you need any more information, just let me know.

---

### Post by Fi5hy on 2012-08-14
Bump...

---

### Post by CrazyDymond88 on 2012-08-14
Hey there, I managed to get the wifi working by following this post [http://ubuntuforums.org/archive/index.php/t-1987927.html](http://ubuntuforums.org/archive/index.php/t-1987927.html)


Run the following in the terminal:
$ sudo apt-get install b43-fwcutter firmware-b43-installer
$ sudo dpkg-reconfigure firmware-b43-installer
response from terminal:
$ No chroot environment found. Starting normal installation
$ Unsupported device(s) found: PCI id 14e4:4331 
Aborting.

then run:
$ sudo modprobe b43
$ export FIRMWARE_INSTALL_DIR="/lib/firmware"
$ cd ~\Downloads
$ wget [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2) $ tar -xjf broadcom-wl-5.100.138.tar.bz2
$ sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" broadcom-wl-5.100.138/linux/wl_apsta.o

You'll get a response like this:
This file is recognised as:
filename : wl_apsta.o
version : 666.2
MD5 : e1b05e268bcdbfef3560c28fc161f30e

...and a lot of extracting will happen

Then enter:
$ dmesg | tail -2

You'll get a response like this:
[ 5866.172626] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5870.282827] applesmc: FS! : read arg fail

Then just enable/disable wireless in Network Manager and it works!

Only I noticed every time I rebooted the machine the wifi would disconnect and dissapear as the OS was booting.  So I put a line in /etc/rc.local 
modprobe b43
save, reboot and all should be good.  

My issue is getting the touchpad to work with multitouch and more importantly waking the machine from sleep!

---

