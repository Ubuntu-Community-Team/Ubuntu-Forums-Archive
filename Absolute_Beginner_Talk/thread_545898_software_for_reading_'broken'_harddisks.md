---
title: "software for reading 'broken' harddisks"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by john-luck on 2007-09-08
Hi,

I had serious troubles with my primary harddisk. Now, ubuntu tells me that it cannot mount the disk, and dmesg|tail shows me:

ubuntu@ubuntu:~$ dmesg|tail
[  600.555137] NTFS-fs error (device sda1): ntfs_fill_super(): Failed to load system files.
[  616.647380] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  616.658815] NTFS volume version 3.1.
[  616.658972] NTFS-fs error (device sda1): map_mft_record_page(): Mft record 0x5 is corrupt.  Run chkdsk.
[  616.658977] NTFS-fs error (device sda1): map_mft_record(): Failed with error code 5.
[  616.658981] NTFS-fs error (device sda1): ntfs_read_locked_inode(): Failed with error code -5.  Marking corrupt inode 0x5 as bad.  Run chkdsk.
[  616.659568] NTFS-fs error (device sda1): load_system_files(): Failed to load root directory.
[  616.659757] NTFS-fs error (device sda1): ntfs_fill_super(): Failed to load system files.
[  622.020347] NTFS-fs warning (device sda1): parse_options(): Option utf8 is no longer supported, using option nls=utf8. Please use option nls=utf8 in the future and make sure utf8 is compiled either as a module or into the kernel.
[  622.031438] NTFS volume version 3.1.

There was also an XP-installation on the same disk. XP-boot cd now shows c:\ as unknown partition type. 

Are there any programs out there that could read the disk in some way? Just for a few files I want to keep. After that I don't care if the disk ends up in the trash.

Also, I tried to do what the system advised me : run chkdsk, but :

ubuntu@ubuntu:~$ chkdsk
bash: chkdsk: command not found

ANY help is much appreciated. 

Thanks.

John Luck Pickerd

---

### Post by JohnCub on 2007-09-08
I've used [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) in the past with good results.

---

### Post by mikeyphi on 2007-09-08
I think chkdsk is a MS utility - if you still have your MS disc or a recovery Floppy you should be able to run it.
Also you might want to open synaptic and install 'ntfs-config'. It should give you better support for the windows partition - it the disk is still OK.

Some further info: I don't think you will be able to boot into your windows partition unless you go via the Grub.

---

### Post by john-luck on 2007-09-09
Thanks for the info guys. I just burned a knoppix cd with testdisk. 

I'll keep you informed on the results. I'll let you know how much fire and smoke was involved in the process.


Yours, John-Luck Pickerd

(Anonymity... relish the thought)

---

### Post by n3tfury on 2007-09-09
> **john-luck said:**
> Thanks for the info guys. I just burned a knoppix cd with testdisk. 

I'll keep you informed on the results. I'll let you know how much fire and smoke was involved in the process.


Yours, John-Luck Pickerd

(Anonymity... relish the thought)

using a thumb drive, you should be able to recover your files with no problems.  you can also try [[COLOR="DarkOrange"]spinrite[/COLOR]]("http://www.grc.com/spinrite.htm"), but it's not free.

---

### Post by john-luck on 2007-09-09
Well.....

I tried a knoppix cd with testdisk. It took a while with permissions and library files, but I got it to work. 
It announced that my drive's bootsector was inconsistent with my backup bootsector. So, I replaced the current one with the backup.... no help. Testdisk now shows no errors, but breaks when I choose to have it list the files. (segmentation error or something)

So what's a thumb drive? Sounds interesting :p. Alot more so than spinrite, as I'm strapped for cash.

Thanks guys,

John Luck Pickerd

oh... btw, my drive is NTFS

---

### Post by n3tfury on 2007-09-09
flash drive = thumb drive = usb stick = whatever :)

live boot with Knoppix, insert flash drive, recover files.

---

### Post by john-luck on 2007-09-09
> **n3tfury said:**
> flash drive = thumb drive = usb stick = whatever :)

live boot with Knoppix, insert flash drive, recover files.

aha... ok, but I can't get to my files. 

Testdisk sees a primary bootable  NTFS-partition, when at the same time, other programs can't see into the disk (the disk itself is recognised as correct type and size)

WinXP-cd says: Partitiontype unknown... (not unpartitioned).

---

### Post by n3tfury on 2007-09-09
> **john-luck said:**
> aha... ok, but I can't get to my files. 

Testdisk sees a primary bootable  NTFS-partition, when at the same time, other programs can't see into the disk (the disk itself is recognised as correct type and size)

WinXP-cd says: Partitiontype unknown... (not unpartitioned).

hm, not sure then.

---

