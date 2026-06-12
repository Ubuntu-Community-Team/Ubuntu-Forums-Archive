---
title: "WUSB11v2.6 with ndiswrapper drivers causes crashes and sometimes does not work"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by cifdtruckie on 2008-01-02
I used ndiswrapper and got my WUSB11v2.6 to work, but I've been experiencing odd problems since.

* My system will randomly crash, especially while actively using internet.  Upon hard reboot, a message will sometimes pop up at the top of the screen (before the GUI loads).  It mentions something about wlan0, but goes away before I can read the whole thing.

* Sometimes after the hard reboot, I cannot access my wireless connection.

I've tried doing some investigating, and this is what I've found:

ndiswrapper
```
chris@chris-desktop:~$ ndiswrapper -l
netusb : driver installed
        device (077B:2219) present (alternate driver: at76_usb)
chris@chris-desktop:~$ 

```
I've tried blacklisting at76_usb (I don't remember the command to do that now, but someone told me how a while back), but that doesn't seem to make it work.  It says this whether or not the wireless is working.

When it wasn't working, opened the system log and read what happened when I disconnected and then reconnected the USB adapter:
[U]
On disconnect[/U]
```
Jan  1 23:02:05 chris-desktop kernel: [  201.829446] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/wireless/at76/at76c503.c: wlan0 disconnecting
Jan  1 23:02:05 chris-desktop kernel: [  201.829456] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/wireless/at76/at76c503.c: at76_usb disconnected
```
... which tells me that it's still using the at76_usb driver, even though I blacklisted it.


_On reconnect_
```
Jan  1 23:02:02 chris-desktop kernel: [  199.173071] usb 3-2: new full speed USB device using uhci_hcd and address 2
Jan  1 23:02:02 chris-desktop NetworkManager: <debug> [1199250122.978878] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_77b_2219_noserial'). 
Jan  1 23:02:02 chris-desktop kernel: [  199.382064] usb 3-2: configuration #1 chosen from 1 choice
Jan  1 23:02:03 chris-desktop NetworkManager: <debug> [1199250123.053035] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_77b_2219_noserial_if0'). 
Jan  1 23:02:03 chris-desktop NetworkManager: <debug> [1199250123.085056] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_77b_2219_noserial_usbraw'). 
```
This tells me that for some reason it does not recognize the device when I connect it, but does when I disconnect it.

When I run iwconfig wlan0 and the wireless is not working, I'm told that the device is not present.

That's really all I've figured out that I can check...  Can anyone help me fix this once and for all???

---

### Post by cifdtruckie on 2008-01-02
I did some more digging... 
I double-checked the blacklist and noticed that the blacklist entry for at76_usb had been commented out.
I removed the # and rebooted.  When I checked the system log, it showed that ndiswrapper had loaded up, and appeared to be working - iwconfig wlan0 showed the SSID of the router, and my wireless connection appeared in the network manager.  I could not, however, connect to the router.  My pings to 192.168.1.1 failed, even though it showed that I was connected.

I re-commented out the at76_usb blacklist entry and rebooted.  I looked through the system log even closer and discovered these 3 lines:
```
Jan  2 06:06:48 chris-desktop kernel: [ 1748.123641] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
Jan  2 06:06:48 chris-desktop kernel: [ 1748.123650] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
Jan  2 06:06:48 chris-desktop kernel: [ 1748.123664] ndiswrapper (mp_halt:259): device eb0bb500 is not initialized - not halting
```
This leads me to believe that the problem is with ndiswrapper itself... is there a way to re-install the ndiswrapper drivers?  Or am I completely off the mark?


These are the system log entries that I found for the device with at76_usb blacklisted.  Please note that it appears that the device is deactivated immediately after it is activated:
```
Jan 2 06:35:47 chris-desktop NetworkManager: <info> wlan0: Device is fully-supported using driver 'ndiswrapper'.
Jan 2 06:35:47 chris-desktop NetworkManager: <info> nm_device_init(): waiting for device's worker thread to start
Jan 2 06:35:47 chris-desktop NetworkManager: <info> nm_device_init(): device's worker thread started, continuing.
Jan 2 06:35:47 chris-desktop NetworkManager: <info> Now managing wireless (802.11) device 'wlan0'.
[B]Jan 2 06:35:47 chris-desktop NetworkManager: <info> Deactivating device wlan0.
Jan 2 06:35:47 chris-desktop NetworkManager: <WARN> nmdevice_802_11_wireless_set_essid (): error setting ESSID to '' for device wlan0: Invalid argument[/B]

```

---

### Post by cifdtruckie on 2008-01-02
Sorry for the bump... but I'm really anxious...

---

