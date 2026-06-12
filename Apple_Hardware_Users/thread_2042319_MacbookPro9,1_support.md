---
title: "MacbookPro9,1 support"
date: 2012-08-14
forum: Apple Hardware Users
---

### Post by CrazyDymond88 on 2012-08-14
I was wondering if there was any timeline on when we could see support for mac's generation 9 in the wiki.  I have a MacbookPro9,1 and not finding much support around the net.  This is for 64 bit only!
Use "noapic" to boot from installation media and do the install.  When done, modify /etc/default/grub
GRUB_CMDLINE_LINUX="nointremap"
save
update-grub

Then, I followed these instructions to get the wifi working (LAN works out of the box):


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
(credit goes to raritan01 for this)
I noticed that the wifi would disconnect and disappear from the machine on reboot so I added modprobe b43 to rc.local and it seems to be fine.

Two finger trackpad works after:
sudo add-apt-repository ppa:mactel-support && sudo apt-get update
sudo apt-get install xserver-xorg-input-synaptics

Things that still do not work, backlit keyboard, waking from sleep.

The waking from sleep is  my biggest problem and the reason I can't give this machine to the user.  Once the machine goes to sleep there is no waking it (it seems to wake the machine but not the display).  Anyone find a solution for this with this model?

---

### Post by thesamprice on 2012-08-21
I just got a new MacBookPro 9,1 laptop.
I ended up using the 10.0 install cd and then upgrading to 12.0
Along the upgrade highway I grabbed dehydra package which isn't maintained anymore.

Followed your steps to get the wifi card working.  (Was using a usb wifi card).

Anyhow sound doesn't work, and nvidia drivers are not listed in 3rd party drivers.

:(

Mouse sucks compared to my older macbook pro

---

### Post by CrazyDymond88 on 2012-08-29
That's really wierd, the sound works fine for me, even the volume up and down buttons.  The mouse works better if you edit the trackpad options and turn off tap to click.  I was able to get the nvidia card to show up once I installed bumblebee (it is open source support for Optimus).  The battery life is still pretty terrible, I'm assuming that's because it's using the nvidia card full time and not the lower power onboard intel one.  Still no luck getting sleep to work though so I've just advised the user to use hibernate for now.  It's weird that I haven't seen any real support for these models yet!

---

### Post by philcolbourn on 2012-09-01
Have you seen [my experience]("http://philatwarrimoo.blogspot.com.au/2012/06/unubtu-1204-on-macbook-pro-91-non.html")?

[http://philatwarrimoo.blogspot.com.au/2012/06/unubtu-1204-on-macbook-pro-91-non.html](http://philatwarrimoo.blogspot.com.au/2012/06/unubtu-1204-on-macbook-pro-91-non.html)

I'm using it now - main problem is no resume after sleep.

---

### Post by dbowlin17 on 2012-11-05
I am trying to do this, Have followed your instructions to the best of my ability, yet airport isn't working at all. :( any suggestions?

---

### Post by philcolbourn on 2012-11-06
> **dbowlin17 said:**
> I am trying to do this, Have followed your instructions to the best of my ability, yet airport isn't working at all. :( any suggestions?

I assume you have a MBP9,1 (15", mid 2012).

I have also documented installing 12.10.

[http://philatwarrimoo.blogspot.com.au/2012/10/installing-ubuntu-1210-on-macbookpro91.html](http://philatwarrimoo.blogspot.com.au/2012/10/installing-ubuntu-1210-on-macbookpro91.html)

Did you install those 3 packages to get wifi working?

Then you need to reboot. Ensure Wireless is enabled and connect to your AP.

---

### Post by dbowlin17 on 2012-11-06
I was directed to this page from the macbook page. I have a mid 2012 13 inch pro. I am not 100% sure what packages I installed, I believe that there were 3 packages. everything else (minus the light sensor to auto adjust brightness) works, so far...

---

### Post by philcolbourn on 2012-11-06
> **dbowlin17 said:**
> I was directed to this page from the macbook page. I have a mid 2012 13 inch pro. I am not 100% sure what packages I installed, I believe that there were 3 packages. everything else (minus the light sensor to auto adjust brightness) works, so far...

Ok. You have a MBP9,2. It is a little different, but WiFi should be same.

Install these packages

b43-fwcutter
linux-firmware (this should already be installed)
linux-firmware-nonfree

Reboot.

---

### Post by dbowlin17 on 2012-11-07
yes, so i rebooted after doing that initially and the wifi didn't work. however, last night i booted up and it worked. so... thanks for your steps and help

---

### Post by owow on 2012-11-23
> **dbowlin17 said:**
> I am trying to do this, Have followed your instructions to the best of my ability, yet airport isn't working at all. :( any suggestions?

Had the same problem on a macbookpro 9.2,  and ubuntu 12.10 64bit however after editing /etc/rc.local from here it worked

see: [https://help.ubuntu.com/community/MacBookPro9-2/Quantal#Wireless](https://help.ubuntu.com/community/MacBookPro9-2/Quantal#Wireless)

Also found some small errors in the instructions by forum conversion which you might have run into?

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

(copy the link location, not the text)
$ wget [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)   

$ tar -xjf broadcom-wl-5.100.138.tar.bz2
$ sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" broadcom-wl-5.100.138/linux/wl_apsta.o

You'll get a response like this:
This file is recognised as:
filename : wl_apsta.o
version : 666.2
MD5 : e1b05e268bcdbfef3560c28fc161f30e

...and a lot of extracting will happen

Then enter:
$ dmesg | tail -2

---

