---
title: "Vista bootloader GONE...... HELP!"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by AriciU on 2007-06-22
I've wrote GRUB to the MBR replacing the Vista boot loader. I did that because i could not get Vista's bootloader to load Ubuntu.

I have 3 hard drives and 2 OS's, Vista and Ubuntu 7.04.

I've followed this guide ([http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)) to replace Vista's bootloader with GRUB.

Ubuntu loads up just fine now, no problems with it. The problem is that when i want to load Vista's bootloader to boot Vista i get this error:

> Error 18: Selected cylinder exceeds maximum suported by BIOS

I've done some research on that and found out that the error pops up because the BIOS has troubles booting a specific OS if it's not written on the first 8GB of the drive or something like that. It also said that new hardware (mobo, bios) is not supposed to have that problem.

My motherboard is a Gigabyte GA-K8NS-Ultra. Not new by recent standards but no dinosaur either...

I will attach below a copy of my GRUB menu.lst

> title		Windows Vista (loader)
root		(hd1,1)
savedefault
chainloader	+1

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd2,3)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=1ea44946-645f-4375-bef1-262d2e21f2f0 ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

............. etc etc etc

This is the output of "df -h" to see how my drives are setup:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              29G   11G   17G  40% /
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  132K  506M   1% /proc/bus/usb
udev                  506M  132K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/sdb4             492M  170M  296M  37% /boot
/dev/disk/by-uuid/CA9C369A9C36814D
                      129G   87G   42G  68% /media/hdb1
/dev/disk/by-uuid/BCA83A94A83A4CE0
                       21G   19G  2.1G  91% /media/hdb2
/dev/disk/by-uuid/122983EA943B1179
                      179G  170G  9.2G  95% /media/sda1
/dev/disk/by-uuid/767C51E77C51A2A3
                      4.9G  4.5G  451M  91% /media/sda3
/dev/disk/by-uuid/DC0C43580C432CB8
                      3.0G  2.8G  162M  95% /media/sda5
/dev/disk/by-uuid/BA70867470863763
                      269G   76G  193G  29% /media/sdb1


Here's an output of "fdisk -l" :

> fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      371368   187169440+   7  HPFS/NTFS
/dev/sda2          381527      387621     3071880    f  W95 Ext'd (LBA)
/dev/sda3          371369      381526     5119632    7  HPFS/NTFS
/dev/sda5          381527      387621     3071848+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      266993   134564440+   7  HPFS/NTFS
/dev/hdb2          266994      310099    21725376    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37199   281224408+   7  HPFS/NTFS
/dev/sdb2   *       37200       41206    30292920   83  Linux
/dev/sdb3           41278       41345      514080   82  Linux swap / Solaris
/dev/sdb4           41207       41277      536760   83  Linux

Partition table entries are not in disk order
fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      371368   187169440+   7  HPFS/NTFS
/dev/sda2          381527      387621     3071880    f  W95 Ext'd (LBA)
/dev/sda3          371369      381526     5119632    7  HPFS/NTFS
/dev/sda5          381527      387621     3071848+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      266993   134564440+   7  HPFS/NTFS
/dev/hdb2          266994      310099    21725376    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37199   281224408+   7  HPFS/NTFS
/dev/sdb2   *       37200       41206    30292920   83  Linux
/dev/sdb3           41278       41345      514080   82  Linux swap / Solaris
/dev/sdb4           41207       41277      536760   83  Linux

Partition table entries are not in disk order

The Ubuntu boot partition is /DEV/SDB4 (HD2,3). The Vista partition is /DEV/HDB2 (HD0,1 or HD1,1 -> i've tried booting both by editing GRUB's menu.lst but still no go).

I noticed looking at the fdisk output that /dev/hdb2 (vista) is not set up as a "boot" partition (/dev/hdb1 is witch is just my other stuff, programs, etc partition).

Could this be it? I don't think so considering the GRUB error 18.

Hope you can help me fix this :)

---

### Post by AriciU on 2007-06-22
No one?

---

### Post by m_atif on 2007-06-22
hmm Not sure... i am just writing it for the sake of discussion. :) and giving the worst case  scenario solution. Dont do it till you get some experts advise. :)

It seems that you have lost/forgotten the partition number of windows Vista. try sdb1 as well. It also seems to be NTFS partition.

one way is to put in the vista CD and type fixmbr. That will fix the MBR for vista. Now you would NOT be able to boot to linux as grub will be gone, but surly you can go into vista. 

Now put in the live CD and go inside the linux drive and reinstall linux (dont do it, wait for some expert to give proper guidance.

---

### Post by AriciU on 2007-06-22
LMAO. I'm an idiot :)

1. Windows can't boot if the boot loader is setup on the second partiton of a drive. It must be on the first partition.

2. I had root (hd0,1) in grub's menu.lst because that's where i had the Windows Vista installation (2nd partition of the HDD)

3. I forgot that the boot loader was installed by default on the 1st partition.

So...

One 

> root (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)

later and Vista booted fine :D

---

