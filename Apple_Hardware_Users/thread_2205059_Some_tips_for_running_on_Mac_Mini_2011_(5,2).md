---
title: "Some tips for running on Mac Mini 2011 (5,2)"
date: 2014-02-11
forum: Apple Hardware Users
---

### Post by macintux on 2014-02-11
My Mac Mini 5,2 (Mid 2011) is a rare one since it is the last one made with discrete AMD graphics, other models have Intel Integrated Graphics, even in the same Mid 2011 series.

Having an AMD Radeon graphics card on a Mac with EFI causes all kind of boot problems, on MacBook Pros you can disable the AMD graphics and switch to Intel, but this Mac mini does not have switchable graphics, it is always using the discrete one.
The key is to boot Live Ubuntu USB Stick in Legacy/BIOS mode and boot the installed Ubuntu using the EFI Stub (booting the kernel via rEFInd).

**Here is what I did for boot and installation:**
- I created a bootable USB stick from Ubuntu 13.10 64bit Desktop iso by following this guide:
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

- Then I installed rEFInd with all drivers:
```
./install.sh --alldrivers
```
Download link:
[http://sourceforge.net/projects/refind/files/0.7.7/refind-bin-0.7.7.zip/download](http://sourceforge.net/projects/refind/files/0.7.7/refind-bin-0.7.7.zip/download)

- I restarted my Mac mini, the rEFInd boot menu found two instances of grubx64 and fallback boot loaders on the USB flash drive, all of them booted fine but the picture on screen froze after trying to load the correct graphics driver.

- I chose the last rEFInd boot option, *Boot Legacy OS*, it booted the live Ubuntu in BIOS compatibility mode.
Booting in BIOS compatibility mode works fine and the graphic card is detected.

- I installed from the live Ubuntu, selected to manually partition the drive, installed the boot loader on Ubuntu's partition, not the mbr.

- After the installation finished, I restarted again, this time the rEFInd menu recognized the installed Linux kernel and booting via EFI Stub allowed me to take advantage of EFI features while retaining graphic card's usability.

**Here are some tips after the installation:**
- You can enable your AirPort WiFi chip by going to System Settings->Software & Updated->Additional Drivers.

- The open source radeon drivers seem to work fine for me, but you can install the proprietary drivers from the same place, I did not try it, but it should work.

**Issues:**
My Mac mini gets a little hot while I'm using Ubuntu, therefore I decided to install macfanctld.
Installing the macfanctld caused the fans to spin at around 4000 rpm, while the normal minimum fan speed is 1800 rpm on OS X and 2000 rpm on macfanctld config.
I installed the lm-sensors package, tried to detect the sensors, the issue remains.
Even though applesmc module was already available and loaded, I tried the one available from the MacTel team and it did not make any difference.
I thought some of the sensors might have given bogus values, so I excluded them and restarted the macfanctld, the issue remains.
The odd thing is, even after rebooting to OS X the fan speed remains at around 4000rpm, but if I set my OS X to sleep and then wake it, the fan speed returns to normal.

---

