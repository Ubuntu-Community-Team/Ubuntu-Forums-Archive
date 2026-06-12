---
title: "macbook pro 5,3 isight woes under Oneiric"
date: 2011-10-31
forum: Apple Hardware Users
---

### Post by molon on 2011-10-31
Hi,

I am running Ubuntu 11.10 (64bit) on a MacBook Pro 5,3. The machine has successively run Lucid, Maverick and Natty. Everything is running mostly fine (thank you, guys!) except for the iSight camera.

The camera used to work fine with Lucid, erratically with Maverick and got lost since Natty. This is a dual-boot machine, on the OSX side it has always been Snow Leopard (also 64bit).

I have tried to get iSight back working and for that I have followed directions [here]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight") and in a number of forums describing the problem. I have tried nearly everything, except for recompiling uvcvideo, since I am not sure that's necessary.

I have, for example, recompiled isight-firmware-tools and then extracted the firmware (according to the previous link, this should work even with Snow Leopard firmware). It seems to be correctly extracted and I can actually find the isight.fw file in /lib/firmware:[INDENT]     > sudo ift-extract -a /lib/firmware/AppleUSBVideoSupport
    ** Message: Found firmware signature at offset 0x29C8.
    ** Message: Firmware extracted successfully in /lib/firmware/isight.fw
    ** Message: Firmware version 2.38.83 (0x02.0x26.0x53)
    ** Message: Apply patch 0 : Fix device descriptor
    ** Message: Apply patch 1 : Fix interface assocation descriptor
    ** Message: Apply patch 2 : Fix video interface collection
    ** Message: Apply patch 3 : Fix video streaming device qualifier
    ** Message: Apply patch 4 : Fix video control interface descriptor
    ** Message: Apply patch 5 : Fix video streaming interface descriptor
    ** Message: Firmware patched successfully 
[/INDENT]The AppleUSBVideoSupport is a copy of the one in the OSX side.
However, ift-load seems unhappy about it:[INDENT]     > sudo /usr/local/lib/udev/ift-load -f /lib/firmware/isight.fw
    ift-load: Failed to init firmware loading
    ift-load: Failed to upload firmware to 0x05AC:0x8507 
[/INDENT]BTW, the product id by default in the ift code is 8300, but my iSight seems to be 8507:[INDENT]     > sudo lsusb -v -d 05ac:
    Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
    Device Descriptor:
    bLength 18
    bDescriptorType 1
    bcdUSB 2.00
    bDeviceClass 239 Miscellaneous Device
    bDeviceSubClass 2 ?
    bDeviceProtocol 1 Interface Association
    bMaxPacketSize0 64
    idVendor 0x05ac Apple, Inc.
    idProduct 0x8507 Built-in iSight
    bcdDevice 4.19
    iManufacturer 1 Apple Inc.
    iProduct 2 Built-in iSight
    iSerial 3 8J9BA1B9Z6V13A00
    bNumConfigurations 1 
[/INDENT]That was the result after a warm boot in linux (coming from a cold boot in OSX), the result of the command is longer after a cold boot in linux (I can attach it if needed) but in both cases the idProduct is the same and so are the bus and the device numbers.

So, I modified the load.h file in the ift code to reflect this, as well as the isight.rules file in the /etc/udev/rules.d/ directory.

After all these changes I find in the kern.log file:[INDENT]Oct 31 21:36:20 pmacmol2 kernel: [ 25.079345] Linux video capture interface: v2.00
Oct 31 21:36:20 pmacmol2 kernel: [ 25.082450] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8507)
Oct 31 21:36:20 pmacmol2 kernel: [ 25.082467] uvcvideo: No valid video chain found.
Oct 31 21:36:20 pmacmol2 kernel: [ 25.082716] usbcore: registered new interface driver uvcvideo
Oct 31 21:36:20 pmacmol2 kernel: [ 25.082718] USB Video Class driver (v1.1.0) 
[/INDENT]I get the "No valid video chain found" message and no /dev/video0.
I don't see any message in the system logs regarding ift-load, so I don't know if it is actually called at boot time. Nevertheless, if I try to manually load the firmware, this is what I still see:[INDENT]> sudo /usr/local/lib/udev/ift-load -f /lib/firmware/isight.fw
ift-load: Failed to init firmware loading
ift-load: Failed to upload firmware to 0x05AC:0x8507
[/INDENT]Sometimes, however, after a warm boot in linux (coming from OSX) I get a different message:[INDENT]Oct 31 23:29:16 pmacmol2 kernel: [   24.796315] uvcvideo: Found UVC 1.00 device Built-in iSight (05ac:8507)
Oct 31 23:29:16 pmacmol2 kernel: [   24.801959] input: Built-in iSight as /devices/pci0000:00/0000:00:04.1/usb1/1-4/1-4:1.0/input/input6
Oct 31 23:29:16 pmacmol2 kernel: [   24.803278] usbcore: registered new interface driver uvcvideo
Oct 31 23:29:16 pmacmol2 kernel: [   24.803280] USB Video Class driver (v1.1.0)
[/INDENT]In these cases the /dev/video0 is created and the camera seems to be "detected" by various programs (cheese, gstreamer-properties, ekiga, skype) but remains useless: nothing is taken in video, the green light is never on. Trying to load the firmware in these cases results in the same message than above.

I would very much appreciate if someone can show me a way to get the camera working.

Best,

---

### Post by bohemier on 2011-11-08
Hi! I'm at the first stages of debugging mine on a MacBook Pro 5,1 but I can tell you that it was working fine on a fresh Oneiric install (used skype with it a few times) and then after a few weeks, it's got lost (no device detected anymore). 

Don't know what caused it... I'll investigate more, and try your suggestions...

Thanks for posting this info.

---

### Post by bohemier on 2011-11-09
Got it to work again by installing the firmware as per:

sudo apt-get install isight-firmware-tools
sudo ift-extract -a AppleUSBVideoSupport

Then shutdown completly. After next boot, it worked again. Don't know why it stopped working in the first time though...

Regards

---

### Post by molon on 2011-11-13
The problem is that after booting (cold or warm) is just a matter of chance whether the iSight will work or not. I haven't found a way to reproduce one or the other. Unfortunately, most of the times, iSight does not work after booting.

It is a pity that anybody more knowledgeable has replied to this post or to previous posts by other users. I just say it is a pity, I understand they have better things to do.

---

### Post by bohemier on 2011-11-13
> **molon said:**
> The problem is that after booting (cold or warm) is just a matter of chance whether the iSight will work or not. I haven't found a way to reproduce one or the other. Unfortunately, most of the times, iSight does not work after booting.

It is a pity that anybody more knowledgeable has replied to this post or to previous posts by other users. I just say it is a pity, I understand they have better things to do.

In my case, It's been working after every boot since I did the update described above...

---

