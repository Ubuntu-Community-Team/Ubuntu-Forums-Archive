---
title: "Installing Ubuntu on Hp tx1250ea (HowTo)"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Irish Sean on 2008-02-04
HP tx1250ea

I have recently installed Ubuntu (7.10 32 bit) on it and it took a bit of doing as it was my first foray into the Linux Operating System.
While trying to get the various features running on the i went through various forum post for similar laptops and scour small bits of information.
So i decided to throw everything i used that i think helped me and link to the original article where possible.

Lets start with just getting it to boot from the live CD pressing F6 and adding the following will allow you to boot up with next to no trouble.

Booting up:
```

noapic acpi_irq_balance fb=false doscsi

```
Sound:

Installing the sound drivers was one of the easier things to do.

The drivers can be located here

[http://linux.softpedia.com/progDownload/ALSA-driver-Download-164.html](http://linux.softpedia.com/progDownload/ALSA-driver-Download-164.html)

I downloaded the latest ones and they worked almost straight away i only had to unmute the headphones for them to work.

If you haven't compiled source code before you'll need to install some packages

Open a terminal and type
```

~$ sudo -s
~# apt-get update
~# apt-get install build-essential
~# apt-get install linux-headers-`uname -r`

```
When that is installed you need to navigate to the dir of the downloaded file and type
```

~$ sudo -s
~# tar xvjf alsa-driver-.....
~# cd alsa-driver-....
~# ./configure
~# make			//May take a few minutes
~# make install
~# exit

```
Once this is installed you should reboot the system and that should sorth the sound problem.

Wireless:

First things first we blacklist the old wireless drivers

Open a Terminal window
```

~$ sudo gedit /etc/modprobe.d/blacklist

```
Add the following lines to the end of the file (Touchscreen elements optional)
```

# Causes problems with wireless
blacklist bcm43xx

#cause touchscreen drivers to malfunction
blacklist usbtouchscreen
blacklist tkusb

```
With that done download the wireless driver from 
HP Drivers:
[ftp://ftp.hp.com/pub/softpaq/sp36501-37000/sp36684.exe](ftp://ftp.hp.com/pub/softpaq/sp36501-37000/sp36684.exe)
Dell Drivers:
[http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)

To extract the necessary files you may have to boot into windows and extract the files by right clicking the icon and chosing to extract (you could try using wine on the driver but as i have no experience i didn't)
Alternatively Drivers can be downloaded from the dell website (I know wierd but they worked for me) and extracted in linux by right clicking and selecting extract here.

Now you need to open a terminal
```

~$ sudo apt-get install ndiswrapper-utils-1.9

```
When this is done reboot

Now you need to open a terminal again and navigate to the folder you extracted the driver files to
```

~$ sudo -s
~# cd DRIVER/
~# ndiswrapper -l		//Lists the drivers currently installed, should be empty.
~# ndiswrapper -i bcmwl5.inf
~# ndiswrapper -l		//Should tell you that your drivers are installed and the device is ready (or something like that)
~# ndiswrapper -m
~# modprobe ndiswrapper
~# echo ndiswrapper >> /etc/modules/

```
Everything should be working after a reboot



TouchScreen:

Download the Drivers from here:
[http://210.64.17.162/web20/TouckDriver/linuxDriver.htm](http://210.64.17.162/web20/TouckDriver/linuxDriver.htm)

Open a Terminal, navigate to where the file downloaded and type:
```

~$ tar xvfz TouchKit_1.07.0831.tar.gz
~$ cd TouchKit
~$ sudo cp egalax_drv.so /usr/lib/xorg/modules/input/

```

Next we have to edit xorg.conf
```

~$ sudo gedit /etc/X11/xorg.conf

```
The following line should be added in "Server Layout":
```

InputDevice    "EETI"      "SendCoreEvents"

```
And between sections of this file you should add the following:
```

Section "InputDevice"
      Identifier "EETI"
      Driver "egalax"
      Option "Device"    "/dev/usb/hiddev0"
      Option "Parameters" "/etc/egalax.cal"
      Option "ScreenNo"   "0"
EndSection

```

Now if you haven't blacklisted the touchscreen drivers above do it now
Back in the terminal navigate to the touchscreen drivers and type
```

~$ cd TouchKit
~$ sudo ./TouchKit

```

This should open up a dialog for calibration of the touchscreen.


I hope this is helpful to anyone who was a lost as i was when i first started:
Links to where i found origional information
Boot Info:
[http://ubuntuforums.org/showpost.php?p=4247852&postcount=584](http://ubuntuforums.org/showpost.php?p=4247852&postcount=584)
TouchScreen:
[http://ubuntuforums.org/showpost.php?p=4197376&postcount=542](http://ubuntuforums.org/showpost.php?p=4197376&postcount=542)
Wireless: (I Think)
[http://ubuntuforums.org/showpost.php?p=3491929&postcount=257](http://ubuntuforums.org/showpost.php?p=3491929&postcount=257)

---

### Post by Blutack on 2008-02-04
Thanks for the effort you've put in!
However, you might want to move your thread here
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
Where it may get more attention.

---

### Post by Irish Sean on 2008-02-19
> **Blutack said:**
> Thanks for the effort you've put in!
However, you might want to move your thread here
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
Where it may get more attention.

If someone wants to do that for that would be good too it won't help anyone if they can't find it

---

