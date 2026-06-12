---
title: "System won't boot after WUBI install of 7.04"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Michael Grabbe on 2007-12-22
I came across an interesting problem on my main machine, today, that normally runs XP-Pro. I went thru the WUBI install process and everything appeared to go smoothly. The problem is that every time I chose to boot to Linux I saw several lines of text refering to "overcharge current " on all four USB ports. The machine then refused to go past that point. I had to shut it down and reboot to go into XP. So for the time being I've removed the WUBI install. At least I have my little VIA box to work with in Linux (7.10).  The main machine is based on a MSI 6582 (NEO II) motherboard with 1 GB of RAM and lots of peripherals - but only one device, an Olympus card reader.

Any ideas?

---

### Post by Nano Geek on 2007-12-22
The WUBI project is still relatively new. 
Why not use the normal install CD and also use the newer 7.10?

---

### Post by abn91c on 2007-12-25
> **Michael Grabbe said:**
> I came across an interesting problem on my main machine, today, that normally runs XP-Pro. I went thru the WUBI install process and everything appeared to go smoothly. The problem is that every time I chose to boot to Linux I saw several lines of text refering to "overcharge current " on all four USB ports. The machine then refused to go past that point. I had to shut it down and reboot to go into XP. So for the time being I've removed the WUBI install. At least I have my little VIA box to work with in Linux (7.10).  The main machine is based on a MSI 6582 (NEO II) motherboard with 1 GB of RAM and lots of peripherals - but only one device, an Olympus card reader.

Any ideas?

I had a similar problem with my Linux PC, it was that I left a jump drive attached to the USB port and the PC will freeze during reboots. you may want to remove the card reader if rebooting, especially if the media card is attached, Wubi may be trying to read the card as a hardrive and boot from it. It solved my issue when i did just that.

---

### Post by Michael Grabbe on 2007-12-26
Thanks for the replies.
1. I used WUBI because I though it would be an easy way to install Ubuntu without having to deal with repartioning my hard drive. The process gives me the willies. Just chicken I guess. I have read about the process some time ago but have not tried it. 

2. I did have the card reader hooked up, it was the only USB device attached (no card in it though). I'll disconnect it and give it another try.

---

### Post by Michael Grabbe on 2007-12-26
I tried downloading and reinstalling after I disconnected the card reader (and the camera which I had forgotten about). I still get the same message. I transcribed it here since I realized that my original post had an error in it: 

Booting  'Ubuntu'

(hd0,0)
Filesystem type is ntfs, partition type 0x7
   [LINUX-bzImage, setup=0x1x00, size=0x1a82cc]
   [LINUX-initrd @ 0x1f85e000, 0x7918a5 bytes]
Loading, please wait...
[   62.217996] hub 1-0:1.0: over-current change on port 7
[   62.325473] hub 1-0:1.0: over-current change on port 8
[   62.273207] hub 1-0:1.0: over-current change on port 1
[   62.378739] hub 1-0:1.0: over-current change on port 2


The keyboard has no effect on the system at this point and I have to use the restart button on the case to get back to the boot menu.

---

