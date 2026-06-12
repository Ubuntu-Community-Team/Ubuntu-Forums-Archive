---
title: "[SOLVED] Mass Storage device (CF card) locks mouse on opening"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-10-02
This OS is Gutsy Gibbon 7.10.

I have a PQI 1GB CompactFlash card in a Nikon digital camera. When I set the camera to xfer the pix over to the computer, the mouse locks. Then the "regular" window opens asking if I want to xfer the photos. If I turn the camera battery off, the mouse unlocks and the computer goes back to "normal".

This is what I get after turning the camera off:

mark@Lexington:~$ fdisk -l

Disk /dev/sdb: 257 MB, 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x417fc429

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         984      251888    e  W95 FAT16 (LBA)

The 20GB hard drive is listed as missing in action!

---

### Post by tgalati4 on 2007-10-02
When the camera is plugged in:  

In a terminal, post the output of:

>cat /proc/interrupts

Sounds like the USB connection and the mouse are sharing the same interrupt.

Can you move the mouse to a different USB port?  Can you use a PS/2 mouse?

---

### Post by Mark_in_Hollywood on 2007-10-10
I removed the mouse from the usb hub, installed the PS/2 adapter and plugged the mouse into that port. The problem then resolved itself.

Thanks.

---

