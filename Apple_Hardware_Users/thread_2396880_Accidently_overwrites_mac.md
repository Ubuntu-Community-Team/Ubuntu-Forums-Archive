---
title: "Accidently overwrites mac"
date: 2018-07-22
forum: Apple Hardware Users
---

### Post by imraj3 on 2018-07-22
Hi,

I dual booted my mac with ubuntu using a tool called reFInd, But after finishing the process, I can't access my mac partition again and ubuntu takes up all the hard disk spaces on my mac. 
. 
And after shutting down or restarting, it goes straight to ubuntu without showing the reFInd menu and I can't access the macOS.

Any help is really appreciated because my backup isn't up to date and I'm yet to backup some important files on the mac partition. 

Thanks.

---

### Post by TheFu on 2018-07-22
Backups sound like the only solution to this problem.  Not having them would mean that data is gone.
To start, let's see if what you've described really happened.

Run
```
sudo fdisk -l
```
Post the output using code tags (Adv Reply #), like I did.

Let's cross out fingers that you are mistaken.

---

### Post by imraj3 on 2018-07-22
Here is the output

```


Disk /dev/sda: 113 GiB, 121332826112 bytes, 236978176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: F901A259-DF51-4F59-A6E9-953131BC1799

Device         Start       End   Sectors   Size Type
/dev/sda1       2048      4095      2048     1M BIOS boot
/dev/sda2       4096 220323839 220319744 105.1G Linux filesystem
/dev/sda3  220323840 236976127  16652288     8G Linux swap


Disk /dev/sdd: 14.7 GiB, 15728640000 bytes, 30720000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x05473618


```

---

### Post by oldfred on 2018-07-22
Moved to Apple sub-forum, since a Mac.

You show a BIOS type install on a Mac which normally is UEFI(EFI).
Your sda1 as bios boot is default for BIOS installs on gpt partitioned drives.
UEFI would normally have first (or near first) partition as ESP - efi system partition, FAT32 and boot flag or other codes to indicate it is the UEFI system boot partition.
In erasing the ESP, you also erased rEFInd which is a boot manager installed in the ESP in a separate folder.
Restore from your backups is about the only choice. Testdisk or photorec may find some data.

There is testdisk to find old partitions, but since a lot of data was overwritten its deeper search may not find anything. If it does immediately copy to another drive.
         [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 
    
If you had some vital data you may be able to recover some of it, but a long process as you have to scan drive for anything that looks like a file and it only recovers file extension.
         [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by imraj3 on 2018-07-22
I've run photorec and I got 1614 recup_dir folders, most of which are text files with random text. A sample screenshot can be found here : [https://ibb.co/k9xEzJ](https://ibb.co/k9xEzJ)

---

### Post by oldfred on 2018-07-22
When I ran photorec, I got valid extensions like .txt, but no file names. 

So then I sorted by size to approximate which files were which and then started doing compares with my backup which was a bit old. Took weeks to do compares. Photorec found all the deleted copies some older than backup, so a lot of work to try to figure out which was correct. Or learned to do better backups.

---

