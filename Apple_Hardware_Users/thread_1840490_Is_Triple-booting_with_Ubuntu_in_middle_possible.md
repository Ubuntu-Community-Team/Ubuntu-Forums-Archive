---
title: "Is Triple-booting with Ubuntu in middle possible?"
date: 2011-09-07
forum: Apple Hardware Users
---

### Post by temporalburst on 2011-09-07
Hi, I have been using Ubuntu for some time now, but my knowledge seems to fall short when it comes to multibooting.

My (possibly dumb) question is, is it possible to install Ubuntu to a partition in between an already installed Mac OS X and Windows 7 without messing up the booting of either OS? I have room to make my OS X partition smaller to add a new one after it, but not after Windows 7. I just wanted to make certain before jumping right in and possibly screwing something up. Apologies in advance if this has been asked before/already has been answered.

It would look something like this when done:

[INDENT][INDENT] Mac OS X                / Ubuntu /          Windows 7
[/INDENT][/INDENT] [==============][==============][===============]

---

### Post by ajgreeny on 2011-09-07
If possible it is far better to avoid moving the start point of a partition on disk, and preferable to shrink the first partition and use the free space there to install your ubuntu OS.

It doesn't really matter where the partitions are on the disk, so is there a particular reason why you want ubuntu between the Mac OS X and Windows 7?  Show us a screenshot of your disk from a ubuntu live CD running gparted, if possible.  It will give a lot more information than we have at the moment, and show the current number of partitions already on disk.

---

### Post by temporalburst on 2011-09-07
> It doesn't really matter where the partitions are on the disk, so is  there a particular reason why you want ubuntu between the Mac OS X and  Windows 7?This is mainly what I needed to know, I just didn't know if a partition's location mattered or not. The only real reason for wanting it between OS X and Windows 7 is that I didn't have room to resize Windows 7's partition, but had plenty room to resize OS X's. Thank you!

Also, I have just two partitions, one for OS X and one for Windows 7 through BootCamp.

---

### Post by srs5694 on 2011-09-07
One caveat is that Windows relies on a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) to boot on an Intel-based Mac. As described on the page to which I linked, hybrid MBRs are a dangerous hack, and if you do things wrong, you can seriously mess up your computer. Most importantly, you should do your partition resizing from OS X's Disk Utility or some other tool that understands the GUID Partition Table (GPT) partitioning scheme that Intel-based Macs use natively. If you use Windows, it will see the disk as MBR, resize the MBR representations of the partitions, and leave the GPT representations alone, which will create a dangerous inconsistency. I realize you probably wouldn't use a Windows tool to shrink your OS X partition, but I want to point out this danger since I've seen posts and even gotten e-mails from people who've seriously damaged their disks because they used Windows partitioning tools on disks with hybrid MBR configurations.

A less serious issue, but one that could easily become a stumbling block, is that when you finish installing Ubuntu, you'll probably have a GPT-only disk rather than a hybrid MBR. Various tools will enable you to create a fresh hybrid MBR, but most of these just add the first three partitions (aside from the EFI System Partition, or ESP, which OS X's Disk Utility hides from view) to the MBR side. Depending on how many partitions you use, putting Windows at the end can result in Windows being left out of the MBR, which means that Windows won't work. This problem is easily overcome by a tool that gives you more control over your hybrid MBR creation. I've seen patched versions of gptsync that do this, but these patches don't seem to have caught on. My own [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program can do the job, too -- see the earlier hybrid MBR link for details of how to use it to create a hybrid MBR.

One more point, which is a general multi-booting issue: I strongly recommend creating a separate FAT or NTFS data-exchange partition. It's generally unwise to access any OS's boot partition from another OS, since non-native filesystem support is often imperfect and security features are often useless in other OSes. These limitations make it easy to accidentally trash a boot partition. Using a separate data-exchange partition minimizes these risks and isolates them to a relatively unimportant partition. Such a partition should, of course, be included in the hybrid MBR along with the Windows boot partition.

---

### Post by oldfred on 2011-09-07
I really do not know Macs.

But I understand they use the newer gpt partitioning. But Windows will only boot from MBR*, so Apple uses a hybrid to boot Windows in BIOS/MBR mode and Mac in gpt mode. You have to sync teh two versions and the windows then has to be in the first partitions.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

*Win7 will boot from UEFI with gpt, but Mac is EFI and Apple does not use the Win7 UEFI mode.

---

### Post by temporalburst on 2011-09-10
Thanks for all the info. ^_^

I have Ubuntu installed and running fine now, all three operating systems booting properly as well.

---

