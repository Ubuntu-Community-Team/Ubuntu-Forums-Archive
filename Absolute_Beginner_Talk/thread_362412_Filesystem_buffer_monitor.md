---
title: "Filesystem buffer monitor"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by ac7ss on 2007-02-15
I use usb drives and other removable SS media. I need to be able to monitor my Filesystem buffer status so that I don't overrun or so that I know how much longer I will have to wait before I can shut down or un-mount the drive.

The two cases are
[LIST]
[*]USB thumb drive on older (P400) Edgy Desktop
[*]Micro SD in adaptor (serial protocol) in PCMCIA reader on laptop (AMD 1200)
[/LIST]

I use the USB for general moving files about, and back it up on the older PC. It refuses to unmount (device is busy) fsck just sits there. (Or whatever the buffer flush is.)

I use the uSD for music on my phone, with a large batch of transfers, it will lock up, state it is read only and refuse to unmount (Same message.)

Is there a way to monitor this status?
Thank you.

---

### Post by mssever on 2007-02-15
Typing mount will show you the current status of all mounted partitions.

I've found that remounting a partition read only sometimes helps. When it comes to bust partitions, anything program that is doing anything with the partition or that has its working directory set to the partition will mark it as busy and keep you from unmounting it. I don't know any way to find out what's keeping it busy, other than manually examining each running program.

---

