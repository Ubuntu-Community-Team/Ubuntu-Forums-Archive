---
title: "Can't connect USB device to VirtualBoxed XP"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-09-02
Hello
I've installed Windows XP with VirtualBox, and I've installed the guest addons, but when I try to connect my Pocket Loox I get the following error message:
[IMG]http://i187.photobucket.com/albums/x161/jstokland/snapshot10.png[/IMG]

Does anyone know how to fix this?
Thanks in advance!
Joakim

Edit: Oh, and in Device Manager in XP i found this below "Standard OpenHCD USB Host Controller" :
Windows cannot load the device driver for this hardware. The driver may be corrupted or missing. (Code 39)

Is there any other driver I should install?

---

### Post by nonewmsgs on 2007-09-09
your best bet is to set it up to use a shared folder.  there's an option in vb before you select which virtual machine you want to use.

and just use linux for the down and dirty thumb drive work.

---

### Post by llamakc on 2007-09-09
You need to make sure that USB is config'd properly in VirtualBox. Before you start up the VM, make sure USB is even enabled.

---

### Post by Orbital75 on 2007-09-09
With Virtual Box you have to install the Guest Additions and 
enable USB Controls. After this you must set up the USB Device Filters.
as llamakc stated above, you must do all this before you start your Virtual Machine

[IMG]http://img516.imageshack.us/img516/8328/00screenshotha0.jpg[/IMG]

---

### Post by Verily on 2007-09-09
I'm also having an issues with getting USB to work with VirtualBox... I have Guest Additions installed.  USB is enabled.  And I've even gone through several steps like setting up a usb user group and whatnot that I've found in other threads/on the [VirtualBox website](http://virtualbox.org/wiki/USB_on_Ubuntu_7.04), have rebooted several times, but still, when I run "VBoxManage list usbhost" in the shell, it tells me "Host USB Devices:  <none>."  I tried putting in the values myself, but even that doesn't work.

I have VMware also installed, so I tested on that and VMware reads the USB fine.  So I'm unsure what the problem is.  And even though I could just use VMware, I suppose, it seems to run a whole lot slower, so I'd kinda rather do VirtualBox if I can.

---

### Post by Joakim Stokland on 2007-09-10
Thanks for your answers!
I've enabled USB and created a filter for the Pocket Loox (VirtualBox was able to fill in the form automatically). I thought the filters were optional though.
I have installed the Guest Additions, but it seems like the USB driver's not properly installed, hence the error message in Device Manager in WIndows.
You see, the thing is, the software for communication with the Pocket Loox actually have to connect to the device to transfer any files at all. The Pocket Loox doesn't act like a thumbdrive. This is the reason I installed Windows at all. Damn Microsoft! :p
Please see my settings and the error message below. Any suggestions?

Thanks again!
Joakim

[IMG]http://i187.photobucket.com/albums/x161/jstokland/snapshot12.png[/IMG]

[IMG]http://i187.photobucket.com/albums/x161/jstokland/snapshot11.png[/IMG]

---

### Post by Joakim Stokland on 2007-09-10
The solution to this problem was actually very simple. All I had to do was to uninstall the USB driver (update driver in device manager didn't help), select Install new hardware and just wait for the correct driver to be installed. All this after mounting the Guest additions image of course.
As soon as the USB driver was running properly I was able to connect to the Pocket Loox as I should.

Thanks for your help anyway, guys! I appreciate it! :)
Joakim

---

### Post by SteveHoffmanUK on 2007-09-10
Joakim: Glad you found the solution! I tried what you did, and no success here.

Virtualbox installed fairly easily, I set up a Windows XP Home system as a VM. It also installed pretty quickly with no obvious problems. It connected to the internet OK, and the one program I need in Windows also installed OK. I'm very impressed at VBox's speed and facilities.

However, I have two USB devices: an 80Gb Freecom VHD-2 PRO external hard disk that I need for backup and a .5 Gb Buffalo Clip memory stick. Neither of these are recognised by my XP virtual machine. I have installed the Virtualbox Guest Additions 1.5.0. Within my XP machine I tried uninstalling the drivers for both the devices shown in the XP Control Panel under Universal Serial Bus Controllers:
1. Standard OpenHCD USB Host Controller
2. USB Root Hub

I then asked XP to look for new hardware, and it duly found both these devices and reinstalled the drivers for them. Still no USB devices show in My Computer. 

I do notice that when XP is running and, in the Virtualbox menu I click on Devices > USB Devices, the three devices attached to my USB controller (Freecom disk, Buffalo memory stick and a Canon printer) show dimmed out in a drop-down submenu. I have installed the filters for the three devices - they came up right away in the VBox Settings function. But still nothing working on the USB connection.

I am running Dapper, if that's relevant. Thanks for any help you can give.

---

### Post by Joakim Stokland on 2007-09-11
Actually, I'm quite a beginner with Ubuntu myself, but have you tried disabling the filters? You are not bound to use them. They are optional. I have currently no filters active, and it works like a charm.
Hope it works out for you too :)
Joakim

---

### Post by SteveHoffmanUK on 2007-09-11
Just tried disabling all the USB filters, but no luck.

Virtualbox recognises all my USB devices but says they are "unavailable". My guest system can't detect them at all. Even when I "install" my Canon USB-connected printer using the manufacturer-supplied CD,  it won't print. The XP device manager shows the printer status as "ready" but when I try to print anything nothing happens.

So at the moment I have no connectivity between my guest XP system and anything connected to my USB port. No USB device is recognised by XP although all are recognised by Virtualbox. I haven't gone through the slog of updating Windows yet, so my XP is still at the SP-1 level, but I can't imagine that makes any difference.

---

### Post by SteveHoffmanUK on 2007-09-11
Got it working by following this advice, based on another Ubuntu thread:

> -Install XP or other OS

-In Ubuntu, create a group called "usbfs" and add yourself to it.

-In terminal issue the following command:

sudo gedit /etc/fstab

-In this file paste the following lines, and change the group ID according to the group ID that is shown for the group "usbfs".


# 1001 is the USB group ID
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0


-Save and close file.

- In Virtualbox, set up the filters for USB devices

-Reboot

When Ubuntu comes up again, you have to unmount the USB devices in Ubuntu before the virtual machine can recognize them, so eject them. 

Open Virtualbox, start XP virtual machine, and it should recognize the USB devices. 

Amazing, after so many attempts, XP "Found new hardware" messages popped up one at a time, and in the end, everything appeared.

---

### Post by Joakim Stokland on 2007-09-11
Great! Glad you got it working! :)

---

