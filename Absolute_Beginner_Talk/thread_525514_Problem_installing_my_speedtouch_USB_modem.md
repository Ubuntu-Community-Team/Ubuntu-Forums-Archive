---
title: "Problem installing my speedtouch USB modem"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by evilbdboi on 2007-08-14
i have i have gone through the threads and websites here regarding the installation of the modem but none of them gave solutions to the problem that i have

after typing this command,

unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor KQD6_3.012

it gave me an error stating that ./firmware-extractor KQD6_3.012 is invalid parameter

---

### Post by laidback on 2007-08-14
This isn't much immediate help but I gave up with my Speedtouch330 in Ubuntu, although I believe that others have managed to get it to work. Instead I bought a router/modem and use ethernet, much better. 
I did get the Speedtouch working in Mandriva.

---

### Post by jgrabham on 2007-08-14
That modem works great in linux theese days - see here - [https://launchpad.net/usb-adsl-modem-manager](https://launchpad.net/usb-adsl-modem-manager)

---

### Post by capink on 2007-08-14
> **evilbdboi said:**
> 

it gave me an error stating that ./firmware-extractor KQD6_3.012 is invalid parameter

You have to rename KQD6_3.012 into mgmt.o and put that into the directory firmware-extractor. So assuming that both the file KQD6_3.012 and the firmware-extractor directory are in your current directory:

```
mv ./KQD6_3.012 ./firmware-extractor/mgmt.o
cd ./firmware-extractor
./configure
make
```

That would create two files: speedtch-1.bin & speedtch-2.bin

Edit: Make sure you are using the file that match you revision. To know the revision of the modem type:

```
cat /proc/bus/usb/devices | grep -B 1 THOMSON
```


For revision 0 & 2 use the KQD6_3.012 file. For revision 4 use the ZZZL_3.012 file.

---

### Post by jgrabham on 2007-08-14
> **evilbdboi said:**
> i have i have gone through the threads and websites here regarding the installation of the modem but none of them gave solutions to the problem that i have

after typing this command,

unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor KQD6_3.012

it gave me an error stating that ./firmware-extractor KQD6_3.012 is invalid parameter

Just ignore all this - here is a .deb file which will install all by itself and all you have to do is tell it your country and username and password in a Graphical user interface

> **jgrabham said:**
> That modem works great in linux theese days - see here - [https://launchpad.net/usb-adsl-modem-manager](https://launchpad.net/usb-adsl-modem-manager)

---

### Post by StevenHarper on 2007-08-14
Hi just a hello

I have made a Package (deb) to support Speedtouch USB 330 modems you can get all the info and the DEB from here

[http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page]("http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page")

Also there is a Long running forum thread here 

[http://ubuntuforums.org/showthread.php?t=445701]("http://ubuntuforums.org/showthread.php?t=445701")

and a Trouble Shooting Guide here

[http://www.squeezedonkey.com/wiki/linux/index.php?title=Troubleshooting]("http://www.squeezedonkey.com/wiki/linux/index.php?title=Troubleshooting")

Hope this helps

Steve

---

