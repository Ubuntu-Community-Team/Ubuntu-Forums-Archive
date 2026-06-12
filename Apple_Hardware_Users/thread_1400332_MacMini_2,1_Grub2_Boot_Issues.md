---
title: "MacMini 2,1 Grub2 Boot Issues"
date: 2010-02-06
forum: Apple Hardware Users
---

### Post by jlalicker on 2010-02-06
Hi guys, I've been using Ubuntu since about 7.10, but I haven't done anything that out of the ordinary, so I haven't needed to post on the forums.

I won't bore you with the details, but I recently decided that I want Ubuntu as the only OS.
After a bit of trouble, I finally got it installed using Grub2. Now for the issues.

1. In order to boot, I have to hold down alt and pick "windows" as the os, which is Ubuntu (OS X is on an external which isn't usually connected). Is there a fix for this?

2. When I ran grub-install, it tells me the following:
 ```
grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.
```fdisk -l outputs this: 

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000010c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              34        1987         977   ef  EFI (FAT-12/16/32)
/dev/sda2   *        1988   228628941   114313477   83  Linux
/dev/sda3       228628942   234441614     2906336+  82  Linux swap / Solaris

```Anyone have any ideas how I can boot without having to hold down alt every time and if embedding/not being able to is an issue. I'll keep an eye on this thread and try to provide any additional information that is needed.

[COLOR=Red][B]UPDATE:
[/B][COLOR=Black]I had a hunch that the EFI framework wasn't being allowed to work because of the size of my EFI Partition. I considered using gParted, but considering an install is considerably faster, I went that route. This time around I manually partitioned my hard drive, 200MB EFI, then Ubuntu, then Swap. This seems to work perfectly on 9.10, It takes a little while to boot, I'm guessing it is because I have to wait through the grub selection screen until the Linux Kernel is loaded, but it now single boots no problem.[/COLOR]
[/COLOR]

---

