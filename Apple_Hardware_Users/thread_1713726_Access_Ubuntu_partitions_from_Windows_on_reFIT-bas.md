---
title: "Access Ubuntu partitions from Windows on reFIT-based triple boot"
date: 2011-03-24
forum: Apple Hardware Users
---

### Post by rryk.ua on 2011-03-24
I have installed reFIT-based triple boot. Here is the partition scheme:

1. GPT Protective Partition (GPT and MFT)
2. Mac OS X (GPT and MFT)
3. Windows 7 64-bit C: (GPT and MFT)
4. Windows 7 64-bit D: (GPT and MFT)
5. Ubuntu 10.04 / (only GPT)
6. Ubuntu 10.04 swap (only GPT)

Windows only supports MFT and thus sees last two partitions (5 and 6) as unallocated space. Can I somehow make it see these partitions to be able to access files from Ubuntu?

P.S. I know this is rather Windows problem, but I don't know any good forums where I can ask that, because mostly on these forums the answer is "Why would you need anything but Windows?". Please give me some links to the forums where people are not so obsessed with Windows :). Thank you.

---

### Post by An Sanct on 2011-03-24
There is a great tool for that, it is called ext2ifs (ext2 driver for windows)

You can download it at this location:
```
http://www.fs-driver.org/
```

---

### Post by rryk.ua on 2011-03-24
> **An Sanct said:**
> There is a great tool for that, it is called ext2ifs (ext2 driver for windows)

You can download it at this location:
```
http://www.fs-driver.org/
```

Thanks, but it does not work on Windows 7 and does not support ext4fs, which is used by Ubuntu.

---

### Post by srs5694 on 2011-03-24
I believe you mean "Master Boot Record (MBR)" or "MS-DOS partition table", not "MFT"; I've never seen that as a name for MBR partitions. (On the other hand, this partitioning system has gone by so many names over the years that it's not humanly possible to keep track of them all, so I may be unaware of that name! ;) )

That said, Windows can't read Linux filesystems without special drivers, and I'd be *very* reluctant to give Windows access to the Linux root (/) filesystem even with such drivers. Windows doesn't know a thing about Linux security or permissions, so it would be far too easy to accidentally damage your Linux system from Windows. (Similar comments apply to accessing the Windows C: partition from Linux.) If you insist, drivers such as those that An Sanct refers to do exist. The last I heard, though, they supported just ext2fs and ext3fs, not the ext4fs that's the default for new Ubuntu installations.

If you need to exchange data between Windows and Linux, your best bet is to use a dedicated file-transfer/shared-file partition. It could be that your Windows D: partition will serve that purpose, but it's impossible to be sure without knowing its size, how much free space it contains, and your needs. If necessary, you could repartition your disk or use another hard disk for the purpose.

Getting to the heart of your question, though, you need to create a new [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) to give Windows access to a different set of partitions. Most tools that create hybrid MBRs, such as the standard version of gptsync, automatically make MBR entries for the first three partitions (usually excluding the EFI System Partition). My [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program can create a hybrid MBR composed of any partitions you like, within the three-partition limit.

Also, you should be aware that what you've identified as partition #1 is *not* one partition in both systems! In GPT, it's the EFI System Partition, which is a standard partition on EFI-based computers. Under MBR, it's a *different* partition; it's the protective partition, which begins at sector 0 and continues until some point (the end of the disk on a legal GPT disk or usually to the first hybridized partition on a hybrid MBR disk). This is almost certain to cover a different set of sectors than the GPT's first partition. On a legal GPT disk, its purpose is to prevent GPT-unaware utilities from mucking with the disk. On both legal GPT disks and hybrid MBR disks, it also signals GPT-aware OSes and utilities that the disk is a GPT disk. The upshot of this is twofold: First, you should never attempt to read from or (worse) write to this partition; and second, you should never attempt to delete or modify the partition using MBR partitioning tools unless you really know what you're doing. Sorry if I'm being pedantic or if this seems like I'm splitting hairs, but the belief that the two partitions are one and the same could lead to some *very* nasty problems, and I'd like to head that off.

---

### Post by rryk.ua on 2011-03-24
> **srs5694 said:**
> I believe you mean "Master Boot Record (MBR)" or "MS-DOS partition table", not "MFT"; I've never seen that as a name for MBR partitions. (On the other hand, this partitioning system has gone by so many names over the years that it's not humanly possible to keep track of them all, so I may be unaware of that name! ;) )

