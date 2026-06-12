---
title: "ZyXel 630-C ADSL Modem Connection issues"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by Orpheus99 on 2005-11-03
Hi

Completely new to Linux, however I work in IT, just in the 'other' world. 

Downloaded  Breezy 5.10 and installed it. Impressed as it detected firewire and multi card reader but it cant see my (usb adsl) modem. Bit of a problem as everything I have read relies on app-get - which obviously relies on internet. Which I dont have (unless I'm in Windose) !!

Really frustrating because all I have found is the driver, which requires recomping, which seems difficult in Ubuntu with no internet connection. Is there something (relatively) simple that can be done ? Please explain in (relatively) straigforward words ! I used to work in a Unix environment 6 years ago and have almost completely forgotten everything !!

Thanks

O

---

### Post by blastus on 2005-11-03
I'm not sure about your modem, but in general it is difficult to get modems to work on Linux. Some of the reasons are:

1. Many manufacturers don't support Linux--they don't release drivers for Linux and even if they do they are usually proprietary and closed source.

2. Microsoft has helped manufacturers to foist "winmodems" on the market--these are modems that are specifically designed to only work with Microsoft Windows--these modems don't have the hardware necessary to function without highly proprietary Microsoft Windows drivers.

Fortunately for me, I have a Lucent modem. It's a winmodem but it isn't a total winmodem as it has a DSP (Digital Signal Processor) in it which means it doesn't need specialized Microsoft Windows drivers. I was able to get my modem to work on Ubuntu, but I had to learn a lot and I had to compile the drivers.

If you have the source code for the drivers for your modem, you should be able to compile them. Unfortunately Breezy has an issue with compiling kernel modules that Hoary doesn't. So before you even figure out how to compile the modules, you need to install gcc-3.4. I posted a HOWTO here: [Install gcc-3.4 via apt-get without an Internet connection.](http://ubuntuforums.org/showthread.php?t=79896)

You may want to check out [Linmodems](http://linmodems.org/). I'm not sure if they discuss ADSL modems but they may have some information that you may find useful. In short, unless your manufacturer has stated that your modem is compatible with Linux (my manufacturer did), AND you can find someone else that has the same modem as yours with instructions on how to get it working (I did but the instructions were very hard to follow initially), then it may be near impossible to get it to work. I really wish I could help you more but I don't have a ZyXel modem and I've only been using Linux now for a couple of months!

---

### Post by Orpheus99 on 2005-11-03
Thanks for that - I've now got gcc installed and I've downloaded a driver tar file for my modem chipset.

How can I compile that now ? Do I need to get the kernel headers ? if so, how ? could you explain in idiotspeak 

thanks

---

### Post by blastus on 2005-11-04
For my modem, I just enter "make" in a terminal. But that's only one piece to the puzzle. After you compile the kernel modules, the output should be one or more *.ko files. You then need to install them on your machine. I'm not sure what the procedure would be to install them on your machine, as the procedure may be different for different hardware. Does the tar file contain instructions? I'd try looking around on the site you downloaded the file from.

Yes, you need to get build-essential and kernel headers. build-essential contains gcc-4.0 and other stuff you need to compile things. However, as noted, you need to manually install gcc-3.4 to compile kernel modules on Breezy as gcc-3.4 is not on the distribution CD. The kernel headers contain the C header files you need to compile your modules against the kernel you have. If you are running Breezy on an i386 machine, you would enter the following:

```
sudo apt-get install build-essential linux-headers-2.6.12-9-386
```

This will install everything you need to compile the kernel modules (except of course gcc-3.4.)

---

