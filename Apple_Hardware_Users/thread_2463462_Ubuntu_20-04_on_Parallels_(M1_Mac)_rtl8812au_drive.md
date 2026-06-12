---
title: "Ubuntu 20-04 on Parallels (M1 Mac) rtl8812au driver issue"
date: 2021-06-11
forum: Apple Hardware Users
---

### Post by billkent on 2021-06-11
Hi all, new Ubuntu user so apologies for the ignorance.  I have the Linksys AC1200 usb wireless adapter which is running the rtl8812au chipset.  I am running Ubuntu 20.04 within Parallels VM on a M1 Mac.  I have installed and updated Ubuntu.  I downloaded the rtl8812au driver package from GitHub, installed it and here is the results of my lsusb commandlsusbBus 003 Device 003: ID 203a:fffb Parallels Virtual Keyboard
Bus 003 Device 002: ID 203a:fffc Parallels Virtual Mouse
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 13b1:0045 Linksys WUSB6300 V2
Bus 002 Device 004: ID 203a:fffa Parallels Virtual Printer (Brother MFC-L3770CDW series - Fax)
Bus 002 Device 003: ID 203a:fffa Parallels Virtual Printer (Brother MFC-L3770CDW series)
Bus 002 Device 002: ID 203a:fffa Parallels Virtual Printer (Print to PDF (Mac Desktop))
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

With the adapter plugged in, here are the results of ifconfig:eth0      no wireless extensions.


lo        no wireless extensions.

Currently, Ubuntu must be sharing the wireless card in my M1 MacBook Pro as I have access.  Feel like I'm missing something simple, please advise.

Thanks,

---

### Post by ActionParsnip on 2021-06-11
What is the output of:
```

sudo lshw -C network

```
Thanks

---

### Post by QIII on 2021-06-11
Moved to Apple Hardware Users since your host is an Apple product.  Further, Parallels is a product for Apple and the hardware abstraction may be quite different from most VM software used with Linux hosts.

---

### Post by billkent on 2021-06-11
parallels@ubuntu-linux-20-04-desktop:~$ sudo lshw -C network
[sudo] password for parallels: 
  *-virtio2                 
       description: Ethernet interface
       physical id: 7
       bus info: virtio@2
       logical name: eth0
       serial: 00:1c:42:e9:83:80
       capabilities: ethernet physical logical
       configuration: autonegotiation=off broadcast=yes driver=virtio_net driverversion=1.0.0 ip=10.211.55.7 link=yes multicast=yes

---

### Post by scorp123 on 2021-06-11
> **billkent said:**
>   ifconfig:eth0      no wireless extensions.


Wrong interface name, in my opinion. If the RTL88xx driver compiled and loaded correctly, then the interface name should be something lile "wlan0".

Can you please check if the driver gets actually loaded? What's the output of this command:
```
sudo lsmod
```

---

