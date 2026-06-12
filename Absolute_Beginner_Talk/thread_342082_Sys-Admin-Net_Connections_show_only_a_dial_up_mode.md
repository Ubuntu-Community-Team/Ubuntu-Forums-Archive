---
title: "Sys-Admin-Net Connections show only a dial up modem."
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Cyberbayne on 2007-01-19
My first installation of a Linux distro, i.e., Ubuntu Dapper, went off without a hitch. I get the dual boot menu at start-up. Dapper is responsive on all fronts - games, apps, terminal. I can read from, and burn to the optical drives. I can play CDs.

But, I cannot get the usb wireless adaptor to appear in the networking connections window.
Troubleshooting commands and their results are below:
___________________________________________________
lshw
*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

*-usb
                   description: Generic USB device
                   product: WUSB11v2.5 802.11b Adapter
                   vendor: Linksys, Inc.
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.32
                   serial: 1
                   capabilities: usb-1.10
                   configuration: driver=prism2_usb maxpower=500 mA speed=12.0MB/s
______________________________________________
lsmod
prism2_usb             77060  0
______________________________________________
sudo iwlist ath0 scan
ath0      Interface doesn't support scanning.
______________________________________________
sudo iwconfig
lo        no wireless extensions.
sit0      no wireless extensions.
wlan0     no wireless extensions.
______________________________________________
sudo ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7896 (7.7 KiB)  TX bytes:7896 (7.7 KiB)
_______________________________________________
Bus 001 Device 003: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x066b Linksys, Inc.
  idProduct          0x2212 WUSB11v2.5 802.11b Adapter
  bcdDevice            1.32
~snip~
Device Status:     0x0000
  (Bus Powered)
____________________________________________________
I have tried booting with the adaptor connected, and booting without it and connecting it after the boot (a la PnP). No difference. I tried rebooting the router while the adaptor was connected. Nothing.
_______________________________________________________

If I'm reading this right, the adaptor is being detected by the OS. The driver is present and functional. But the adaptor is not registering in the networking connections window, which is where it has to activated from(yes/no?).  As you can see, I've put some effort into this, but my brain hurts and i'm starting to get crosseyed. Am I close? Way off base? What's next?
__________________________________________________________________

Question added to Support/Networking board - maybe this is not right for Absolute Beginner Board...

---

### Post by riven0 on 2007-01-19
Is there any way you can hook up to a wired connection and install the network manager? That corrects most people's problems with wireless connections.

---

### Post by Cyberbayne on 2007-01-21
i did install the network-manager-gnome. It put the icon up next to the date, and said no network detected. 
Anyway, I've given up and done a clean install of Edgy with a PCI adaptor instead of the USB adaptor. I'm not on the net yet, but at least the wireless adaptor is detected by the connection manager and the driver is present. I could even ping 127.0.0.1 :) But that's it :(

Here's my forum post if you're interested...

[http://www.ubuntuforums.org/showthread.php?t=343482](http://www.ubuntuforums.org/showthread.php?t=343482)

---

