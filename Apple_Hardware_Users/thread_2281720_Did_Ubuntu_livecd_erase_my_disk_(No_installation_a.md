---
title: "Did Ubuntu livecd erase my disk? (No installation attempt)"
date: 2015-06-09
forum: Apple Hardware Users
---

### Post by emex2 on 2015-06-09
Hello forums!

     I booted into a livecd of ubuntu 14.04.2-desktop-i386 that was made off of OSX. I was was attempting to follow these instructions for the USB Armory. [https://github.com/inversepath/usbarmory/wiki/Preparing-a-bootable-microSD-image](https://github.com/inversepath/usbarmory/wiki/Preparing-a-bootable-microSD-image)
I was about halfway to installing the kernel when I held the power button down and pulled the livecd in order to get back to OSX quickly. I booted into the flashing file folder with a question mark, which led me to trying to figure out what was going on. Long long long story short, I installed OSX on a USB and started using Gdisk to read my figure out why my SSD was saying that it's partition map scheme was MBR. Is it possible that the livecd overwrote my OSX partitioning while following the usbarmory instructions? Gdisk is not really helping out a whole lot, probably because I dont understand it very well. I have used Gdisk and testdisk to read my ssd. No changes have been made with either program, but testdisk is able to recover the EFI system partition and find to "MS Data" partitions. I did have bootcamp running windows 8 on there, but those files don't show up when looking through the files in testdisk. I do see some linux lookng files in one of the MS Data partitions that testdisk finds... 

My Gdisk read outs are as follows:

```
sh-3.2# gpt -vv -r show /dev/disk0
gpt show: /dev/disk0: mediasize=121332826112; sectorsize=512; blocks=236978176
gpt show: /dev/disk0: MBR at sector 0
      start       size  index  contents
          0          1         MBR
          1      10239         
      10240  236967936      1  MBR part 131


sh-3.2# gdisk /dev/disk0
GPT fdisk (gdisk) version 1.0.0


Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present




***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************




Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.


Command (? for help): p


Disk /dev/disk0: 236978176 sectors, 113.0 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): E3CB17F6-9D5D-4B11-910C-9D04981A0E3C
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 236978142
Partitions will be aligned on 2048-sector boundaries
Total free space is 10206 sectors (5.0 MiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1           10240       236978175   113.0 GiB   8300  Linux filesystem






TestDisk 7.0, Data Recovery Utility, April 2015
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


Disk /dev/rdisk0 - 121 GB / 113 GiB - 236978176 sectors
     Partition               Start        End    Size in sectors
 D EFI System                    40     409639     409600 [EFI]
 D EFI System                    46     409645     409600 [EFI]
 D MS Data                    10238  236978173  236967936
>D MS Data                    10240  236978175  236967936
```

---

### Post by Bucky Ball on 2015-06-09
> I was was attempting to follow these instructions for the USB Armory. [https://github.com/inversepath/usbar...-microSD-image](https://github.com/inversepath/usbar...-microSD-image)

Welcome. Without knowing exactly what you've done it is hard to advise what to do. Where did you get up to? Please be specific which part of the tutorial you were attempting and where you ripped the disk out. Your BIOS is set to boot from the correct disk? 

No, running the Ubuntu Live install media alone can not make any changes on your hard drive unless you install it to the hard drive intentionally. What a user does when they are booted into the live desktop, on the other hand, can mangle things very well. :)

PS: Please see the last link in my signature regarding code tags for posting terminal output. Thanks.

PPS: Are you sure you installed part of the kernel to the USB and NOT the hard drive? The USB would not be sda. It would be sdb or sdc probably. You would need to specify that in your terminal commands somewhere along the way.

* Just re-reading the link and be aware that executing the 'sudo dd' command will wipe anything on the target device. That is the final command. Also, that tutorial is for making an SD. Are you using a USB? If so, there are easier ways of going about creating a bootable USB than that link.

Did you complete the testdisk repair and reboot? If you think it's possible you've wiped data you haven't got backed up, don't use that disk for anything other than repairing it. Boot from USB or some other bootable media, not the disk.

---

### Post by wildmanne39 on 2015-06-09
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

