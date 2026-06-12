---
title: "Installing a wireless driver on to gutsy"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by pavlick on 2008-02-05
hi
im a complete beginner, and i have just installed gutsy on my computer.
my problem is that gutsy doesn't seem to have recognized my wireless usb adapter and i can't even pick a network to connect to :( i am trying to install the drive for my Linksys WUSBG V4. but i have no idea how to work the terminal and how i can install ndiswrapper drivers and what not. please help me with the commands. I have all the files i need on the system, i've transferred them with my usb stick, but i cant put it all together. thank you

---

### Post by jbrown96 on 2008-02-05
After doing some searching, there appears to be three ways to get your card working. There is new support for your card (possibly limited and definitely buggy) in the kernel. The kernel update today (2.6.22-14) adds the drivers. The maintainers say the drivers are very buggy, but it's a place to start, since you will almost certainly do the updates anyways. There should be an icon telling you to update, but if it doesn't show, type the following in a terminal

sudo apt-get update
sudo apt-get upgrade

and type any passwords and agree to any updates. Restart your computer.

The second way is to download the most recent version of these drivers.
[URL="http://rt2x00.serialmonkey.com/wiki/index.php/Downloads"]
has the tarball you need. Use the Rt73 chipset (located at the bottom). There is a readme file in the tarball, but feel free to ask if you have questions installing. 

The third option is to use Ndiswrapper. From their list of cards at [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/")

  > 1.
      Card: Linksys WUSB54Gv4, 802.11b/g, USB 2.0

    *
      Chipset: RT2500USB (RT2571F) (They just changed the chip and didn’t tell anybody. Be careful which version (v1/v2/v4) you buy!)
    *
      usbid: 13b1:000d
    *
      Driver 00: Ralink Driver, Open Source: [http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/) - 2005-07-25 / Good alternative to ralinktech.com’s driver. Works WELL.
    *
      Driver 0: Ralink driver: [http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm) - 2005-03-25 / Drv2.0.1.0, rt2500usb.inf & rt2500usb.sys Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): works on both USB2.0 (load with modprobe ehci-hcd log2_irq_thresh=4 to avoid “usb X-Y: reset high speed USB device using ehci_hcd and address Z”) and USB1.1 (UHCI (OHCI not tested (yet?))). WEP works with 64bit and 128bit keys. but bitrate is only 11Mbit/s Note: rename the configuration file for the adapter once you installed the drivers (getting them extracted is quite a mess (WINE/Cedega) you need rt2500usb.*). ‘mv /etc/ndiswrapper/rt2500usb/148F\:2570.0.conf /etc/ndiswrapper/rt2500usb/13b1\:000d.0.conf’ should do the trick.
    *
      Driver 1: Linksys Windows XP driver: [http://www.linksys.com/download/default.asp](http://www.linksys.com/download/default.asp) Notes: ndiswrapper v1.1, kernel 2.6.11.7 vanilla: kernel-oops! ndiswrapper v1.2-rc1 loads fine (EHCI loaded with modprobe ehci-hcd log2_irq_thresh=4) but oopses when unloading the module and the adapter is still plugged in (Kernel 2.6.11.7 vanilla). Yet transmission seems to fail completely (except increasing ‘Tx Invalid misc’ values nothing happens).
    *
      Driver 2: older Linksys Windows XP driver: [ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe](ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe) Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): seems to work, but only 11Mbit/s and without any encryption. no need to unplug the device before removing the ndiswrapper module. works on USB2.0, USB1.1 not tested (yet).
    *
      Driver 3:There is a native driver for rt2x00 but it has no USB support yet. View its status at rt2x00.serialmonkey.com 

You can try it, but it is beyond my expertise. I would try the native drivers first. Write back with any questions

---

### Post by pavlick on 2008-02-05
i would do all of the above, but my biggest problem is that, I DO NOT HAVE INTERNET on the Ubuntu right now!
So i have no way of getting the card to work or going out on the internet, so i need a way to get my card online first, and if i succeed, my life will become a lot easier.

---