You are absolutely right. I meant MBR. MFT stands for Master File Table in the NTFS file system and has nothing to do with partitioning.

> **srs5694 said:**
> That said, Windows can't read Linux filesystems without special drivers, and I'd be *very* reluctant to give Windows access to the Linux root (/) filesystem even with such drivers. Windows doesn't know a thing about Linux security or permissions, so it would be far too easy to accidentally damage your Linux system from Windows. (Similar comments apply to accessing the Windows C: partition from Linux.) If you insist, drivers such as those that An Sanct refers to do exist. The last I heard, though, they supported just ext2fs and ext3fs, not the ext4fs that's the default for new Ubuntu installations.

First of all I don't necessarily need write-access. I just want to be able to copy files from the Linux to Windows without the need to reboot. To be more specific this is why I need this.

I develop cross-platform application and keep two development repositories under Git. One is on the Linux partition and the other is on Windows drive D. When I perform some changes into Linux version and before I will push them into shared repository on the remote server, I need to reboot into Windows and check if my changes compile/work there. Of course I can copy these changes by creating a patch or pushing the changes directly to the Windows drive D from Linux, but I often forget to do so and there are also some additional problems related to messed up line endings.

All in all, I need to have read-only access to Linux partitions from Windows. I remember that I have already tried solving this problem some long time ago and then I have found out that, like you said, it only supports ext3fs, while my installation had ext4fs.

As for the drivers, that An Sanct referred to, can I simply recompile them for Windows 7 or must they be ported/adapted it it?

> **srs5694 said:**
> If you need to exchange data between Windows and Linux, your best bet is to use a dedicated file-transfer/shared-file partition. It could be that your Windows D: partition will serve that purpose, but it's impossible to be sure without knowing its size, how much free space it contains, and your needs. If necessary, you could repartition your disk or use another hard disk for the purpose.

I have also tried doing this in the past, but Linux works much faster with it's own native FS, rather than with FAT or NTFS. My projects consts of dozens of thousands of small files and compilation times depend on the underlying OS heavily.

