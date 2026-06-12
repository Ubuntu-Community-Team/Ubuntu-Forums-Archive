---
title: "USB Hard Drive Not Detected"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-12-05
I recently bought a 500GB Seagate external (USB) HDD, and it won't even be detected by Ubuntu.

Most searches I did came up with SATA problems or mounting problems. My hard drive won't even show up in GParted. I have tried different plugin/unplug combinations, such as:

Turn on computer. Plug in HDD USB. Plug in HDD Power.
Plug in HDD USB. Plug in HDD Power. Turn on computer.
Plug in HDD USB. Turn on computer. Plug in HDD Power.

(btw - which is the "best" combination for that?) None of them worked. I've also tried different USB ports; however, I haven't tried all 3 combinations for all 4 USB ports. That much restarting seemed futile. :)

What should I be looking for? Is there any chance that I'll need drivers for my USB ports (they're on-board)? I didn't see anything relevant in dmesg, but I'm not really sure what I'm looking for, either. I'm using newly-installed Gutsy.

Thanks in advance.

---

### Post by Sarteck on 2007-12-05
When you plug in the hdd, what is the output of **dmesg | tail -n 100** ?

---

### Post by Hospadar on 2007-12-05
also when it's plugged in, what is the output of "lsusb"

I can't imagine it would be a usb driver issue, if anything else is working off your USB then I'd imagine this would work.  USB is a pretty stable feature.

Do you know how the drive is formatted?

---

### Post by tonyr1988 on 2007-12-05
It's formatted as one big ext3 partition (I'm using it purely for data to be used in Linuxboxen).

I don't have access to my computer right now, but I'll try those commands ASAP.

---

### Post by tonyr1988 on 2007-12-05
I have 4 USB ports on-board. When I plug the HDD into any of them (when it's already powered on), lsusb always says:

> Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

And dmesg doesn't change, so I'm assuming nothing happens.

When I plug in a 4-port hub, lsusb changes to:

> Bus 002 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

And **dmesg | tail -n 100** has this added:

> end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
usb 2-4: new high speed USB device using ehc1_hcd and address 2
usb 2-4: configuration #1 chosen from 1 choice
hub 2-4:1.0: USB hub found
hub 2-4:1.0: 4 ports detected

---

### Post by tonyr1988 on 2007-12-05
tiny bump...

---

### Post by tonyr1988 on 2007-12-06
More information:

-Turning the HDD on and off doesn't seem to help the detection.

-Plugging the HDD into the USB hub (which is detected and works) doesn't seem to help at all.

---

### Post by tonyr1988 on 2007-12-06
Anybody? How can a working hard drive not be detected by a working USB port? I could understand if it gave me some errors, but nothing....

---

### Post by Sarteck on 2007-12-06
Sorry, had to go to work--it was layout night at the paper, heh.

Have you installed usbmount?```
sudo apt-get install usbmount
```It helped me with a very similar problem with I/O Errors in dmesg.

---

### Post by tonyr1988 on 2007-12-06
I will try that now. Is there any particular order I need to worry about (do I plug in USB for HDD, plug in power for HDD, then turn on computer, etc?)?

---

### Post by philinux on 2007-12-06
USB stuff is meant to be hotplugged I think - just plug it in with pc on.

---

### Post by tonyr1988 on 2007-12-06
Installed it, restarted computer, plugged in hard drive, nothing.

lsusb is still empty, and nothing is in dmesg. :(

---

### Post by philinux on 2007-12-06
Have a browse to /media see if there anything recognisable as a ext HD in there

If the is then you could 

mount   /media/sdxx

---

### Post by tonyr1988 on 2007-12-06
In /media, there's a cdrom, floppy, and 7 usb. If I try to mount any of them, it tells me that it's not a block device.

---

### Post by philinux on 2007-12-06
Ok so what does 

[FONT="Courier New"]**lsusb**[/FONT] 

give

---

### Post by tonyr1988 on 2007-12-06
> **philinux said:**
> Ok so what does 

[FONT="Courier New"]**lsusb**[/FONT] 

give

lsusb always gives me:

> Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

No matter what USB port I plug the HDD into. But, I know that the ports work, because lsusb changes if I plug other USB devices in.

---

