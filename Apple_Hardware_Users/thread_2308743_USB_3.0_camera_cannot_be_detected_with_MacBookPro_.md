---
title: "USB 3.0 camera cannot be detected with MacBookPro + Ubuntu14.04"
date: 2016-01-05
forum: Apple Hardware Users
---

### Post by daichi2 on 2016-01-05
Hi there,

I'm using macbook pro(Retina, 15-inch, Mid 2014) + Ubuntu14.04 and
got in trouble with USB 3.0 camera.

Currently, it's not even detected.
I wonder the port connected with camera could be internally treated as USB 2.0 ...
In this case, what should I do ? I would like to use USB 3.0 port as USB 3.0 port, explicitly.

Accoding to the result of "lsusb -t", macbook has Bus 01 and 02.
Bus 01 and 02 seem to correspond with USB 2.0 and USB 3.0 respectively.
Therefore, whenever I connect the camera with macbook, Bus 01 seems to be used to control the camera.

Here, it is said that other laptops + Ubuntu 14.04 + Kernel 3.17.3 can be detected according to
info on web and my friend.
The camera I'm using is from my friend, so I don't think it's broken.

---------------------------------------------------------------------------------------

I describe the details here.

1. macbook pro + Ubuntu 14.04.2(Tried with both of Kernel 3.13.0 and 3.17.3 and had the same results)
2. macbook has 2 ports of USB 3.0
2. Would like to use USB 3.0 camera (ps4eye)
3. lsusb, dmesg and /dev showed the same results before and after I connected camera.
    Of course, I tried both ports.
&#12288; lsusb showed the follow.

Bus 002 Device 002: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 05ac:8289 Apple, Inc. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 003: ID 05ac:0262 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

4. According to the result of "lsusb -t", Bus 02 Port 1 seems to be recognized as USB 3.0 port.

/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
    |__ Port 4: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/14p, 480M
    |__ Port 8: Dev 2, If 0, Class=Hub, Driver=hub/3p, 12M
        |__ Port 3: Dev 6, If 0, Class=Vendor Specific Class, Driver=btusb, 12M
        |__ Port 3: Dev 6, If 1, Class=Wireless, Driver=btusb, 12M
        |__ Port 3: Dev 6, If 2, Class=Vendor Specific Class, Driver=, 12M
        |__ Port 3: Dev 6, If 3, Class=Application Specific Interface, Driver=, 12M
    |__ Port 12: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 12: Dev 3, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 12: Dev 3, If 2, Class=Human Interface Device, Driver=bcm5974, 12M

5. In order to check the port is not broken, I tried to connected USB 2.0 camera to both ports and it worked well.
&#12539;Case 1: connected camera to the first port and lsusb showed the follow
Bus 002 Device 002: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 05ac:8289 Apple, Inc. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 009: ID 046d:0808 Logitech, Inc. Webcam C600
Bus 001 Device 003: ID 05ac:0262 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

&#12539;Case 2: connected camera to another port and lsusb showed the follow
Bus 002 Device 002: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 05ac:8289 Apple, Inc. 
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 003: ID 05ac:0262 Apple, Inc. 
Bus 001 Device 010: ID 046d:0808 Logitech, Inc. Webcam C600
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

------------------------------------------------------------

lspci showed the follow.
Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI is used as the USB controller.
I have no idear about USB controller ... this controller is not supported yet ?

00:00.0 Host bridge: Intel Corporation Crystal Well DRAM Controller (rev 08)
00:01.0 PCI bridge: Intel Corporation Crystal Well PCI Express x16 Controller (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Crystal Well Integrated Graphics Controller (rev 08)
00:03.0 Audio device: Intel Corporation Crystal Well HD Audio Controller (rev 08)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05) <--USB controller&#12392;&#21516;&#12376;&#12418;&#12398;
02:00.0 Network controller: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter (rev 03)
03:00.0 Multimedia controller: Broadcom Corporation Device 1570
04:00.0 SATA controller: Samsung Electronics Co Ltd Apple PCIe SSD (rev 01)

Thank you very much in advance.

---

### Post by howefield on 2016-01-05
Thread moved to the "*Apple Hardware Users*" forum.

---

