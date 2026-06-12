---
title: "Trouble mounting USB drives"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by max24 on 2008-04-12
I'm having a bit of trouble mounting a couple of external usb hard drives.  Usually, when I connect the usb cable, the drive automatically mounts; but now when I connect it, the light on the drive illuminates, but nothing else happens.  One of the drives is ext3 and the other is FAT32.

Any insights would be greatly appreciated

---

### Post by edm1 on 2008-04-12
Can you plug them in then open the terminal and post the output of 'lsusb'.

---

### Post by max24 on 2008-04-12
This is the output of typing 'lsusb' into the terminal when the drives are plugged in


Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000

any ideas?

---

### Post by max24 on 2008-04-12
Not sure if this is relevant, but I just tried connecting one of them to a windows pc and it worked just fine.

---

### Post by Csylleste on 2008-04-12
What are the models of the drives? They may be having some issues with the generic drivers you are using through Linux.

---

### Post by warp99 on 2008-04-12
Try this:
```
sudo /etc/init.d/dbus restart
```
then plug the drives in. Are they seen? If not run:
```
dmesg |tail
```
and post the output to this thread.

---

### Post by max24 on 2008-04-13
Csylleste, 

here is the information for the drives:

1. Western Digital
model: wd1200u017-001

2. FireLite
model: #usbflb40-c

But how can I use the original drivers with ubuntu?

thanks,
-max

---

### Post by max24 on 2008-04-13
Warp99,

The drives were not recognized after the first step.

here is the output of 'dmesg |tail'

[ 9413.080000] usb 4-4: device descriptor read/64, error -71
[ 9413.296000] usb 4-4: new high speed USB device using ehci_hcd and address 44
[ 9413.704000] usb 4-4: device not accepting address 44, error -71
[ 9413.816000] usb 4-4: new high speed USB device using ehci_hcd and address 45
[ 9414.224000] usb 4-4: device not accepting address 45, error -71
[ 9446.708000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 9456.948000] eth1: no IPv6 routers present
[ 9547.104000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 9547.268000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 9563.884000] eth1: no IPv6 routers present

thanks,
-max

---

### Post by warp99 on 2008-04-13
Try the following:

```
lsmod |grep ehci_hcd
```

Is the module loaded? Remove and reload the module:

```
sudo rmmod ehci-hcd && sudo modprobe ehci-hcd
```

then try one of the drives, then

```
dmesg |tail
```

so we can check any messages.

---

### Post by max24 on 2008-04-13
Warp99,

First of all, thanks for your help.  I followed the steps you outlined above, and here is the output:

[21988.552000] usb 4-3: new high speed USB device using ehci_hcd and address 2
[21988.664000] usb 4-3: device descriptor read/64, error -71
[21988.880000] usb 4-3: device descriptor read/64, error -71
[21989.096000] usb 4-3: new high speed USB device using ehci_hcd and address 3
[21989.208000] usb 4-3: device descriptor read/64, error -71
[21989.424000] usb 4-3: device descriptor read/64, error -71
[21989.640000] usb 4-3: new high speed USB device using ehci_hcd and address 4
[21990.048000] usb 4-3: device not accepting address 4, error -71
[21990.160000] usb 4-3: new high speed USB device using ehci_hcd and address 5
[21990.568000] usb 4-3: device not accepting address 5, error -71

let me know what you think,
-max

---

### Post by reylafo on 2008-04-13
Try conecting to a different usb port. Sometimes is a hardware-connection thing.

---

### Post by waspbr on 2008-04-13
Are you by any chance using ndiswrapper?

---

### Post by max24 on 2008-04-13
Reylafo,

Good suggestion, but I've just now tried all 4 of the usb ports and no luck.

Thanks,
-max

---

### Post by max24 on 2008-04-13
Waspbr,

To tell you the truth, I don't know what ndiswrapper is.  I don't think I use it.  I will do some research and find out what ndiswrapper is so that I can give you a better answer.

Thanks,
-max

---

### Post by max24 on 2008-04-13
Well, now I'm really stumped.  Disregarding the hard drives in particular, the problem may be with the usb ports in general.  

Out of curiosity, I tried to plug in a printer and a usb mouse to see if they would be recognized: The light illuminated on the mouse, but nothing else happened...

The usb ports worked fine as of a week ago, and I haven't made any changes to my computer since then.

