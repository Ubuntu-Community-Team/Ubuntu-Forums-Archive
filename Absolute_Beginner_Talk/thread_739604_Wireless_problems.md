---
title: "Wireless problems"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by trelka on 2008-03-29
I just bought a Gateway T-1625 notebook which contains a Realtek RTL8187 built in wireless card.  I have  constructed it as a dual boot and the wireless card works fine in Vista, but I do not think it's recognized in Ubuntu 7.10.  When I go to the Network settings section, I only get Wired and Modem connections, no wireless.  Putting ubuntu 7.10 on a new machine has proven challenging thus far.  Can anyone help me with what to do next?  

Thanks,

Darin Trelka

---

### Post by Papa-san on 2008-03-29
I know that you'll probably need to post the output for these commands:
```
sudo lshw -C network
iwconfig
ifconfig

```(Separately, though. one at a time...)
also:
Try this link: [HERE]("http://globalsyzygy.wordpress.com/2007/12/30/fixing-your-rtl8187-netgear-wg111v2-in-ubuntu/")

---

### Post by rkd on 2008-03-29
This page

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek)

says that you have to use ndiswrapper for the 8187B and has pointers to installation instructions.  

I don't know whether yours is 8187B or something else.  Before following the instructions linked to from that page, verify that your device is 8187B.  I think sudo lsusb will let you check that, since that page says the 8187B is a USB device.  If you don't find it in the lsusb output (look for ID 0bda:8189), look at the output from lspci to see whether you see the device there.

---

