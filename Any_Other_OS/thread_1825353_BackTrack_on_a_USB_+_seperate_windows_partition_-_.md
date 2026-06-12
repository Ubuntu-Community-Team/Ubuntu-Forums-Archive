---
title: "BackTrack on a USB + seperate windows partition - Can't mount in Windows."
date: 2011-08-15
forum: Any Other OS
---

### Post by jonny_sicoli on 2011-08-15
Hello all, I'm currently having a problem with my Ubuntu distro. Specifically, the one on my USB drive, which I installed via the method at this URL:

[http://www.infosecramblings.com/backtrack/backtrack-5-bootable-usb-thumb-drive-with-full-disk-encryption/](http://www.infosecramblings.com/backtrack/backtrack-5-bootable-usb-thumb-drive-with-full-disk-encryption/)
(Backtrack is a security-oriented version of Ubuntu.)



Now I have a 32 GB USB drive, so I figured I'd use 16GB for the installation, and have a 16GB FAT32 partition reserved for all my Windows files, since my Windows can't access Ext2. I can both create and read the partition just fine in Backtrack (Ubuntu). However, when I try to mount it in Windows:
- The "Format Disk" option appears, which is most definitely NOT what I want. I assume it's trying to mount the first partition.
- In "Disk Management", it shows that the last partition is mounted, but that it's in RAW.

Here's my basic partition layout, from memory, in order.

- ~500MB EXT3 partition, which I assume has the bootloader.
- Extended partition, that has a ~13GB EXT3 (Linux files) and a 1.5GB swap.
- ~16GB (rest of the USB) dedicated to my files, in FAT32.

I would really appreciate some help as I often need access to these files in Windows, but would also like to have a Linux distro on my USB.  Please let me know if there's any information you are missing!

---

### Post by varunendra on 2011-08-15
Are you installing BackTrack or Ubuntu? Although both are debian based, they are different in many aspects, so i can't say whether or not the following method would work with BackTrack (although given the way BT installs and operates on a native HDD, I think there should be no difference between them)

Furthermore, which version of windows are you using? If it is XP, it can read ONLY the first partition on a USB key. With Vista/win7, there should be no problem reading later partitions if they are correctly formatted.

Regardless of the version of Windows and assuming you are talking about Ubuntu (not sure about BT) this 'should' work:

[LIST=1]
[*]Recreate partitions on the USB key using gparted (sequence of creating partitions MUST be in the following order)
[*]First, create a FAT32 partition in the beginning (size = whatever you want)
[*]Next, create an EXT3/4 partition for installation (size = remaining space - swap space)
[*]Last, create the swap partition
[/LIST]
Now install Ubuntu on the USB key normally as you would on a normal internal HDD, only make sure to choose the USB key as the destination for GRUB (else it'll get installed on the internal drive and then you'll need to plug in the USB key every time you boot). For '/' choose the ext3/4 partition you created on the USB key.

So far I have made only Live installations on such USB key layouts, but am quite sure the normal installation should work the same way.

---

### Post by jonny_sicoli on 2011-08-15
Hello again! I'm not at my home PC yet, but I can confirm that my Backtrack distro already works. I can boot into it and everything. However, when I plug the USB in on Win7, it apparently mounts the first (bootloader) partition, while saying that the last partition is mounted. Screenshot of the device in Disk Mgmt. 
Could it be something re: the way the partitions are mounted?

---

### Post by varunendra on 2011-08-15
> **jonny_sicoli said:**
> Hello again! I'm not at my home PC yet, but I can confirm that my Backtrack distro already works. I can boot into it and everything. However, when I plug the USB in on Win7, it apparently mounts the first (bootloader) partition, while saying that the last partition is mounted. Screenshot of the device in Disk Mgmt. 
Could it be something re: the way the partitions are mounted?
The tutorial you referred to is about a 'full disk' encryption. I didn't read it, but it may be the reason why win7 considers it a raw file-system.

So, what are your objectives here? If a full disk encryption is not one of them, why don't you try the method I suggested in my previous post? If you indeed require the encryption, I'm afraid you have to look into 'individual partition encryption' rather than full disk encryption, so that the FAT32 partition and MBR could be left unaffected.

Besides all of this, you still haven't made clear whether your problem is related with Backtrack or Ubuntu. If you are talking about BackTrack, stop calling it 'Ubuntu'. BT is NOT Ubuntu, just like mint is not! Also, is it a version installed on your computer at home or one on the USB key? Solving a problem becomes much more difficult if we have to 'assume' most of things rather than work on solid details.

---

### Post by Dutch70 on 2011-08-15
I just want to add that you can read ext2 & ext3 files from windows by installing [Ext2 IFS]("http://www.fs-driver.org/") into windows. I've been doing it for years with no problems whatsoever.

I don't think it's possible to read Ext4 yet.

---

### Post by jonny_sicoli on 2011-08-16
> **varunendra said:**
> Besides all of this, you still haven't made clear whether your problem is related with Backtrack or Ubuntu. If you are talking about BackTrack, stop calling it 'Ubuntu'. BT is NOT Ubuntu, just like mint is not! Also, is it a version installed on your computer at home or one on the USB key? Solving a problem becomes much more difficult if we have to 'assume' most of things rather than work on solid details.

Ah. I'm sorry for the misconception. I was under the impression that Backtrack was a modified flavor of Ubuntu.  I'm working with Backtrack Linux here. I was also under the impression that the differences in the kernel wouldn't be large enough to affect things like mounting FAT32 partitions alongside it.

Anyway, what I am currently trying to do is make a USB that can both boot into Backtrack (not Ubuntu) and, when plugged into a Windows system, open up a FAT32 partition for my Windows things.... I guess I don't really NEED partition encryption, so for my sanity's sake I guess I'll leave it out.

[QUOTE=Dutch70]I just want to add that you can read ext2 & ext3 files from windows by installing Ext2 IFS into windows. I've been doing it for years with no problems whatsoever.[/QUOTE]

Actually, I have heard about this program. Really excellent, practically seamless, but people tend to frown upon having weird programs installed on their PC by someone else.  Ext2 IFS is awesome, but not what I'm looking for here.

Anyway, I reformatted the drive, and recreated the partitions in the order Varunendra suggested. I'm just waiting for it to finish up, I'll let you guys know how it goes.  Thanks!

EDIT: Success! FAT32 partition can be read in Windows, and can boot from USB into Backtrack Linux. Marking this thread as Solved!

---

### Post by Perfect Storm on 2011-08-16
Moved to Other OS/Distro Talk.

---

### Post by drawkcab on 2011-08-17
> **Dutch70 said:**
> I just want to add that you can read ext2 & ext3 files from windows by installing [Ext2 IFS]("http://www.fs-driver.org/") into windows. I've been doing it for years with no problems whatsoever.

I don't think it's possible to read Ext4 yet.

I wish someone would figure that out!

---

