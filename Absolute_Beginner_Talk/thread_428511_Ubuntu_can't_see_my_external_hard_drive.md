---
title: "Ubuntu can't see my external hard drive"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Mikkel Nielsen on 2007-04-30
Hear thee hear thee :)

Ubuntu can't see my external hard drive which is kind of a big problem since all my music and some other stuff is on it.

This is from the terminal confirming that ubuntu doesn't recognize the hard drive, only my USB connected mouse:

mikkel@Mikkel:~$ lsusb
Bus 001 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 001 Device 001: ID 0000:0000

How do i gain access to the external hard drive?

(It's not USB 2.0 but the (good) old USB 1.1 or what it's called.)

Peace, Mikkel

---

### Post by taurus on 2007-04-30
What's the output of this command from a terminal, after plugging in your external harddrive and turning it on?

```
sudo fdisk -l
```

---

### Post by Mikkel Nielsen on 2007-04-30
The output is:

mikkel@Mikkel:~$ sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1460    11727418+   7  HPFS/NTFS
/dev/hda2            1960        2491     4273290    f  W95 Ext'd (LBA)
/dev/hda3            1461        1959     4008217+  83  Linux
/dev/hda5            1986        2491     4064413+   7  HPFS/NTFS
/dev/hda6            1960        1985      208782   82  Linux swap / Solaris

Partition table entries are not in disk order

Does this help ?

---

### Post by Mikkel Nielsen on 2007-04-30
I guess this should also show my external 80 Gb hard drive

---

### Post by taurus on 2007-04-30
Which release are you running?  

What manufacture is your USB harddrive?  

Does it work in Windows (does Windows detect/see it)?

---

### Post by Mikkel Nielsen on 2007-04-30
I'm running the latest release (7.04 Feisty fawn ).

The hard drive was originally the hard drive of a laptop computer (Fujitsu Siemens), but when it broke the hard drive survived and I bought a kind of a case for it to hook it up with my desktop computer as an external hard drive which worked just fine with windows.

I don't know what the manufacturer of the hard drive itself is - is that essential?

---

