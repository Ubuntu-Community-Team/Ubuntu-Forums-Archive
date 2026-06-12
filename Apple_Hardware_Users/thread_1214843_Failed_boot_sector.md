---
title: "Failed boot sector"
date: 2009-07-16
forum: Apple Hardware Users
---

### Post by FiZi on 2009-07-16
A friend of mine has a Mac Book Pro and it appears his boot sector got eaten/physically failed on him. His Mac Book of course won't boot anymore and his drive is formatted to use HFS+.

I've removed the hard drive from his system and put it into a PC laptop and fired up a Ubuntu 8.04 LiveCD in an attempt to get at his data and copy it to another hard drive. Following the information I've found around these forums and the Wiki I've managed to make a copy of his hard drive using ddrescue. We've also run Spinrite on his hard drive and of course the only bad sector (and sector it can't recover) is 00.

When I try to mount the image of his hard drive I get the following:
```

ubuntu@ubuntu:/mnt/usb1TB$ sudo mount -o loop,r -t hfsplus johnnyHD.img /mnt/johnnyHD/
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I used foremost and managed to get a bunch of data back straight out of the image but it's no where near everything. I've tried mounting the image with an offset so I'd only get the main partition but it fails with the same error as above. If I use 'losetup' to mount the image to a loop back device I can view the loop back device with 'parted' and see the partitions. Is there anyway I can repair the superblock? Or simply force it to mount the partition so I can copy all the data off it?

---

### Post by FiZi on 2009-07-17
Maybe I should get this thread moved to General Help where more eyes might see it?

---

### Post by FiZi on 2009-07-18
Resolved this problem by manually rebuilding the partition table following these instructions:

[http://perrohunter.com/?p=technology/repair-a-mac-os-x-hfs-partition-table](http://perrohunter.com/?p=technology/repair-a-mac-os-x-hfs-partition-table)

---

