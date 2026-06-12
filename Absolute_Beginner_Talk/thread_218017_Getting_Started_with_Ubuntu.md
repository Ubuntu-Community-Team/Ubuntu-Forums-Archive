---
title: "Getting Started with Ubuntu"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Gris on 2006-07-18
Hi Everyone

My first try at Linux! (I also have Windows and MacOS X)

I've just installed Ubuntu 6.06 and am having 2 problems:

1. I can't access the Internet. I'm using a USB DWL-120d connecting to a wireless router. This device is listed as "Prism 2.x 802.11b Adapter" in the Device Manager. Do I need to download a driver for this or is there a configuration step I need to take? To get this working on Windows I had to download drivers (on the Mac I just plugged it in and it worked instantly!).

2. My screen only comes up in 1280x1024 and is very slow. I have a 1920x1200 monitor being driven by a Radeon 9700. How can I set up the screen to work properly?

Thanks for any help!

David

---

### Post by GuitarHero on 2006-07-18
System>Preferences>Screen Resolution
If that doesn't let you make it big enough, do 
sudo dpkg-reconfigure xserver-xorg
Add your resolution.


Not sure about the networking, check the site of the card maker for drivers.  Networking can be tough.  You configured and activated it right?

---

### Post by Sef on 2006-07-18
What are your system specs?  


> 2. My screen only comes up in 1280x1024 and is very slow. 

How much ram do you have?

---

### Post by Gris on 2006-07-18
Hi, thanks for the quick replys!!

How do I do "sudo dpkg-reconfigure xserver-xorg"?

PC: 1Gb RAM; P4 2.5GHz; Radeon 9700 Pro; Unbuntu on separate 80Gb drive.

Cheers

David

---

### Post by bruenig on 2006-07-18
> **Gris said:**
> 
How do I do "sudo dpkg-reconfigure xserver-xorg"?

The terminal is the name of the command line in ubuntu
Go to Applications>Accessories>Terminal and copy and paste that into it and hit enter.

---

### Post by nalmeth on 2006-07-18
Open a terminal to enter the command, you should only need to do this if you're prefered resolution isn't available in System - Preferences - Screen Resolution

Applications - Accessories - Terminal

sudo dpkg-reconfigure xserver-xorg

pick defaults across the board (unless you know better), and then when you get to the resolutions, add the ones you need.

Wireless can be tricky, especially with USB devices, as companies choose not to release drivers for linux, so developers have the arduous task of reverse engineering their technology.

Stick around and ask for help, we are glad to provide if we can.

Did you try activating the device from System - Administration - Networking?

We'll start there

---

### Post by Arisna on 2006-07-18
When you're ready to attack the network issue, go back to the terminal and enter the following command (you can copy and paste it):

```
dmesg | grep -A 10 Prism
```

This will output some (hopefully) enlightening information about your network adapter.  Copy the output by highlighting it, going to "Edit > Copy", and pasting it into a message here.

---

### Post by Gris on 2006-07-18
Hi
Okay, I've run the sudo command and went through all the options, thanks.

When I reboot all I get is a blank screen on both the VGA and DVI inputs (both are connected to the monitor). When I switch to VGA, the monitor says "Cannot handle this resolution" so I assume that somehow it has selected a resolution greater than 1920x1200. During the sudo command it did recognise the monitor as a Dell 2405 so this is surprising.

Also, when I hit Esc to go into Grub I cannot see my Windows OS in the choices. Windows is on a separate HD on a RAID controller. How do I reboot to Windows?

Cheers

David

---

### Post by Gris on 2006-07-18
Hi Everyone

Some progress, thanks for trying to help me!

1. I rebooted and used Grub and then selected recovery mode which got me a command-line. I redid the sudo command and this time discovered (by accident) that hitting the spacebar allowed me to put an asterisk (*) in the 1920x1200 option. I also selected the Medium option and scrolled through the options until I found 1920x1200x60Hz. This was hard because the screen was not refreshing properly and was leaving a trail of characters behind!

Anyway, I now have a 1920x1200 display! It only works in analogue mode (VGA) not digital (DVI) though...

2. I tried "dmesg | grep -A 10 prism" (lowercase P) and got some output. Unfortunately I don't have a way to copy and paste this as I don't have a connection between the PC and the laptop on which this is being typed! Here is what I believe is the relevent output, typed by hand:

prism2usb_init: prims2_usb.o: 0.2.2 Loaded
prism2usb_init: dev_info is: prism2_usb
usbcore: registered new driver prism2_usb

Cheers

David

---

### Post by Gris on 2006-07-18
Arisna, when I go to System->Administration->Networking, the panel lists 2 connections: Ethernet and Modem, so the USB device is not showing up. Can I add it? I tried right clicking, but nothing happens :)

Cheers

David

---

### Post by Arisna on 2006-07-18
I believe you're going to need to install some additional software to get the wireless network interface to work.  The "dmesg..." command I had you enter tells us that you already have the driver, but this entire process will work more smoothly with the package "linux-wlan-ng" installed.  It contains wrapper scripts and other utilities that will make this easier.

So, here's our dilemma--you need to install this package, which would be downloaded from the Internet, but your Internet connection isn't working yet.  Would it be convenient to hook up this computer temporarily using an Ethernet cable?  If not, you can download the package with your laptop or another PC and transfer it to the Ubuntu machine with a CD/Floppy/USB Disk.

If you can hook up to a wired configuration for a few minutes, the command to type in a Terminal would be:

```
sudo aptitude install linux-wlan-ng
```

If you opt to download and manually transfer the package instead of connecting temporarily with wires, you can download it here using another machine:

[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.3-1ubuntu7_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.3-1ubuntu7_i386.deb)

Copy the file to your home folder on your Ubuntu machine. Make sure to right-click on the icon that appears for the removable media you've used and Unmount/Eject it before you remove the media.  Then type this in a terminal:

```
cd
sudo dpkg -i linux-wlan-*Hit Tab Now.  It will auto-complete the file name*
```

Whichever method you choose, go ahead and reboot the Ubuntu machine after you've installed linux-wlan-ng.  See if the device has started working.  If not, post output from this command:

```
iwconfig
```

:)

---

### Post by Gris on 2006-07-18
Hi Arisna

Thanks so much for the help! I downloaded and bunt to CD the deb package and followed your instructions. In setting up, the following error turns up:

* linux >= 2.6.13-rc1 requires pcmciautils instead of pcmcia-cs

I tried rebooting anyway, but no improvement.

How do I get pcmciautils?

Thanks again,

David

---

