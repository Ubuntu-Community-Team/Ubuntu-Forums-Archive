---
title: "Raspbery Pi OpenWRT Multi Booting Help:"
date: 2015-07-30
forum: Any Other OS
---

### Post by Bentleythecomputer on 2015-07-30
I got a Raspberry Pi a while ago and finally just got the time to start working on turning it into a triple-boot, triple-purpose device. I used NOOBS to install RaspBMC with Kodi (formerly XBMC) and Arch Linux just fine. I then used Gparted to make another BOOT and root partition for OpenWRT, the third OS meant to turn my Raspberry Pi into a router. Here is a screenshot from Gparted with the partition layout:

[ATTACH=CONFIG]263494[/ATTACH]

As you can see, the partitions in the extended partition are numbered 5,6,7,8,10,9. I downloaded this file (it's a link):
[openwrt-brcm2708-sdcard-vfat-ext4.img]("http://downloads.openwrt.org/barrier_breaker/14.07/brcm2708/generic/openwrt-brcm2708-sdcard-vfat-ext4.img") 
using this helpful guide:
[http://askubuntu.com/questions/445979/mount-sd-card-image-created-using-dd](http://askubuntu.com/questions/445979/mount-sd-card-image-created-using-dd)and put the files extracted from the vfat partition into the BOOT2 partition. Those from the ext4 partition went into the root1 partition. I also changed the NOOBS configuration file to reflect these new additions so that I could boot from the new partition.
Knowing from previous experience that I needed to change the "root" in the cmdline.txt to redirect to the correct partition, I changed it to read "root=/dev/mmcblk0p9", which as you can see is the correct partiton that the rest of the OS is on.
That went fine. I was able to get NOOBS to start the booting process from BOOT2. 
However, it froze, saying, "waiting for root device." Using some info online, I changed "rootwait" to "rootdelay=10". During the next attempt, after ten seconds, it gave me this (I typed this in from a picture I took, as I don't know where a log would be for that stage of the boot process. I've also omitted the message times on the left to save typing time.):

```
VFP support v0.3: implementor 41 architecture 1 part 20 varia (picture cut off)
Waiting 10sec before mounting root device...
mmc0: read SD Status register (SSR) after 6 attempts
mmc0: new high speed SDHC card at address e624
mmcblk0: mcc0:e624 SU16G 14.8 GiB
 mmcblk0: p1 p2 < p5 p6 p7 > p3
VFS: Cannot open root device  "mmcblk0p9 or unknown block (0,0) (picture cut off)
Please append a correct "root=" boot option: here are the avail (picture cut off)
b300        15558144 mmcblk0 driver: mmcblk
    b301            1525343 mmcblk0p1 0008e6e2-01
    b302                        1 mmcblk0p2
    b303                32768 mmcblk0p3 0008e6e2-03
    b305              102400 mmcblk0p5 0008e6e2-05
    b306            6773760 mmcblk0p6 0008e6e2-06
    b307                81920 mmcblk0p7 0008e6e2-07
Kernel panic - not syncing: VFS: Unable to mount root fs on unkn (picture cut off)
```
As you can see, it doesn't detect the mmcblk0p9 (root1) partition, so it can't mount root and panics. The strange thing is, the boot files are on mmcblk0p10 (BOOT2), so it can't even detect the partition it's on. RaspBMC detects and mounts all the partitions just fine. I haven't tried mounting or detecting them with Arch, though.
I've tried using TestDisk to rebuild the boot sector on mmcblk0p10, but that just screwed it up. I reformatted the partition and put the boot files back in there, but that was a no dice either.
I am stumped and don't know how to proceed. Does anybody have any ideas as to how to fix this detection problem?

---

### Post by tgalati4 on 2015-07-31
Welcome to the forums?  Why do you want to create a triple-boot RaspberryPi?  They are cheap enough to be used as single-use computers.  

Take a fresh SD card and format it with a vfat partition and try loading openwrt by itself.  Make sure that the RaspberryPi will work with it by itself.  Because the network card hangs off of the USB bus (using the same controller chip), network performance is poor.  This would not be a good choice for a router.

---

