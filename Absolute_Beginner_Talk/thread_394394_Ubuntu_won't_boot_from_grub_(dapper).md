---
title: "Ubuntu won't boot from grub (dapper)"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by antoz on 2007-03-26
Just finished installing Ubuntu on my new computer, but I am having a problem it won&#8217;t boot from the grub, gives me an error message unable to mount 00. I think I stuffed it up when I created the partitions and created an extended partition instead of a primary. I did get a message during the installation about unable to mount a partition but I thought it was the windows partition and just skipped it. I wonder if I can fix the problem from the live CD or if I have to reinstall? 
I have no problem booting windows from the grub.

---

### Post by BrianK on 2007-03-26
Check menu.lst in /boot (you may have to boot from the install disk & mount the boot partition by hand).  Make sure menu.lst is correct - specifically the kernel you are trying to boot (which should be the first uncommented line).  It sounds like grub got installed on the disk correctly if you can boot into windows, so it may just be that the mappings are wrong in menu.lst

---

### Post by antoz on 2007-03-26
Thanks for the reply, will give it a go later, but I am not sure if it is possible to save changes with the live CD. I have since checked my partitions and it is a primary partition so this is not the problem. The grub menu is fine but I can only boot into windows, everything else gives me the error message, including the recovery mode.

---

### Post by antoz on 2007-03-26
A bit more info: fstab

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda7 swap swap defaults 0

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   104326109    52163023+   7  HPFS/NTFS
/dev/sda2       104326110   466672184   181173037+   f  W95 Ext'd (LBA)
/dev/sda3       466672185   488006504    10667160   83  Linux
/dev/sda5       104326173   385977689   140825758+   7  HPFS/NTFS
/dev/sda6       385977753   426943439    20482843+   b  W95 FAT32
/dev/sda7       426943503   432421604     2739051   82  Linux swap / Solaris
/dev/sda8       432421668   466672184    17125258+  83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   316127069   158063503+   7  HPFS/NTFS
/dev/sdb2       316127070   390716864    37294897+   5  Extended
/dev/sdb5       316127133   390716864    37294866    7  HPFS/NTFS

Disk /dev/sdd: 257 MB, 257948672 bytes
33 heads, 63 sectors/track, 242 cylinders, total 503806 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              32      503805      251887    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(249, 32, 63) logical=(242, 10, 58)
ubuntu@ubuntu:~$

If anyone could have a look at this and tell me it is possible to do something about my problem or if I need a reinstall 
Cheers, A
PS: menu lst is blank probably because I am using the live CD since I can't boot into ubuntu

---

### Post by zvacet on 2007-03-27
[http://ubuntuforums.org/showthread.php?t=76652&highlight=reinstall+grub]("http://ubuntuforums.org/showthread.php?t=76652&highlight=reinstall+grub")

---

### Post by BrianK on 2007-03-27
> **antoz said:**
> Thanks for the reply, will give it a go later, but I am not sure if it is possible to save changes with the live CD. I have since checked my partitions and it is a primary partition so this is not the problem. The grub menu is fine but I can only boot into windows, everything else gives me the error message, including the recovery mode.
You can, infact save changes using the live CD, however, you need to be sure you're editing the correct file.  do this:

mkdir disk
*<good lord, why do you have so many partitions?>*
sudo mount /dev/sda3 disk
cd disk
ls

that last ls should be your installed OS drive.  I have no idea how you've partitioned your disk, so sda3 may be the wrong partition.  In any event, you get the jist - mount your hard drive, then edit the files on the drive.

the fstab you posted was the fstab from the live CD & is of no use.

menu.lst is blank because it's the menu.lst from the live CD.

Please get the menu.lst off the disk (which you can get to once you've mounted the partition) & post it here.  Once we see that, we can help out more.  ;)

---

### Post by antoz on 2007-03-29
Thanks BrianK
Sorry I have not answered earlier but I had started a new thread [URL="http://www.ubuntuforums.org/showthread.php?t=394493"]http://www.ubuntuforums.or
g/showthread.php?t=394493[/URL]
The boot problem is resolved after I edited my menu lst but I now have a login problem you can have a look at the other thread.
As for the number of my partitons; windows, my documents, a fat 32 for sharing with Ubuntu, sda3 for my Ubuntu, linux swap and sda8 is my home partition, this is the one that gives me trouble with login.
Cheers,A.

---

