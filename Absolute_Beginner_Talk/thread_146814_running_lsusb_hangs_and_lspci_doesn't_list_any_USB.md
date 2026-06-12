---
title: "running lsusb hangs and lspci doesn't list any USB ports?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by jtp51 on 2006-03-19
When I run:

lsusb or sudo lsusb

the terminal hangs and I have close the terminal manually (unable to type exit).

When I run:

lspci

I return the following list:

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 10)
0000:00:02.0 PCI bridge: ATI Technologies Inc: Unknown device 5a34
0000:00:12.0 IDE interface: ATI Technologies Inc: Unknown device 4379
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0092 (rev a1)
0000:02:01.0 Communication controller: Lucent Microelectronics: Unknown device 0620
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)


So, in order to have USB, I need to fix the reason why I am receiving so many Unknown device messages.

Any direction or assistance is greatly appreciated.

Thanks,

---

### Post by Pragmatist on 2006-03-19
Please give the output of these commands:
```
dmesg |grep usb >> outputfile
```
```
cat /var/log/messages |grep usb >> outputfile
```
```
lshal |grep usb >> outputfile
```

Then attach the file called "outputfile" in your next post here.

---

### Post by marshcast on 2008-06-07
I have the same problem, although i don't have the unknown device entries in lspci...

my dmesg|grep usb is here... any chance someone could have a look & let me know if it's fixable?

I have a Dell Optiplex320 running fiesty, hp1018 printer (plugged in) and usb keyboard & mouse.

This has also been an issue with another machine - optiplex320 too, hp 1020 running gutsy.

fingers crossed...

edit -- sorry -- 2 files - misread & confused - will upload outputfile now...

---

### Post by marshcast on 2008-06-07
outputfile

---

### Post by marshcast on 2008-06-07
outputfile was too big -- how this? (sorry - am moking a pigs ear of this... files must have an extension to upload here (for future ref ;)))

---

