---
title: "OCZ RevoDrive PCI-E, poor performance on ubuntu"
date: 2012-09-28
forum: Any Other OS
---

### Post by lukasz bandzarewicz on 2012-09-28
Several months ago I bought OCZ RevoDrive PCI-E SSD 110GB 530/435MB/s and I installed Linux on it (Mint 12 distribution). I had several problem with the boot partition but I managed to workaround this problem with boot part installed on a conventional disk.

I suspect that I have something wrong with my linux configuration because I did a simple benchmark for my drive and the results are far away from the specification (read should be about 500MB/s):

[FONT="Courier New"]sudo hdparm -tT /dev/sda

/dev/sda:
Timing cached reads: 29506 MB in 2.00 seconds = 14770.52 MB/sec
Timing buffered disk reads: 700 MB in 3.01 seconds = 232.85 MB/sec
[/FONT]
For a comparison in my laptop T410s I have Samsung MMCRE28G8MXP-0VBL1 and the benchmark results for this drive are:

[FONT="Courier New"]$ sudo hdparm -tT /dev/sda

/dev/sda:
Timing cached reads: 6668 MB in 2.00 seconds = 3334.77 MB/sec
Timing buffered disk reads: 506 MB in 3.01 seconds = 168.33 MB/sec[/FONT]

It seems that my super fancy PCI-E ssd RevoDrive is only slightly faster than ssd installed in my laptop. Is it possible?
How to improve RevoDrive performance on Linux?

---

### Post by Perfect Storm on 2012-09-28
Moved to Other OS/Distro Talk.

---

### Post by mips on 2012-09-28
1. Did you update the drives firmware to the latest version when you got it? If you update the firmware you could lose all the data on it so don't do it unless you backed up!

2. Did you enable AHCI in your BIOS settings?

---

### Post by lukasz bandzarewicz on 2012-09-29
> 
1. Did you update the drives firmware to the latest version when you got it? If you update the firmware you could lose all the data on it so don't do it unless you backed up!


I've updated firmware to the latest version: 1.37. No difference.

> 
2. Did you enable AHCI in your BIOS settings?


I've just enabled AHCI and I don't see the difference. Anyway AHCI as far as understand AHCI is for conventional SATA driver. 
My RevoDrive is on PCI-E.

---

### Post by mips on 2012-09-29
Maybe try asking here [http://www.ocztechnologyforum.com/forum/forum.php](http://www.ocztechnologyforum.com/forum/forum.php) and let us know whatever you find out.

---

### Post by oldfred on 2012-09-29
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

 trim does need ahci

Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

