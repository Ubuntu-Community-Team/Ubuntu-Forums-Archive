---
title: "Logitech MX900 Bluetooth Mouse"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by MartinGoose on 2006-07-22
I have been trying out Ubuntu as a future replacement for Win2000Pro on the 2 desktop PCs on my home network.  It seems to be going reasonably well!!

Only real problem so far is my Logitech MX900 Bluetooth Mouse.  The mouse is listed here:-
[http://www.holtmann.org/linux/bluetooth/features.html](http://www.holtmann.org/linux/bluetooth/features.html)
as 'supported under Linux' and I have managed to get it operating.  However it does not survive a reboot.  I have to unplug the USB connector and reinsert it for it to be detected again.

I have tried to follow the instructions at:-
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

lsusb returns:-
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 006: ID 046d:c705 Logitech, Inc.
Bus 002 Device 005: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 002 Device 001: ID 0000:0000

but hcitool dev returns only:-
Devices:

I now have HIDD_ENABLED=1 in /etc/default/bluez-utils but do not know what to do about
HIDD_OPTIONS="--master --server"

Any help out there?

---

### Post by MartinGoose on 2006-07-28
Following up my own post (sorry)

It would seem that this is not a Bluetooth problem but a USB detection problem.  How do I rescan for USB devices after logon if the USB mouse is not found?

---

### Post by bernied on 2006-08-05
I have the same issue with the MX900 - I have to unplug and replug the USB cable to make it work - have you had any luck yet?
Curiously, before I did this install, I was running Kubuntu off a gentoo kernel and the mouse was detected sometimes, especially if I wiggled it during startup. But not now. But in the gentoo kernel I hadn't enabled bluetooth at all.

Although you say this is not a bluetooth problem, I'm not so sure. I don't think the hub is being detected properly at startup. My bluetooth icon flashes on and off for a bit, then gives up, and there's nothing in lsusb (nothing that mentions bluetooth), and hcitool scan returns 'Device is not available: no such device', and like you I get nothing from hcitool dev

Will keep looking...

---

### Post by bernied on 2006-08-05
This might be worthwhile:
[http://www.bueche.ch/comp/mx900/mx900.html](http://www.bueche.ch/comp/mx900/mx900.html)

I don't think we'll have to do a lot of it though, as all the bluez-utils stuff is installed in ubuntu, and I'm guessing the current kernels don't need patching either. I'm going to start at the 'hcid' bit and see where I get.
At least he tells us how to find the mouse MAC address - it's written on the mouse - d'oh

---

### Post by bernied on 2006-08-05
That link in my last post was a winner. I think it was the hid2hci command that did it. I also changed that option in /etc/defaults/bluez-utils to HIDD_OPTIONS="--server"
Might have changed that in /etc/bluetooth/hcid.conf as well, but not sure if any of that was necessary. I think that hid2hci was the one...
```
$ man hid2hci
NAME
       hid2hci - Bluetooth HID to HCI mode switching utility
DESCRIPTION
       hid2hci is used to set up switch HID proxy Bluetooth dongle into the HCI mode and back.
```
Next is to get those other buttons working...

---

### Post by bernied on 2006-08-05
I should have said that once you do that hid2hci your mouse will go dead, and you'll then need to get it to connect using bluetooth. I had to mess around with the 'hidd --connect' command a bit, and even took out the batteries on the mouse and put them back again. You might have to restart hidd (killall hidd) as well (all this as root or with sudo in front). But it survives a restart, which was the important thing.

---

### Post by MartinGoose on 2006-08-06
Have tried to follow what you have done but only succeeded in making my MX900 inoperable in Win2000 when I swap back.  The hid2hci program is supposed to switch either way but appears only to switch to HCI.  When I try the ‘–1’ switch the utility responds ‘no devices in HID mode’.  Which is correct. I am trying to switch back.

I guess that I will have to email Logitech tech support.
](*,)

---

### Post by bernied on 2006-08-06
I apologise if I've led you astray. My story is also not quite as sweet as I thought. The mouse survived a restart in kubuntu, but once Windows (XP Home) was run, again it doesn't work. For me the solution might be to write a script to run at startup that will do the things that got it working last time. I'm sure there's some confusion in both operating systems as to whether the device is a bluetooth interface or a usb mouse.

Have you installed the Logitech bluetooth software on your Win2000? That might sort you out.

---

### Post by bernied on 2006-08-06
I'm now more confused that before. I don't know what I've done, but to connect the mouse, I now do the following:
hid2hci
hcitool --connect xx:xx:xx:xx:xx:xx    # replace x's with the mouse's MAC address

But then I have to press the connect button on the mouse - the frustration!
A script could be written for the rest, but not to press that button! 

Seems there's a lot more to know about this. 

Also have you tried powering off your bluetooth hub - unplugging it from the power adapter?

---

### Post by bernied on 2006-08-06
those emoticon things weren't intentional, but are kind-of appropriate anyway

---

### Post by bernied on 2006-08-06
OK, two more things (sorry, this may still not help you martin, but is maybe useful for anyone else who might follow this in future)

Adding the line```
hci_usb
```to /etc/modules,
and adding an entry to the /etc/defaults/bluez-utils file that looked like this```
HIDD_OPTIONS="-i 00:07:61:14:FE:A0 --server"
```seems to have worked.

Note that the MAC address in that line is not the one on the bottom of the mouse, but is the address given by ```
hciconfig -a
```Is this the MAC address of the bluetooth base station mouse-cradle thingy?

After running WinXP and rebooting into Kubuntu Dapper, the mouse worked straight away.

---

### Post by MartinGoose on 2006-08-07
Working again under Win2000:) 

Had to uninstall and reinstall the Widcomm Bluetooth stack then let the install wizard find the hub again.

Will try the tips in your last post later.

---

### Post by bernied on 2006-08-09
An update: although I thought that my setup was Windows-tolerant, I was wrong. I was only starting Windows to the login screen, wiggling the mouse to see it was connected, then restarting. Logging in to Windows and then restarting Kubuntu led to no mouse functionality, until I unplugged/replugged the USB cable. And then there was still no bluetooth until I went through the hid2hci rigmarole.

Since I knew that my gentoo kernel worked with the mouse, I compiled another kernel specifically for this machine. And now the mouse is detected straight away and (so far) survives Windows.

My understanding of the problem is something like this:
- the logitech USB Receiver functions both as a Human Interface Device (HID) when it reports itself as a mouse, and as a Bluetooth adapter, that could have a mouse attached. When Ubuntu is telling me that bluetooth is available the lspci command gives two logitech USB devices.
- there is a switch in the logitech device that tells it which way to behave. hid2hci changes this, but so does Windows.
- the Ubuntu kernel, wonderful as it is, is highly modular and loads modules as needed, but it doesn't know this bluetooth device and can be confused by it. If the device doesn't change between restarts, then Ubuntu seems to carry over the settings from last startup, and is happy, but if Windows has changed the device, then Ubuntu is confused. (I apologise for my anthropomorphisms here, this is just my primitive way of understanding the situation.) But we don't understand the nature of these 'settings', so don't know what to tweak.
- a simpler, less modular kernel has less decisions to make, so doesn't get 'confused'

This problem must be solvable in Ubuntu/Kubuntu because the mouse can be made to funtion properly. But there is a lot going on between the kernel - modules - USB bus - Logitech base - mouse. I'd like to learn how to tell the usb drivers about specific devices, to specify particular behaviours. And I'd like to learn more about bluetooth.

---