I reinstalled ubuntu today just to see if that would help, but no luck there.

So, I guess the problem has more to do with my usb ports on my computer.

---

### Post by warp99 on 2008-04-13
> **max24 said:**
> Well, now I'm really stumped.  Disregarding the hard drives in particular, the problem may be with the usb ports in general.  

Out of curiosity, I tried to plug in a printer and a usb mouse to see if they would be recognized: The light illuminated on the mouse, but nothing else happened...

The usb ports worked fine as of a week ago, and I haven't made any changes to my computer since then.

I reinstalled ubuntu today just to see if that would help, but no luck there.

So, I guess the problem has more to do with my usb ports on my computer.

Your don't need to reinstall Ubuntu because the USB drives are not seen, that was a big waste of time. Notice the message during 'dmesg |tail':

> 21988.552000] usb 4-3: new high speed USB device using ehci_hcd and address 2
[21988.664000] usb 4-3: device descriptor read/64, error -71
[21988.880000] usb 4-3: device descriptor read/64, error -71
[21989.096000] usb 4-3: new high speed USB device using ehci_hcd and address 3
[21989.208000] usb 4-3: device descriptor read/64, error -71
[21989.424000] usb 4-3: device descriptor read/64, error -71
[21989.640000] usb 4-3: new high speed USB device using ehci_hcd and address 4
[21990.048000] usb 4-3: **device not accepting address** 4, error -71
[21990.160000] usb 4-3: new high speed USB device using ehci_hcd and address 5
[21990.568000] usb 4-3: **device not accepting address** 5, error -71

That's the reason why I suggested you reload the module 'ehci-hcd' in a previous post. Your problem is common depending on your hardware setup:

> Q:  Why doesn't USB work at all? I get **"device not accepting address".**

A: This can be one of several problems:

    * High speed devices sometimes have problems with cables used to connect them. They're more sensitive to signal quality issues than older usb 1.1 full or low speed devices. If the device works OK at full speed on the same system, after you "rmmod ehci-hcd", this is likely the problem you're seeing. There are a lot of things you can do to change signal quality.
          o Use a different cable. Some are even marketed specifically for use with high speed devices. Most USB 1.1 cables work just fine at high speed, but the one you're using might be an exception (maybe it's been damaged).
          o Switch to a different USB connector on your computer. Back panel connectors are often right on the motherboard, with much care taken to preserve signal quality. A front panel connector probably doesn't use cabling designed with USB in mind; and its cable could be damaged by bending, baking or something else even when it's not routed through the power supply.
          o Use an external high speed hub. Those hubs have signal conditioning circuitry that may cover up certain flaws.
          o Make sure your device is using its own external power supply, or that its battery is fully charged. 
      You might be able to get the same device to work at high speed on a different machine.
    * You may have some problem with your PCI setup that's preventing your USB host controller from getting hardware interrupts. (Current Linux 2.6 kernels will actually tell you when they notice this problem; see the "dmesg" output.) When Linux submits a request, but never hears back from the controller, this is the diagnostic you'll see. To see if this is the problem, look at /proc/interrupts to see if the interrupt count for your host controller driver ever goes up. If it doesn't, this is the problem: either your BIOS isn't telling the truth to Linux (ACPI sometimes confuses these things, or setting the expected OS to windows in your BIOS), or Linux doesn't understand what it's saying.
    * Sometimes a BIOS fix will be available for your motherboard, and in other cases a more recent kernel will have a Linux fix. You may be able to work around this by passing the noapic boot option to your kernel, or (when you're using an add-in PCI card) moving the USB adapter to some other PCI slot. If you're using a current kernel and BIOS, report this problem to the Linux-kernel mailing list, with details about your motherboard and BIOS.

[http://www.linux-usb.org/FAQ.html#ts6](http://www.linux-usb.org/FAQ.html#ts6)


Here's some user feedback on possible fixes:

[http://www.linux-usb.org/notAcceptFeedback.html](http://www.linux-usb.org/notAcceptFeedback.html)

---

### Post by diablo75 on 2008-04-13
You might see if the BIOS on your PC is out of date....

---

### Post by waspbr on 2008-04-13
if you don't know what ndiswrapper  is then you are not using it,

---

### Post by cros13 on 2008-06-12
BUMP! sry!

Try "modprobe -r ehci_hcd"

temporary solution.

---

