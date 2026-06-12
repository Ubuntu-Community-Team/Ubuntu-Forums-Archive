---
title: "USB not being recognized in ubuntu"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by NuclearPeon on 2007-07-10
Greetings all,

Now I've looked through other topics regarding usb problems in ubuntu, but I haven't seen an answer to my problem. Yet.

I have a dual boot of Windows XP, but mainly I run Ubuntu Feisty 7.04.
USB works on my windows partition, but not ubuntu. When I plug in my memory stick, it lights up and all, but it's not immediately recognized. I've tried mounting it, but I get stuck.

So here's some info:

sudo lsusb:

```
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

dmesg | grep "usb"

```
[   31.325477] usbcore: registered new interface driver usbfs
[   31.325524] usbcore: registered new interface driver hub
[   31.325568] usbcore: registered new device driver usb
[   31.327911] usb usb1: configuration #1 chosen from 1 choice
[   31.429748] usb usb2: configuration #1 chosen from 1 choice
[   31.533610] usb usb3: configuration #1 chosen from 1 choice
[   31.637565] usb usb4: configuration #1 chosen from 1 choice
[   50.732484] usbcore: registered new interface driver acx_usb
```

which then goes on for a ways with lines like this:

```

[18497.352873] usb 4-6: new high speed USB device using ehci_hcd and address 2
[18508.886061] usb 4-6: device not accepting address 2, error -110
[18509.185813] usb 4-6: new high speed USB device using ehci_hcd and address 4
[18520.718997] usb 4-6: device not accepting address 4, error -110
[18521.018714] usb 4-6: new high speed USB device using ehci_hcd and address 6
[18532.551901] usb 4-6: device not accepting address 6, error -110
[18532.855634] usb 4-6: new high speed USB device using ehci_hcd and address 8
[18544.388814] usb 4-6: device not accepting address 8, error -110
```


It won't recognize my usb stick or my mp3 player when I plug it in. I've tried using these commands with both. I have multiple usb ports, but each one I've tried (at least 3 out of 4) has the same results.

Does anyone know what the issue is? 

Thanks.

---

### Post by NuclearPeon on 2007-07-11
Can anyone help me?

---

### Post by NuclearPeon on 2007-07-22
All of my usb connections worked in Windows, but my usb is not working in ubuntu, kubuntu, or ubuntu studio. Could this be a hardware problem or is it software-related?

---

### Post by alienexplorers on 2007-07-22
I had a simular problem, but it was windows that I had the USB problems with.  In ubuntu all my USB equipment works perfectly.

---

