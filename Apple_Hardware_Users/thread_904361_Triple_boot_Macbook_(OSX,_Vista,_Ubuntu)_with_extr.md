---
title: "Triple boot Macbook (OSX, Vista, Ubuntu) with extra storage partiton"
date: 2008-08-29
forum: Apple Hardware Users
---

### Post by mobiuz on 2008-08-29
After reading several guides I tried yesterday installing a triple boot setup on my Macbook with an extra storage partition to share files between the different OS:es. Unfortunately, none of the guides I found explained how to do it with the extra storage partition, and after a lot of trying without managing Vista and Linux to booth successfully (using rEFIt) at the same time I gave up.

Then today I found [this post]("http://ubuntuforums.org/showthread.php?t=815737") where someone succeeds using this partition table:

(hd0,0) /dev/sda1 - EFI
(hd0,1) /dev/sda2 - Storage (FAT32)
(hd0,2) /dev/sda3 - Ubuntu Linux (ext3) <- GRUB
(hd0,3) /dev/sda4 - Windows Vista (NTFS)
(hd0,4) /dev/sda5 - Mac OS X (Mac OS Extended)
(hd0,5) /dev/sda6 - Swap (Linux Swap)

Now, I would like to keep my Mac OSX installation intact which I would guess requires me to keep Mac OSX as sda2. My proposed partition table is this:

/dev/sda1 EFI
/dev/sda2 Mac OS X (Mac OS Extended) (50GB)
/dev/sda3 Storage (FAT32) (100GB)
/dev/sda4 Windows Vista (NTFS) (50GB)
/dev/sda5 Ubuntu Linux (ext3) (30GB) <- GRUB
/dev/sda6 Swap (Linux Swap)

It takes the following requirements into account:
1) EFI is intact as number 1
2) OSX partition is left untouched
3) Storage partition is within the first four MBR partitions which means that even Windows Vista should be able to read it (I assume OSX and Ubuntu can too)
4) Vista is within the first four MBR partitions and also last among them (which seems optimal according to a number of posts I've read)
5,6) I guess this is the big question mark. The previously mentioned partition table had OSX outside the 4 MBR:s since the post submitter knew OSX could handle it. Now, can Ubuntu also be placed outside the 4 MBR:s and will it be able to read the storage partition? 

I don't care if the OS:es can't read each others partition, as long as they all can read the storage partition.

What do you think, will this work? Does anyone have another solution?

Thanks

---

### Post by cyberdork33 on 2008-08-29
> **mobiuz said:**
> 5,6) I guess this is the big question mark. The previously mentioned partition table had OSX outside the 4 MBR:s since the post submitter knew OSX could handle it. Now, can Ubuntu also be placed outside the 4 MBR:s and will it be able to read the storage partition? 
No.

The first table you posted looks like it would work (and from what I gather, someone did get it to work). The 4 partition barrier is a limitation of the "emulated" BIOS/MBR. GRUB uses the MBR partition table to boot, and thus cannot see Ubuntu (really it just needs to see it's configuration files and the kernel to boot).

You _can_ change what partition your MBR table points to though, but I haven't tried it:
[http://ubuntuforums.org/showthread.php?p=4896559#post4896559](http://ubuntuforums.org/showthread.php?p=4896559#post4896559)

---

### Post by mobiuz on 2008-09-01
Thanks for the response. I think I will go with the safe choice and put my OSX partition in the end instead.

---

