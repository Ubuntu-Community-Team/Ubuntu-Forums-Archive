---
title: "ASUS A55VD ubuntu doesn't recognize partitions . Help pls."
date: 2013-10-10
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Guitarboy314 on 2013-10-10
Hi everyone:

I have Windows 7, and i was running ubuntu 12.04 in a virtual machine but when i realized a dual boot, it appears this problem. I try using fdisk, nothing. i try resizing the default partitions from w7, nothing, and at last, i try reinstalling windows but i don' get to install it. I'm newer with ubuntu, so i need your advice.

I installed DIsk-repair. It doesn't appear nothing in advanced oprtions.So, i let you the boot repair info.

[http://paste.ubuntu.com/6219276](http://paste.ubuntu.com/6219276)

Thank you in advance.

---

### Post by oldfred on 2013-10-10
You have UEFI with efi boot and gpt partitioning.  

This error is the issue. But it seems to be the protective MBR partition, not the working gpt partitions.
      >  /dev/sda1 ends after the last sector of /dev/sda



The MBR partition table is just there so old partition tools do not try to format a gpt partition table..

I might try gdisk and see if it will write the correct MBR also, I think it does, but it is primarily for gpt partition work. It is in the repository, so you can directly download it.
sudo apt-get install gdisk
This will show partitions, not sure if it will mention error or not?
 sudo gdisk -l /dev/sda

      
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

    I think just loading gpt table and the using the w command to write will also update MBR.

---

### Post by Guitarboy314 on 2013-10-11
Thanks for replying!

I run gdisk and i upload the report. do i have to do anything else before applying w option?My hdd is 320GiB ,so, where's the last partition? can i resize it?

Disk /dev/sda: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 91B5A850-8718-4D8C-AA48-4DA569E5BEAE
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 2048-sector boundaries
Total free space is 4062 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          411647   200.0 MiB   EF00  EFI system partition
   2          411648          673791   128.0 MiB   0C01  Microsoft reserved part
   3          673792       250730495   119.2 GiB   0700  Basic data partition
   4       250730496       573941759   154.1 GiB   0700  Basic data partition
   5       573943808       625142447   24.4 GiB    2700  Basic data partition

Command (? for help): v

Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.

Identified 1 problems!

---

### Post by oldfred on 2013-10-11
That is showing another issue and says you need to shrink last partition.

But it seems like you are now in a catch 22. You cannot use partition tools to shrink partition because of error, but need to shrink partition to fix error.
Does sgdisk then work or not?

I do not know VM, so is that perhaps part of the issue?

---

### Post by Guitarboy314 on 2013-10-11
it appears the same message when i run gdisk oprtion w...

Command (? for help): w

Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
Aborting write of new partition table.

---

### Post by oldfred on 2013-10-11
This is by the author of gdisk on same issue.

[http://askubuntu.com/questions/150378/how-to-fix-mbr-partition-prior-to-ubuntu-installation-a-partition-overlaps-gpt](http://askubuntu.com/questions/150378/how-to-fix-mbr-partition-prior-to-ubuntu-installation-a-partition-overlaps-gpt)

It looks like you have to backup that partition and delete it. Then you should be able to recreate it slightly smaller.

---

