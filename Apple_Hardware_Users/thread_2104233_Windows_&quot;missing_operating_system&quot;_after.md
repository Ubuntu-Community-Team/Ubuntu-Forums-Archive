---
title: "Windows &quot;missing operating system&quot; after Ubuntu 12.10 instal?"
date: 2013-01-12
forum: Apple Hardware Users
---

### Post by jp1016 on 2013-01-12
Hi, I used rEFIt to install Ubuntu 12.10 on my macbook pro, which also had windows 7 on it. Now when I try to use the windows partition, it displays the message "missing operating system" on a black screen. If there's any other information needed I'll post more. 

Any help is appreciated! Thanks!

Here is a link to the other thread to see what I've already tried. I was told to start a thread in the APple sub-forum as people might know what to do :o

---

### Post by oldfred on 2013-01-14
You can "bump" thread every 24 hours to see if someone reviewing new threads sees your issue.

Your link to previous thread
[http://ubuntuforums.org/showthread.php?t=2097620](http://ubuntuforums.org/showthread.php?t=2097620)

---

### Post by luckylud on 2013-01-20
The better way to solve this problem is to forget Windose ...
I suppose you have installed windose in bios mod, and in this case your disk have probably a hybrid mbr/gpt partition table. After install of ubuntu gpt partition table as changed, mbr and gpt need to be synchronize.

install gptsync in ubuntu and launch :
# sudo gptsync /dev/sda

If your partitions tables aren't sync, answer yes to sync it.

Reboot and if windows doesn't start ... you'll need the windows install DVD to repair it.

---

### Post by Sola Gamal on 2013-02-12
> **luckylud said:**
> The better way to solve this problem is to forget Windose ...
I suppose you have installed windose in bios mod, and in this case your disk have probably a hybrid mbr/gpt partition table. After install of ubuntu gpt partition table as changed, mbr and gpt need to be synchronize.

install gptsync in ubuntu and launch :
# sudo gptsync /dev/sda

If your partitions tables aren't sync, answer yes to sync it.

Reboot and if windows doesn't start ... you'll need the windows install DVD to repair it.
I have a similar problem, i installed ubuntu 12.10 and now i have no windows 7 that was on C or the NTFS drive (D) that was my data on it.
when i run fdisk -l i recognized the gpt and syncronized it now the output is:
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x56a045f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2047        1023+  ee  GPT
Partition 1 does not start on physical sector boundary.
/dev/sda2   *        2048    39063551    19530752   da  Non-FS data
/dev/sda3       156250112   164063231     3906560   82  Linux swap / Solaris
/dev/sda4       164063232   171876351     3906560   82  Linux swap / Solaris

and when i logged with Windows 7 DVD i found C and D became unallocated space.

any one know what does it means?
how come that happen?
and if there is any solution for return my data that was on D drive?

---

### Post by oldfred on 2013-02-12
@Sola Gamal
Is yours a Mac? The OP has a Mac and those issues would be a lot different than a Windows system. Windows only boots from gpt with UEFI, but with a Mac they usually create a hybrid MBR/gpt drive. So the Mac and boot with efi and Windows with BIOS.
Best to have your own thread.

---

