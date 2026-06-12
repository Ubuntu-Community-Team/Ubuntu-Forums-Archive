---
title: "Ubuntu 15.04 Bluetooth issues on a Macbook Pro Early 2015 (12,1)"
date: 2015-06-14
forum: Apple Hardware Users
---

### Post by sundragon2 on 2015-06-14
I have been using a bluetooth mouse (HPx4000b) to get around trackpad issues. I paired the mouse with Yosemite and it automatically worked with Ubuntu (nice) but when I look at System Settings >Bluetooth its greyed out but it's definitely working how I have no idea how, haha.


This is what I found:


$ hcitool dev
Devices:
$ sudo service bluetooth status
&#9679; bluetooth.service - Bluetooth service
Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
Active: inactive (dead)

Not sure how Bluetooth is inactive yet works.

---

### Post by raywang2 on 2015-06-24
It seems no one response to this topic...

---

### Post by sicvolo on 2015-07-21
I've noticed that ubuntu fails to reset devices to their default state on reboot/shutdown. Probably has to do with Apple's non-standard EFI implementation. The SSD reader seems to be afflicted with the similar curse you have with bluetooth. 
BTW My bluetooth service is running, but it fails to discover any devices and reports GATT as disabled.

Edit: GATT was a red herring, due to the old bluez version in the official distro. Get bluez v5  from [here]("https://launchpad.net/~vidplace7/+archive/ubuntu/bluez5") and the GATT problem goes away. Bluetooth however still is not recognized. 
I suspect that usermode stuff is to blame. Kernel seems to report it fine during boot, but something in the usermode packages makes it fall over.

what happens when you run lspci --nn and usb-devices?

---

### Post by mj0g on 2015-07-22
Apparently has a Broadcom USB Bluetooth adaptor:

> 
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.01 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=05ac ProdID=8290 Rev=00.90
S:  Manufacturer=Broadcom Corp.
S:  Product=Bluetooth USB Host Controller
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 5 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)


dmesg reports the following:

> [    1.429096] usb 1-3: new full-speed USB device number 2 using xhci_hcd
[   16.622262] usb 1-3: device descriptor read/64, error -110
[   31.036154] usb 1-3: new full-speed USB device number 4 using xhci_hcd
[   31.164864] usb 1-3: No LPM exit latency info found, disabling LPM.
[   31.167216] usb 1-3: New USB device found, idVendor=05ac, idProduct=8290
[   31.167218] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   31.167220] usb 1-3: Product: Bluetooth USB Host Controller
[   31.167221] usb 1-3: Manufacturer: Broadcom Corp.
[   31.167378] usb 1-3: ep 0x85 - rounding interval to 64 microframes, ep desc says 80 microframes
[   31.167381] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes
[   31.232695] input: Broadcom Corp. Bluetooth USB Host Controller as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:05AC:8290.0006/input/input7
[   31.288159] input: Broadcom Corp. Bluetooth USB Host Controller as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.1/0003:05AC:8290.0007/input/input8


---

### Post by Lucas_Thomas on 2015-09-08
I am having this exact same issue. My blue-tooth devices are "working" in the sense they are connecting and I'm able to use them, mostly. My magic mouse can only move the mouse. I can't scroll or do any type of gesture. My magic keyboard works as it should. When I go into System Setting -> Bluetooth, it shows as disabled - which is the same issue sundragon2 is reporting. Also, my Wi-Fi doesn't work at all.   

Has anyone found any other information to get a better experience with these Apple Bluetooth devices within Ubuntu?

---

### Post by mj0g on 2015-09-09
I'm not even getting the device recognised as being present beyond the kernel probing at boot:

> 
[    1.869553] usb 1-3: new full-speed USB device number 2 using xhci_hcd
...
[    2.004387] usb 1-3: New USB device found, idVendor=05ac, idProduct=8290
[    2.004388] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.004389] usb 1-3: Product: Bluetooth USB Host Controller
[    2.004390] usb 1-3: Manufacturer: Broadcom Corp.
[    2.004478] usb 1-3: ep 0x85 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.004480] usb 1-3: ep 0x86 - rounding interval to 64 microframes, ep desc says 80 microframes
...
[    2.425178] hid-generic 0003:05AC:8290.0001: input,hidraw4: USB HID v1.11 Keyboard [Broadcom Corp. Bluetooth USB Host Controller] on usb-0000:00:14.0-3/input0
[    2.425259] input: Broadcom Corp. Bluetooth USB Host Controller as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.1/0003:05AC:8290.0002/input/input7
...
[   10.254634] usbcore: registered new interface driver btusb
...
[   16.642700] usb 1-3: device descriptor read/64, error -110


Presumably that last line is bad.

Nothing ever shows up in `hcitool dev`.

Running hid2hci seems to fail, so maybe that needs to be updated?

Turns out Broadcom changed the USB interface on the BT chip used in the MBP12,1 and hence the btusb kernel module needs to be patched. There's a hack on the linux-bluetooth mailing list that will get it working (while breaking support for all other BT adaptors) if you know how to recompile a kernel, otherwise you'll need to wait until a proper fix makes it into the kernel.

---

### Post by sundragon2 on 2015-09-17
> **mj0g said:**
> Turns out Broadcom changed the USB interface on the BT chip used in the MBP12,1 and hence the btusb kernel module needs to be patched. There's a hack on the linux-bluetooth mailing list that will get it working (while breaking support for all other BT adaptors) if you know how to recompile a kernel, otherwise you'll need to wait until a proper fix makes it into the kernel.

I've just updated to 4.2 unstable from August 30th (4.2.0-040200-generic) and Bluetooth still doesn't work. Issues with the trackpad and function keys have been resolved as far as I can tell, which is awesome. I have a feeling Bluetooth won't be working in Ubuntu 15.10 Wily Werewolf out of the box.

---

### Post by mj0g on 2015-10-20
Proper support for the MBP12,1's Bluetooth controller was just [applied to the bluetooth-next repo]("https://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/?id=2af82d55442672e1429e36439a89e17896c2fb66"), so hopefully this will be fixed in Linux 4.3 or 4.4.

---

### Post by enrico12 on 2015-10-20
SunDragon,

have you tried Ubuntu 15.10? BT works fine?

---

### Post by raphael8 on 2015-11-08
> **enrico12 said:**
> SunDragon,

have you tried Ubuntu 15.10? BT works fine?

I have an ealy 2015 MBP 12.1, just installed 15.10 and no BT possible. If someone has an idea I'd like to solve it.

No idea what I did... But my Magic Mouse 2 works now. Only the scroll isn't working.

I realized my mouse was working after disabling enabling my network connections.

---

### Post by mj0g on 2015-11-26
Quick update: I just tested linux 4.4-rc2 from the Ubuntu mainline kernel PPA and Bluetooth seems working fine on my MBP 12,1. Apparently Xenial will be based on 4.4, so the next release should support Bluetooth out of the box.

---

### Post by kostas-chatzi on 2015-11-28
I can confirm that bluetooth (and everything else I've tried :D) works fine with[COLOR=#000000]linux 4.4-rc2.

Only problem: my bluetooth mouse ([/COLOR]Microsoft Bluetooth Notebook Mouse 5000) is quite laggy, way more than the same mouse is on my old Dell XPS 13.
evhz from [this page]("https://wiki.archlinux.org/index.php/Mouse_polling_rate") shows 350+ Hz polling rate, so that's not the problem.

Anybody else experiencing this?

---

### Post by knasher2 on 2016-03-02
> **kostas-chatzi said:**
> Anybody else experiencing this?

Yeah, I get the same thing when using an Apple mouse.

---