> **srs5694 said:**
> Getting to the heart of your question, though, you need to create a new [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) to give Windows access to a different set of partitions. Most tools that create hybrid MBRs, such as the standard version of gptsync, automatically make MBR entries for the first three partitions (usually excluding the EFI System Partition). My [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program can create a hybrid MBR composed of any partitions you like, within the three-partition limit.

Sounds like the whole thing is really messed up. Thanks for the link - it is the first article that clearly explains the situation. Let's hope that one day Windows will fully support GPT (also on BIOS/BIOS-emulated computers) and we will forget about legacy MBR with all of it's limitations.

> **srs5694 said:**
> Also, you should be aware that what you've identified as partition #1 is *not* one partition in both systems! In GPT, it's the EFI System Partition, which is a standard partition on EFI-based computers. Under MBR, it's a *different* partition; it's the protective partition, which begins at sector 0 and continues until some point (the end of the disk on a legal GPT disk or usually to the first hybridized partition on a hybrid MBR disk). This is almost certain to cover a different set of sectors than the GPT's first partition. On a legal GPT disk, its purpose is to prevent GPT-unaware utilities from mucking with the disk. On both legal GPT disks and hybrid MBR disks, it also signals GPT-aware OSes and utilities that the disk is a GPT disk. The upshot of this is twofold: First, you should never attempt to read from or (worse) write to this partition; and second, you should never attempt to delete or modify the partition using MBR partitioning tools unless you really know what you're doing. Sorry if I'm being pedantic or if this seems like I'm splitting hairs, but the belief that the two partitions are one and the same could lead to some *very* nasty problems, and I'd like to head that off.

Thanks for the clarification. I thought that this is a normal partition that contains recovery information that is used by Mac OS X to reset compute to the factory settings, including erasing entire disk and restoring original Mac OS installation.

---

### Post by srs5694 on 2011-03-24
> **rryk.ua said:**
> First of all I don't necessarily need write-access. I just want to be able to copy files from the Linux to Windows without the need to reboot.

Read-only access is certainly much safer.

> All in all, I need to have read-only access to Linux partitions from Windows. I remember that I have already tried solving this problem some long time ago and then I have found out that, like you said, it only supports ext3fs, while my installation had ext4fs.

I don't know if there are any tools for ext4fs access from Windows. You might consider converting from ext4fs to ext3fs, or add an ext3fs partition on which you store the files you want to transfer. You'd have to back up and restore or use partition resizing tools to accomplish either goal, though. Personally, I wouldn't trust a partition resizer on a hybrid MBR disk; there are too many ways that could lead to trouble. Thus, if you decide to resize in order to create a new partition, I recommend you first convert the disk to a conventional GPT configuration (temporarily rendering Windows unbootable), resize your partitions, and then create a fresh hybrid MBR.

> As for the drivers, that An Sanct referred to, can I simply recompile them for Windows 7 or must they be ported/adapted it it?

I have no idea.

> Sounds like the whole thing is really messed up. Thanks for the link - it is the first article that clearly explains the situation. Let's hope that one day Windows will fully support GPT (also on BIOS/BIOS-emulated computers) and we will forget about legacy MBR with all of it's limitations.

Windows Vista and 7 do support GPT, but only as data (non-boot) disks on BIOS systems. On EFI, they fully support GPT, but unfortunately, Microsoft doesn't support Apple's version of EFI, so Windows must treat Macs as BIOS-based computers (relying on the BIOS emulation that's built into Apple's EFI). As you say, it's "messed up."

> Thanks for the clarification. I thought that this is a normal partition that contains recovery information that is used by Mac OS X to reset compute to the factory settings, including erasing entire disk and restoring original Mac OS installation.

The EFI System Partition officially exists to hold drivers for the EFI and boot loaders. On a from-the-box Mac, it's normally empty or nearly so, but when you start adding OSes, you're likely to end up with extra boot loader files. rEFIt stores files there, and depending on the configuration, GRUB 2 might do so, as well.

Because the start sectors are different, an MBR-using OS (like Windows) will be unable to see the filesystem on the 0xEE partition, which is one of the dangers -- if you think the filesystem has been damaged and try to re-create it, you'll end up damaging the filesystem that's actually there (just offset by a few sectors).

---

### Post by An Sanct on 2011-03-25
> **rryk.ua said:**
> Thanks, but it does not work on Windows 7 and does not support ext4fs, which is used by Ubuntu.
I am using it on Windows 7 Ultimate 64bit edition and it works just fine :)

PS. All my partitions are ext4, it has no trouble opening files with ext4, since as far as I know, Ext file systems are compatible... Ext3 and Ext4 are only upgrades of Ext2 ...

PS2. I have MBR, since under GPT windows didn't let me install :(

---

### Post by rryk.ua on 2011-03-26
> **An Sanct said:**
> I am using it on Windows 7 Ultimate 64bit edition and it works just fine :)

PS. All my partitions are ext4, it has no trouble opening files with ext4, since as far as I know, Ext file systems are compatible... Ext3 and Ext4 are only upgrades of Ext2 ...

PS2. I have MBR, since under GPT windows didn't let me install :(

Sounds like just what I need, but according to [download web-page]("http://www.fs-driver.org/download.html") it only supports Windows NT 4.0/2000/XP/2003/Vista/2008 (both x86 and x64 platform). Also when trying to run the installer it pops up a dialog box with similar message: "This version of the software runs on Windows NT 4.0, Windows 2000, Windows XP, Windows 2003 and Windows Vista (for the x86 and x64 platform) only".

Can you please send me a direct link to what you have downloaded and installation instructions if some "special" steps are required? Also I would appreciate if you will explain me how should I add Linux drives to the program that are recognized as unallocated space by Windows? Is this possible at all?

---

### Post by srs5694 on 2011-03-26
> **rryk.ua said:**
> Also I would appreciate if you will explain me how should I add Linux drives to the program that are recognized as unallocated space by Windows? Is this possible at all?

Please review what I've already posted here about hybrid MBRs.

---

