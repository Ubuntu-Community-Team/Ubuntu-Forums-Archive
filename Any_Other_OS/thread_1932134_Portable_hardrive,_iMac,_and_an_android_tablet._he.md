---
title: "Portable hardrive, iMac, and an android tablet. help please."
date: 2012-02-26
forum: Any Other OS
---

### Post by Piggah on 2012-02-26
So my computer is an iMac. I have a Toshiba thrive android tablet. I just bought a 750gb portable Toshiba hard drive. I accidently formatted it to the mac filesystem and i think thats why i am unable to access any of the files when i plug it into my tablet. my tablet recognizes the hard drive but i cant see any files.

do i need to format it into a different filesystem for the android tablet to see it? and if so how? i tried doing through virtualbox and ubuntu but it didnt recognise my tablet.


thank you

---

### Post by mips on 2012-02-27
From a bit of googling it seems you have to format the drive to exFAT FS. [http://en.wikipedia.org/wiki/ExFAT](http://en.wikipedia.org/wiki/ExFAT)

Other people suggest installing "USB Mount All" on you device which will give you access to ext2, ext3, ext4, fat32 and ntfs file systems.

[https://market.android.com/details?id=com.interphaze.USBMountAll&hl=en](https://market.android.com/details?id=com.interphaze.USBMountAll&hl=en)
[http://forum.xda-developers.com/showthread.php?t=1101729](http://forum.xda-developers.com/showthread.php?t=1101729)

HFS+ as used by OS X is not supported.

---

### Post by Double.J on 2012-02-27
Mips is quite correct - the HFS+ (probably journaled) filesystem is the problem.  And exFAT will solve the issue, however my tuppence would be for using NTFS as the filesystem and just installing the 3g driver in OSX. NTFS is far better supported than exFAT.

Either way you've got a microsoft filesystem, but I find NTFS to be the best filesystem for sharing cross platform because everything supports it, or support can be added very easily. Especially if you want to use ubuntu or other Linux - NTFS-3g is far more stable and tested than the fuse-exfat package.

It is of course personal choice - if you've already re formated and copied your data over, there's not much point in doing it again as exFAT support is growing quickly now we're constantly pushing the 4GB limit of FAT32. 

The main thing to remember is if you are using anything in addition to MAC, I usually find it's best to have removable media not formatted in HFS+ as support is simply terible. The other thing to wtch out for is the journalling - this is definitely  needed for OS X system partitions, but not recommended for filesystems where you may want to access from a different system as the journalling further reduces support.

If you haven't already added NTFS support to your mac, there's a trusted cnet download [here]("http://download.cnet.com/NTFS-3G/3000-2094_4-10913782.html")

Hope it helps!

---

### Post by mips on 2012-02-27
> **gnu/mirow said:**
> Mips is quite correct - the HFS+ (probably journaled) filesystem is the problem.  And exFAT will solve the issue, however my tuppence would be for using NTFS as the filesystem and just installing the 3g driver in OSX. NTFS is far better supported than exFAT.

Either way you've got a microsoft filesystem, but I find NTFS to be the best filesystem for sharing cross platform because everything supports it, or support can be added very easily. Especially if you want to use ubuntu or other Linux - NTFS-3g is far more stable and tested than the fuse-exfat package.

It is of course personal choice - if you've already re formated and copied your data over, there's not much point in doing it again as exFAT support is growing quickly now we're constantly pushing the 4GB limit of FAT32. 

The main thing to remember is if you are using anything in addition to MAC, I usually find it's best to have removable media not formatted in HFS+ as support is simply terible. The other thing to wtch out for is the journalling - this is definitely  needed for OS X system partitions, but not recommended for filesystems where you may want to access from a different system as the journalling further reduces support.

If you haven't already added NTFS support to your mac, there's a trusted cnet download [here]("http://download.cnet.com/NTFS-3G/3000-2094_4-10913782.html")

Hope it helps!

I have to agree with gnu/mirow here. Especially since NTFS supports files larger than 4GB when it comes to movies etc which FAT32 etc does not. As far as I'm aware exFAT also supports files larger than 4GB but NTFS is a much better FS.

---

