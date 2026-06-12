---
title: "Gnome Bluetooth &amp; Bluetooth Dongle &amp; Mighty Mouse"
date: 2006-11-14
forum: Apple PPC Users
---

### Post by amishman on 2006-11-14
I have a G5 with a Belkin bluetooth dongle plugged into the USB port.  I also have a new wireless Mighty Mouse.  I would love to use it with Ubuntu.  I can't find Gnome Bluetooth in the Synaptic Package Manager.  Is it already part of 6.10 Ubuntu?  My G5 did not come with bluetooth so I am using a Belkin Bluetooth dongle.

Any help would be great.

tj

---

### Post by LifeIsAFractal on 2006-11-27
Well, I'm not running a Mac but I think I can help you.  First you need the package bluez-passkey-gnome.  Once you have that installed logout and log back in and it will automatically start.  Now turn on your mouse and leave it motionless.  Run hcitool scan at the terminal.  This should show you your mouse.  Take the mac address and type this command hidd --connect XX:XX:XX:XX:XX:XX where XX:XX:XX:XX:XX:XX is the mac address of your mouse.  The bluetooth applet should ask you for a key, enter 0000.  This should work.  I have this working on a PC with a single button apple bluetooth mouse.  If you have any further question PM me and Ill post more help in this thread.

---

### Post by acheun on 2006-11-27
I can't find the bluez-passkey-gnome in dapper repository.  Do you know which one it resides?  I like to do the same.

---

### Post by martinje on 2006-11-28
click on system then administrator then synaptic packet manager do a search for it there.

---

### Post by ivelasco on 2006-11-28
I'm using a mighty on a Powerbook G4 with onboard bluetooth.The specific files that I have edited are:

/etc/bluetooth/hcid.conf-->added two lines:

auth enable; 
encrypt enable;

/etc/default/bluetooth :

HIDD_ENABLED=1-->VERY IMPORTANT(default is 0)
HIDD_OPTIONS="--connect 00:14:51:C3:5A:07 --server"-->Obviously mighty's MAC

That&#347; all

---

### Post by acheun on 2006-11-29
Thanks.  I don't need bluez-passkey-gnome (i can't find it any way).
I do exactly the same on the first file.
For the second one, I couldn't find the /etc/default/bluetooth.  But I did find /etc/default/bluez-utils, and edit the same inside.
It did prompt me enter pin for the mighty mouse, and the Mighty Mouse work!

(However, the bluetooth signal die very soon.  I believe it's another problem of the signal.  I continue my search on this. )

---

### Post by jrsoft on 2007-03-25
I do what is described in this thread and I get errors in the kernel log when it is initializing bluetooth. The portion of the log with errors is as follows:

Mar 25 21:17:19 jack-desktop kernel: [  113.424091] ioctl32(hald-probe-inpu:4570): Unknown cmd fd(4) cmd(40084502){00} arg(ffed78aa) on /dev/input/ts0
Mar 25 21:17:19 jack-desktop kernel: [  113.710603] ioctl32(hald-probe-inpu:4581): Unknown cmd fd(4) cmd(40084502){00} arg(ffad58aa) on /dev/input/ts1
Mar 25 21:17:23 jack-desktop kernel: [  117.674166] ondemand governor failed to load due to too long transition latency
Mar 25 21:17:23 jack-desktop kernel: [  117.868397] Bluetooth: Core ver 2.8
Mar 25 21:17:23 jack-desktop kernel: [  117.868410] NET: Registered protocol family 31
Mar 25 21:17:23 jack-desktop kernel: [  117.868414] Bluetooth: HCI device and connection manager initialized
Mar 25 21:17:23 jack-desktop kernel: [  117.868450] Bluetooth: HCI socket layer initialized
Mar 25 21:17:24 jack-desktop kernel: [  117.898999] Bluetooth: L2CAP ver 2.8
Mar 25 21:17:24 jack-desktop kernel: [  117.899005] Bluetooth: L2CAP socket layer initialized
Mar 25 21:17:24 jack-desktop kernel: [  117.904864] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
Mar 25 21:17:24 jack-desktop kernel: [  117.943138] usb 3-3: usbfs: USBDEVFS_CONTROL failed cmd hid2hci rqt 64 rq 0 len 0 ret -110
Mar 25 21:17:24 jack-desktop kernel: [  118.009055] Bluetooth: RFCOMM socket layer initialized
Mar 25 21:17:24 jack-desktop kernel: [  118.009081] Bluetooth: RFCOMM TTY layer initialized
Mar 25 21:17:24 jack-desktop kernel: [  118.009084] Bluetooth: RFCOMM ver 1.7
Mar 25 21:17:24 jack-desktop kernel: [  118.289934] usb 3-3: USB disconnect, address 4
Mar 25 21:17:24 jack-desktop kernel: [  118.593715] usb 3-3: new full speed USB device using ohci_hcd and address 7
Mar 25 21:17:25 jack-desktop kernel: [  118.895127] usb 3-3: configuration #1 chosen from 1 choice
Mar 25 21:17:25 jack-desktop kernel: [  119.189237] Bluetooth: HCI USB driver ver 2.9
Mar 25 21:17:25 jack-desktop kernel: [  119.192360] usbcore: registered new driver hci_usb
Mar 25 21:17:39 jack-desktop kernel: [  132.709359] hfs: Filesystem was not cleanly

If instead of doing remove the bluetooth completely I can get bluetooth keyboard to be usable with this system. I did the following:

Changed

BLUETOOTH_ENABLED=1 to BLUETOOTH_ENABLED=1 in /etc/default/bluetooth.

I am using ubuntu 6.10

Thanks

---

