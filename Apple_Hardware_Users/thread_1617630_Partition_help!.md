---
title: "Partition help!"
date: 2010-11-09
forum: Apple Hardware Users
---

### Post by awinterbreeze77 on 2010-11-09
Hi,

OS X's Disk Utility was refusing to partition the hard drive; so I 1-upped apple by popping in a Linux distro and partitioning with gParted. 

This was a mistake.

I cannot, for the life of me, get Apple to recognize the partition. I've tried formatting it to Fat 16, Fat 32, NTFS, whatever, and it can't do anything with it - it can't even format it. I was going to try reformatting it to HFS+ but I want some input from people before this happens.  Is there anyway I can get out of just simply reformatting the entire hard disk and reinstalling OS X? This is what I really want to avoid.

Honestly, I just want a clean install of Windows XP on my Mac, and boot camp/disk utility failing to work at all, I took matters into my own hands. In any case, I might throw a Ubuntu on a third section of the drive, so I might as well tackle this issue sooner rather than later.


Your support / advice is appreciated!


FYI: I'm doing this all on MacBook Pro 1,1.

[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc4/hs947.snc4/74044_10100402508112334_2363453_68465913_6076970_n.jpg[/IMG]

---

### Post by srs5694 on 2010-11-09
At least part of the problem is that the partition is marked as a [Microsoft Reserved](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition) partition, which OS X's Disk Utility can't handle very well. I recommend you download my [GPT fdisk (gdisk)](http://sourceforge.net/projects/gptfdisk/files/) program (for Linux or OS X) and use it to change the partition type code via the "t" main-menu option. Try changing it to a type of 0700 (Linux/Windows data) or AF00 (HFS/HFS+). Note that the change in gdisk only changes the type code, not the actual filesystem; you'll have to create a new filesystem using other tools. You must save the changes in gdisk by typing "w". Alternatively, you can delete the partition and then allow OS X's Disk Utility to create a new partition in its place.

You might find my [GPT fdisk page](http://www.rodsbooks.com/gdisk/) helpful, and particularly the [gdisk Walkthrough](http://www.rodsbooks.com//gdisk/walkthrough.html) page. Under OS X, the disk device will probably be /dev/disk0; under Linux, it will probably be /dev/sda.

---

### Post by awinterbreeze77 on 2010-11-09
I still have Tiger, so I'll have to use an older version of it. But following through with what you said.

---

### Post by awinterbreeze77 on 2010-11-09
So, I tried gdisk, but unfortunately it isn't able to start as per Version 4.1 - it keeps giving me 'Bus Error.' 4.1 is the latest OS X tiger version I could find.

---

### Post by awinterbreeze77 on 2010-11-09
Okay, so I popped in the LiveCD and ran Gdisk and this is how far I got : 

mepis1:/# sudo gdisk
GPT fdisk (gdisk) version 0.6.13

Type device filename, or press <Enter> to exit: /dev/sda3
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************

Exact type match not found for type code 7000; assigning type code for
'Linux/Windows data'
Exact type match not found for type code 4300; assigning type code for
'Linux/Windows data'
Exact type match not found for type code 7200; assigning type code for
'Linux/Windows data'

Warning! Secondary partition table overlaps the last partition by
3741111295 blocks!
You will need to delete this partition or resize it in another utility.

Command (? for help):

---

### Post by awinterbreeze77 on 2010-11-09
Further gdisk results. The sizes of the drives are grossly inaccurate:


Command (? for help): i
Partition number (1-3): 1
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Linux/Windows data)
Partition unique GUID: CDA99A7C-5D6E-40D8-B739-DDE766ABAC9A
First sector: 6579571 (at 3.1 GiB)
Last sector: 1924427647 (at 917.6 GiB)
Partition size: 1917848077 sectors (914.5 GiB)
Attribute flags: 0000000000000000
Partition name: Linux/Windows data

Command (? for help): i 
Partition number (1-3): 2
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Linux/Windows data)
Partition unique GUID: C63E5772-A387-4F5E-8C80-17634B352CDC
First sector: 1953251627 (at 931.4 GiB)
Last sector: 3771827541 (at 1.8 TiB)
Partition size: 1818575915 sectors (867.2 GiB)
Attribute flags: 0000000000000000
Partition name: Linux/Windows data

Command (? for help): i
Partition number (1-3): 3
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Linux/Windows data)
Partition unique GUID: 4CBA00D7-F040-415C-9BD7-05C40322EF50
First sector: 225735265 (at 107.6 GiB)
Last sector: 225735274 (at 107.6 GiB)
Partition size: 10 sectors (5.0 KiB)
Attribute flags: 0000000000000000
Partition name: Linux/Windows data

---

### Post by srs5694 on 2010-11-09
You've specified /dev/sda3 (a partition) as the input for gdisk; but gdisk must be given a *whole disk* (probably /dev/sda in Linux) as its input. I recommend you try again, giving it the correct device filename.

---

