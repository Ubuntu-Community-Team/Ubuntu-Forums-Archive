---
title: "mounting usb-devices"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by thrasher on 2005-11-24
Hi! 

On my notebook, i have only an external dvd-drive connected with usb and i couldn't use it for installation. 
Now Ubuntu is running, but i still have no clue how to mount the drive. Second, there's an usb-stick too that i'd like to have mounted in ubuntu...

do i have to install modules first for this or is it just a simple trick... i tried mount /proc/bus/usb/004 /dvd but it returns that it isn't a block-device... 

any hints?

---

### Post by Swe on 2005-11-24
My External DVD wouldn't mount unless i put a CD in it 
but i guess you know about that.
Have you tried to use HAL and see if it's even listed?
You might need to download some modules as you said yourself.

I've only had Ubuntu for about 4 days
with no prior experience of Linux what so ever
so i can't be of much help either.

---

### Post by patrick295767 on 2005-11-24
try : qtparted to see it 
or gparted 
([HTML]apt-get install qtparted [/HTML]) first 
  
also, u can use: 
lsusb
  
or usbview
  
-----------------------------
To know which /dev/sdax u have, qtparted normally:
  
mount -t ntfs /dev/sda1 /mnt/sda1 
should work normally... 
  
---
greetz'
Pat

---

### Post by thrasher on 2005-11-24
ahm...yeah..

i tried lsusb and this is the output: 

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

well, since i tried out to modprobe ndiswrapper, dmesg writes...

Initializing USB Mass Storage driver...
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb 4-2: new high speed USB device using ehci_hcd and address 3
usb 4-2: khubd timed out on ep0in
usb 4-2: khubd timed out on ep0out
usb 4-2: khubd timed out on ep0out
usb 4-2: device not accepting address 3, error -110

it does this with all addresses, but none succeeds :(

---

