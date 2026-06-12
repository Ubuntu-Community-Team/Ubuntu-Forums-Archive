---
title: "Wireless USB not working after update"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by wr0x2 on 2006-10-25
My friend has a wireless usb adaptor that he was using until it was broken by the last update. The device isn't even listed under networking. Here's the output from dmesg when I plug it in:

```

sjason2007@sjason2007-laptop:~$ dmesg | tail
[17181239.984000] usb 1-1: new full speed USB device using uhci_hcd and address 11
[17181240.104000] usb 1-1: device descriptor read/64, error -71
[17181240.328000] usb 1-1: device descriptor read/64, error -71
[17181240.544000] usb 1-1: new full speed USB device using uhci_hcd and address 12
[17181240.664000] usb 1-1: device descriptor read/64, error -71
[17181240.892000] usb 1-1: device descriptor read/64, error -71
[17181241.108000] usb 1-1: new full speed USB device using uhci_hcd and address 13
[17181241.516000] usb 1-1: device not accepting address 13, error -71
[17181241.628000] usb 1-1: new full speed USB device using uhci_hcd and address 14
[17181242.036000] usb 1-1: device not accepting address 14, error -71

```

---

### Post by TitusDalwards on 2006-10-25
could you please control that usb modules installed correctly while booting the syustem.

```
lsmod|grep ....
```

---

### Post by wr0x2 on 2006-10-25
USB in general should be working, because a USB mouse and keyboard work when plugged in. Also, the wireless adaptor lights up when it's plugged in.

---

