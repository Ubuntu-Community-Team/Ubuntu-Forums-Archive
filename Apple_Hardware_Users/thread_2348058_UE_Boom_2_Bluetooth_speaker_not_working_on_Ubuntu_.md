---
title: "UE Boom 2 Bluetooth speaker not working on Ubuntu 16.04 LTS or 16.10"
date: 2016-12-31
forum: Apple Hardware Users
---

### Post by bpresles on 2016-12-31
I've a UE Boom 2 Bluetooth wireless speaker and I tried to make it working with my Ubuntu 16.04 LTS installed on a MacBook Pro 15" Late 2014.
I've also tested on Live USB key of Ubuntu 16.10 without more success. Also tested on a PC (Gigabyte Z87N, Core i7 4770k, NVidia GTX 760) with a BCM20702A0 (Broadcom) based bluetooth card.

On all these systems, it pairs correctly but don't display on sound settings.
I've tried to fix the issue using blueman and trying to select an audio profile for the device, but the fact is that while it's correctly detected as a speaker, and a "Audio profile" menu is available for the device, there is no audio profile available on this menu, and I don't know why.

Do you have any idea to help me fix this issue and make my UE Boom 2 speaker working on Ubuntu?

P.S: The UE Boom speaker is working perfectly fine on macOS or Windows

---

### Post by howefield on 2016-12-31
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by bpresles on 2017-01-02
Considering that I reproduced the issue on a PC also, it's not just related to Apple Hardware anymore and so the thread should be put back in the generic Hardware section in my humble opinion.

---

### Post by mark183 on 2017-01-02
I have the same issue with Ubuntu-MATE 16.04 and a neo2go Bluetooth speaker. Found this workaround which seems to consistently work for some, but only now and then in my case:
[http://askubuntu.com/questions/866530/autoconnecting-seamlessly-to-bluetooth-headset-16-04](http://askubuntu.com/questions/866530/autoconnecting-seamlessly-to-bluetooth-headset-16-04)

Blueman-manager sometimes displays "Failed to change profile to a2dp_sink", but even without this it would mostly not work.

---

### Post by jeremy31 on 2017-01-02
Some Broadcom bluetooth devices need firmware, post results for ```
dmesg | egrep -i 'blue|firm'
```

mark183
What has worked for me is to connect to the headset, then set the profile to off, then disconnect, connect and then change the profile to a2dp_sink but I haven't tried it with blueman
See the [bug report](https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1577197) for a link to a a2dp.py script that may help you with this

---

### Post by bpresles on 2017-01-03
Here the result of [COLOR=#000000][FONT=&quot]dmesg | egrep -i 'blue|firm'[/FONT][/COLOR], from the PC (I'll post the MacBook Pro result later):

[    0.134729] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    9.441172] Bluetooth: Core ver 2.21
[    9.441189] Bluetooth: HCI device and connection manager initialized
[    9.441193] Bluetooth: HCI socket layer initialized
[    9.441195] Bluetooth: L2CAP socket layer initialized
[    9.441207] Bluetooth: SCO socket layer initialized
[    9.588684] Bluetooth: hci0: BCM: chip id 63
[    9.604700] Bluetooth: hci0: Z87N-WIFI
[    9.605693] Bluetooth: hci0: BCM20702A1 (001.002.014) build 1479
[    9.606816] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-13d3-3404.hcd failed with error -2
[    9.606819] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-13d3-3404.hcd not found
[   13.443134] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.443135] Bluetooth: BNEP filters: protocol multicast
[   13.443138] Bluetooth: BNEP socket layer initialized
[   21.122669] Bluetooth: RFCOMM TTY layer initialized
[   21.122680] Bluetooth: RFCOMM socket layer initialized
[   21.122685] Bluetooth: RFCOMM ver 1.11

---

### Post by jeremy31 on 2017-01-03
See Pilot6's answer from [http://askubuntu.com/a/632348/300665](http://askubuntu.com/a/632348/300665) as you will need to download the windows file he linked to and search the inf file for 3404 to find the hex file to convert to BCM20702A1-13d3-3404.hcd and copy it to /lib/firmware/brcm

---

### Post by bpresles on 2017-01-03
After adding appropriate firmware, the output of [COLOR=#000000]dmesg | egrep -i 'blue|firm'[/COLOR] looks better:

$ dmesg | egrep -i 'blue|firm'
[    0.133562] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    9.269539] Bluetooth: Core ver 2.21
[    9.269559] Bluetooth: HCI device and connection manager initialized
[    9.269563] Bluetooth: HCI socket layer initialized
[    9.269566] Bluetooth: L2CAP socket layer initialized
[    9.269573] Bluetooth: SCO socket layer initialized
[    9.297495] Bluetooth: hci0: BCM: chip id 63
[    9.313500] Bluetooth: hci0: bpresles-Z87N-WIFI
[    9.314496] Bluetooth: hci0: BCM20702A1 (001.002.014) build 1479
[    9.933606] Bluetooth: hci0: BCM20702A1 (001.002.014) build 1479
[    9.949559] Bluetooth: hci0: Broadcom Bluetooth Device
[   13.162698] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.162700] Bluetooth: BNEP filters: protocol multicast
[   13.162704] Bluetooth: BNEP socket layer initialized
[   21.954624] Bluetooth: RFCOMM TTY layer initialized
[   21.954632] Bluetooth: RFCOMM socket layer initialized
[   21.954637] Bluetooth: RFCOMM ver 1.11



But I'm still unable to use my UE Boom 2 as a speaker (it's still not showing in sounds settings as output device).

Note that I tried to pair other bluetooth devices (but I don't have any other bluetooth speaker to test), like an iPhone (and used it with mobile connection tethering through bluetooth), a keyboard and a mouse, all these devices worked fine. So the bluetooth card itself seems to be working fine, just that when pairing with the UE Boom 2, I don't have it on sound settings and I'm unable to select an audio profile with Blueman (it doesn't list any profile to select).

---

### Post by bpresles on 2017-01-04
On the MacBook Pro, here the output of dmesg | egrep -i 'blue|firm':

[    0.265067] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.273443] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-9b] only partially covers this bridge
[    3.779240] usb 1-8.3: Product: Bluetooth USB Host Controller
[   10.523665] Bluetooth: Core ver 2.21
[   10.523687] Bluetooth: HCI device and connection manager initialized
[   10.523689] Bluetooth: HCI socket layer initialized
[   10.523691] Bluetooth: L2CAP socket layer initialized
[   10.523694] Bluetooth: SCO socket layer initialized
[   10.536606] Bluetooth: hci0: BCM: chip id 73 build 1036
[   10.537595] Bluetooth: hci0: BCM: product 05ac:8289
[   10.553595] Bluetooth: hci0: BCM20702B0 Generic USB Class 1 @ 20 MHz
[   11.823511] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.823514] Bluetooth: BNEP filters: protocol multicast
[   11.823518] Bluetooth: BNEP socket layer initialized
[   46.223563] Bluetooth: RFCOMM TTY layer initialized
[   46.223568] Bluetooth: RFCOMM socket layer initialized
[   46.223573] Bluetooth: RFCOMM ver 1.11

---

