---
title: "USB woes - please help!"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by iainv on 2008-03-22
I've posted several threads on usb problems recently, and thought i'd found a solution, but it's too flaky and only works intermittently, and now I seem to have buggered my whole system.

I need help please.

I'm running Gutsy 7.10, and wanted to install VirtualBox to run XP so I could use Quickbooks and my scanner (a Xerox 4800) which won't work in Ubuntu. The only other things installed after the default installation were Avant Window Navigator and the Compiz-fusion cube.

The problem I had was with VB not finding the USB ports.

My problem now is that whatever i've done to the USB setup has properly broken the normal running of the machine – the printer is only detected intermittently, my memory-stick won't work and the wifi keeps dropping out and asking for the WEP key again, before failing to connect.

During the initial attempts to run VB I took the following steps:

1)I uncommented the “magic” steps in /etc/init.d/mountdevsubfs.sh so that it reads as follows:

```
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs “” /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount –rbind /dev/bus/usb /proc/bus/usb
```

2)I edited /etc/udev/rules.d/40-permissions.rules to read:

```
# USB devices (usbfs replacement)
SUBSYSTEM==”usb_device”, GROUP=”vboxusers”, MODE=”0666&#8243;
```

3)I added the following entries to /etc/fstab

```
none /proc/bus/usb usbfs devgid=121,devmode=664 0 0 
usbfs	/proc/bus/usb	usbfs	auto	0	0
```

At this point VboxManage list usbhost just kept telling me all my devices were “unavailable”, so:
4)I added the following to System > Preferences > Sessions > Startup:

```
sudo /etc/init.d/mountdevsubfs.sh start
```

5)I then enabled the USB controller options in VB, and my scanner worked!


Unfortunately it didn't the next time I rebooted, and I started to get problems with my memory sticks and wifi in Ubuntu as I mentioned above.

In the meantime i'd also installed, and then uninstalled HPLIP as it didn't cope with the flaky USB stuff at all and failed to print a test-page just saying “the printer may not be connected” when it clearly was!

I've therefore removed all the edits I made above, restarted the system several times over and still it's no better.

The output of VboxManage list usbhost is now:

```
VirtualBox Command Line Management Interface Version 1.5.6 
(C) 2005-2008 innotek GmbH 
All rights reserved. 

[!] FAILED calling Host->GetUSBDevices(CollPtr.asOutParam()) at line 1958! 
[!] Primary RC  = 0x80004005 
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80004005 
[!] Text        = Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer 
[!] Component   = Host, Interface: IHost, {81729c26-1aec-46f5-b7c0-cc7364738fdb} 
[!] Callee      = IHost, {81729c26-1aec-46f5-b7c0-cc7364738fdb} 
```


lsusb doesn't work – it just hangs!

Please can someone help me - I need to get everything running properly – I would try a fresh installation, but I worry that I'll just run into the same problems again when I try and fix VB, so I'd like to try and understand where it's going wrong if possible.

Iain

---

### Post by diablo75 on 2008-03-23
I would have put this post in the Virtualzation forum.  If a mod doesn't move it there for you, you might try copying it over and seeing if someone there is more familiar with VB.  I use VMware-Server, myself...

---

