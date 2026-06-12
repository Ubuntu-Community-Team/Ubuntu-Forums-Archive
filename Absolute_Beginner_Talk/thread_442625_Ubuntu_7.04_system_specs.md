---
title: "Ubuntu 7.04 system specs"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by linuxhippy on 2007-05-13
I just started using the AMD64 bit Ubuntu 7.04 on my 64Athlon.  What are the system specs for this OS as far as memory?

---

### Post by RomeReactor on 2007-05-13
Hi. This is from the [Ubuntu]("http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition") page:

> System Requirements

Ubuntu is available for PC, 64-Bit and Mac architectures. CDs require at least 256 MB of RAM. Install requires at least 2 GB of disk space.



---

### Post by mikewhatever on 2007-05-13
System specs? Not sure what's that. The minimum requirement is 256 MB of RAM for standard Ubuntu installation. Hope it was close to what you wanted.

---

### Post by linuxhippy on 2007-05-13
Yup, that's what I wanted (system specifications or requirements).  I have 512 MB of RAM that's integrated with my video that's 32 MB....the xfce system meter says I have an available 468 MB of RAM.  It seems to work ok until the memory fills up.

Any ideas on how to minimize the used memory?

---

### Post by mikewhatever on 2007-05-13
What happens when the memory 'fills up'? How large is your swap partition?

---

### Post by linuxhippy on 2007-05-14
My swap space is about twice my memory or 1 GB.  Ubuntu may not be mounting my swap partition that I informed it about during install (I specified the advanced partition setup rather than the default of using my entire harddrive).  I'll have to check that when I am at my Linux box.

When the memory fills up the computer almost grinds to a halt (I see the memory meter at it's 100% level), the mouse moves choppily slow, and keyboard shortcuts won't work.  I'm not able to close down unused applications either.

---

### Post by linuxhippy on 2007-05-14
ok, looks like my swap partition is not getting recognized.  I have no idea why Ubuntu put this in etc/fstab:

UUID=830088b0-f22d-4c86-89f8-92fe0ea1af07 none            swap    sw              0       0

I changed it to this (it was in Fedora's /etc/fstab):

/dev/hda6               swap                    swap    defaults        0 0

This is my hard drive with fdisk -l:
 
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2055    16506756    7  HPFS/NTFS
/dev/hda2   *        2056        2068      104422+  83  Linux
/dev/hda3            2069        5128    24579450   a5  FreeBSD
/dev/hda4            5129       24321   154167772+   5  Extended
/dev/hda5            5129        7678    20482843+  83  Linux
/dev/hda6            7679        7805     1020096   82  Linux swap / Solaris
/dev/hda7            7806        7869      514048+  83  Linux
/dev/hda8            7870       10480    20972826   83  Linux
/dev/hda9           10481       13091    20972826   83  Linux
/dev/hda10          13092       15702    20972826    b  W95 FAT32
/dev/hda11          15703       18313    20972826   83  Linux
/dev/hda12          18314       21315    24113533+  83  Linux
/dev/hda13          21316       22098     6289416   83  Linux
/dev/hda14          22099       24321    17856216   83  Linux

swapon -a set up my swap space for this session.  Since it's setup now in fstab, will it continue to setup swap on reboot?

---

### Post by linuxhippy on 2007-05-14
fixed!!  I just rebooted and sudo free shows this:

Swap:      1020088      37236     982852

Oh, I used sudo swapon -a above and that fixed everything once /etc/fstab was correct.

:guitar:

---

