---
title: "Mounting APFS partition within corrupted dd image and InnoDB data recovery"
date: 2018-05-28
forum: Apple Hardware Users
---

### Post by jhoefs on 2018-05-28
I'd like help in solving a problem that has so far been intractable. It involves an accidental dropped tables incident in MySQL (losing 40% of the database) which affected a website development project in Joomla that had been ongoing for nine months. In most situations, it would have been pretty easy to recover the data in Ubuntu, thanks to the Undrop for InnoDB tools. Unfortunately, thanks to Apple, it may be postponed indefinitely, as it has so far been impossible to mount the disk image. 

I am still hopeful, though. I am hoping that wiser minds and the wiser mind of the community collective will triumph. That's why I am posting here.

I've tried too many things to name all of them, as it would be prohibitive to space; suffice to say that I have tried, read, and exhausted every solution for mounting unmountable disks (and related topics) I could possible find down to five pages deep in google, using both Ubuntu and mac systems as potential resources. I have invested many many hours, and several all-nighters, into this so far. 

Where I am at in the present moment: when the incident happened, I shut down the server immediately and rebooted the Macbook Air in recovery. This is why only 40%, and not 100% of the tables were dropped. I then created a dd image of the entire hard drive. 

The data I want to access is stored in an encrypted APFS partition within this disk image, which you can see below. From the mac terminal first (and then on to Ubuntu): 

```
$ sudo hdiutil imageinfo /Volumes/untitled/clone.dmg
Backing Store Information:
    URL: file:///Volumes/untitled/clone.dmg
    Name: clone.dmg
    Class Name: CBSDBackingStore
Class Name: CRawDiskImage
Checksum Type: none
Size Information:
    Total Bytes: 121332826112
    Compressed Ratio: 1
    Sector Count: 236978176
    Total Non-Empty Bytes: 121332826112
    Compressed Bytes: 121332826112
    Total Empty Bytes: 0
Format: UDRW
Format Description: raw read/write
Checksum Value:
Properties:
    Encrypted: false
    Kernel Compatible: true
    Checksummed: false
    Software License Agreement: false
    Partitioned: false
    Compressed: no
Segments:
    0: /Volumes/untitled/clone.dmg
partitions:
    partition-scheme: fdisk
    block-size: 512
    partitions:
        0:
            partition-name: Master Boot Record
            partition-start: 0
            partition-synthesized: true
            partition-length: 1
            partition-hint: MBR
            boot-code: 0x0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
        1:
            partition-start: 1
            partition-number: 1
            partition-length: 29622271
            partition-hint: Type EE
        2:
            partition-name:
            partition-start: 29622272
            partition-synthesized: true
            partition-length: 207355904
            partition-hint: Apple_Free
    burnable: false
Resize limits (per hdiutil resize -limits):
 min      cur      max
236978176    236978176    775551664
```

As you can see there are several partitions in the disk image. As far as I've found there is no way to mount a partition within a disk image based upon an offset or partition number in mac osx (!). If someone knew a way of doing this, then perhaps I could mount the volume on the Macbook, and convert it to a format which Ubuntu could handle easier. 

In Ubuntu:

```
~$ sudo fdisk -lu /media/jonathan/untitled1/clone.dmg

Disk /media/jonathan/untitled1/clone.dmg: 121.3 GB, 121332826112 bytes
255 heads, 63 sectors/track, 14751 cylinders, total 236978176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                              Device Boot      Start         End      Blocks   Id  System
/media/jonathan/untitled1/clone.dmg1               1    29622271    14811135+  ee  GPT
```

You will notice that my linux computer is not "seeing" the second partition (the APFS one). 

My most recent attempt to mount the device looked like this (all I have to do is get that partition to mount in Ubuntu [including using the encryption key], the Undrop for innoDB tools will take care of the rest). In this case, I am using the offset information from the macbook (although it is the end of the listed partition from fdisk +1, so could have been deduced from that, as well):
```

$ sudo losetup -o 15166603264 /dev/loop3 /media/jonathan/untitled1/clone.dmg
$ sudo ./apfs-fuse -r passphrase /dev/loop3 /media/jonathan/mountpoint
nid 225bb8ef93393147 xid 699def95c77bf8a9 NOT FOUND!!!
Unable to get volume!
```

and, just for posterity, attempting to mount the APFS partition using apfs-fuse with an offset:
```

$ sudo ./apfs-fuse -o 15166603264 -r passphrase /media/jonathan/untitled1/clone.dmg /media/jonathan/mountpoint
Unable to get volume!
```

[note: I replaced the encryption key with "passphrase" in both examples above, for obvious reasons]

Any solutions? I have searched everywhere for a tool that could mount apfs, or convert it to another format, or anything along those lines. I have tried converting the image to other formats through the Macbook, to no avail [I converted it to ISO, but that would not mount, either. In mac the error is: "no mountable file systems" for both .dmg and .iso - I didn't mention this above, but normal old disk utility in mac fails to mount the disk image, as well, and since it cannot mount it, it cannot repair it, either]. I have tried to repair the dd disk image as a whole (which also will not mount in either system), to no avail. I have tried partition map repair tools (including Christophe Grenier&#8217;s testdisk tool) - no dice so far.

I have no experience manufacturing headers, but perhaps if I manufactured the right one, I could trick the computer into mounting the drive. I will never access any of the files in the traditional way (like opening a text document), so this should be fine - The undrop for innoDB tool will search everything in the image, and the most likely place for the dropped tables is virtual memory. And then I will be done with the disk image. So if I can get it mounted, even if all the t's are not crossed and the i's not dotted, it is likely the process will work. [I don't even know if manufacturing a header would work, the idea comes from a page someone authored in 2009, where they had a similar problem with HFS+ images and successfully solved it by manufacturing headers to get the image to mount&#8230; they were then able to proceed with successful data recovery, even though I think the header information was patched from another disk image, and so probably contained errors]

I have never worked with disk images at this level before - it has been a crash course of necessity! Please, any help will be so much appreciated.

Rant: Why did MAC do this? It seems like their APFS switchover has screwed alot of people over from my research, including me, and I would like for them to answer as to why they didn&#8217;t develop appropriate tools to prevent this huge gap in functionality that is affecting peoples personal and professional data. Visa vie the fact that many of their command line tools aren't as up to date in working with APFS as HFS+. I would think that rolling out comprehensive command line tool support and the new data format at the same time would be the ethical thing to do. What's that you say? Proprietary formats and the conquest of new capital resources? What? I don&#8217;t understand. Lol. This incident may mark the end of my time with mac. We will see.

---

### Post by QIII on 2018-05-29
Moved to Apple Hardware Users.

---

### Post by jhoefs on 2018-06-01
Bump

---

