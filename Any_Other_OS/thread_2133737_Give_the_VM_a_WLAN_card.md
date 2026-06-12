---
title: "Give the VM a WLAN card?"
date: 2013-04-09
forum: Any Other OS
---

### Post by createdcreature on 2013-04-09
Hi guys! I have just installed Kali Linux in a VirtualBox VM, and want to penetration test MY OWN wifi network. In order for this to be possible I need to give the VM a WLAN card. How would I go about doing this? All of the network adapters available are just LAN cards (AMD PCNET 2 PCI, AMD PCNET 3 FAST PCI Family Fast Ethernet, Intel Gigabit Workstation, Intel Gigabit Server, Intel Gigabit Datacenter server, and Paravirtualized virtio-net). These are all wired, even though I have a fully functional WLAN card on the host! I have tried bridging through the WLAN card, but it can still only come through as one of those lan adapters. Any ideas? I have heard about getting a USB/Serial WLAN adapter, and using the USB function to get it into the VM, but I don't really want to do that. Any help would be greatly appreciated.

Thanks!

---

### Post by mikewhatever on 2013-04-09
What made you think you could do penetration testing from a VM in the first place? Usually, an OS installed in a VM, only sees virtual hardware, which makes wlans on the host irrelevant.
For more info, check out [http://www.kalilinux.net/community/](http://www.kalilinux.net/community/)

---

### Post by Elfy on 2013-04-09
*Thread moved to **Other OS/Distro Support**.*

---

