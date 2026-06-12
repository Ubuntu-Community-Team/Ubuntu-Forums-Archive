---
title: "Boot floppy for live-cd?"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Liolikas on 2006-01-27
Is it possible to boot ubuntu live-cd from hdd with "boot floppy" like Puppy or DSL? :rolleyes:

---

### Post by JAwuku on 2006-01-27
I don't think you can use a boot floppy for the Live CD, as it's designed to boot straight from the CD, and run directly from the CD without interfering with the hard disk at all.

---

### Post by lha on 2006-01-28
[QUOTE=Liolikas]Is it possible to boot ubuntu live-cd from hdd with "boot floppy" like Puppy or DSL? :rolleyes:[/QUOTE]

Yes, it is, but I haven't found a way to do completely automated boot. I had to manually mount the cd-image every time I boot it. I did this some time ago, and don't remember the exact produres to make it work, but I hope this helps you a bit.

I made a dedicated partition for the live-cd. You probably could use an existing partition if you want. I copied all files from the live-cd image (they can be copied from a real live-cd, too) to the partition. Then I edited my grub's menu.lst to have something like this:
```
title Ubuntu Live CD
root (hd0,1)
kernel /install/vmlinuz casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop vga=normal ramdisk_size=1048576 root=/dev/rd/0 rw --
initrd /install/initrd.gz
```
I know that kernel line needed some modifications. (Those options are used when you boot a real live cd.) Maybe I had to remove those /cdrom bit or change root=/dev/rd/0 to something else or remove it. You can use a grub floppy to do this bit if you don't have grub on your hd.

When "live cd" is booting up, it stop when trying to mount cd. (Of course it does, there's no cd!) Here you have to go to console (<control>-<alt>-<f2>) and mount the partition where you have lice cd files. Use <control>-<alt>-<f1> to get back in the "searching for cd" screen. Now it should be able to find "a cd".

Sorry for these lousy instruction, but i really cannot remember more accurately how i did it. BTW, how did you boot DSL from hd? I'd be interested in that if there's a clean way to do it.

---

### Post by Liolikas on 2006-01-28
For DSL it is possible to download "bootfloppy.img" from all download mirrors.
Then I copy KNOPIX folder from iso with "daemon tools 4" directly into fat32 partition.
Then I "burn" floppy image with "rawwritewin".
Then insert floopy reboot my PC and DSL starts!
It is so easy to do, instaling pc game sometimes is more dificult! :D

---

