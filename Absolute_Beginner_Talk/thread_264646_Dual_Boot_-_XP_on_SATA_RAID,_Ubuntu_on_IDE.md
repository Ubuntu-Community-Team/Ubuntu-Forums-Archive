---
title: "Dual Boot - XP on SATA RAID, Ubuntu on IDE"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by slockton on 2006-09-25
Hello,

I'm starting to play about with Ubuntu (6.06) and I have a question about dual-booting with XP. I have Windows XP Pro on a RAID 1 array (two mirrored 320GB SATAII HDs), and I also have a 250GB IDE hard drive installed as spare storage. I wanted to install Ubuntu on a partition on this 250Gb drive.

I browsed these forums to get the best way to do this and I mostly followed the advice given in this post: [http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata](http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata)

I've been bitten before with the MBR being messed up by grub/lilo, so before installing Ubuntu on 50Gb of unallocated space on the IDE drive, I unplugged my two SATA drives. Just in case.

So right now I have the two OSs installed, but can only choose which OS to boot by changing the hard drive boot order in the BIOS. This is not ideal. The idea behind the link I posted above was you boot first off the Ubuntu IDE drive and get grub to choose between your XP and Ubuntu installs - this way the grub never touches the XP partition/drive/array. 

However, because I unplugged my Windows drives when installing Ubuntu, when I cd to /boot/grub and open menu.lst with gedit XP is not listed, so I cannot make the necessary edits to the file (as described in the above link) to be able to boot windows as default with grub.

So, what do I have to do so I can boot from the IDE drive first and have grub load the Windows install from the RAID 1 array as default? I don't have to reinstall anything do I? 

Thanks,
Steve

---

### Post by confused57 on 2006-09-25
Windows won't be listed in your menu.lst, since your SATA drives were disconnected during Ubuntu install...just add a new entry similar to the one listed in the link at the very end of the file.

Also, see this thread for a possible Windows entry:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

You might want to boot into Ubuntu & open a terminal, enter:
```
sudo fdisk -l
```
The -l is a small "L".

This will show your partition tables of your hard drives, Ubuntu "may" see your raid as a single hd...I'm not familiar with raid or SATA hard drives.

---

### Post by slockton on 2006-09-25
Hi,

Thanks for the reply. I did the fdisk and this is the output:

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            6173       30401   194619442+   f  W95 Ext'd (LBA)
/dev/hdb2   *           1        6172    49576558+  83  Linux
/dev/hdb5            6438       30401   192490798+   7  HPFS/NTFS
/dev/hdb6            6173        6437     2128549+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38912   312560608+   7  HPFS/NTFS


It looks like Ubuntu does NOT see the RAID array, but two SATA drives. Is there a way of getting Ubuntu to see the opposite? Does it matter? If you could just use sda in a menu.lst entry to refer to the array, what would the code be?

Cheers,
Steve

---

### Post by slockton on 2006-09-27
So, no ideas then?

I have an intel 955XBK motherboard. I *think* my array is hardware RAID. When changing around the boot order to make the IDE drive boot first, I switch between "Intel RAID1" and the IDE, so the hardware recognises it in the BIOS.

Why can't ubuntu recognise the array?

Do I need some kind of driver for ubuntu? If so, which one and where do I get it?

Thanks,
Steve

---

### Post by slockton on 2006-09-27
I have some further information.

I'm currently booted in ubuntu via the live CD.

I used file browser to navigate to "Computer" - and it displays my windows drives - *including the RAID1 array*. I try to open it and it says it is "Unable to mount the selected volume" - error: device /dev/sdb1 is not removable; error: could not execute pmount

I also cannot open the IDE drive (which is strange) for the same reason: "Unable to mount the selected volume" - error: device /dev/hdb5 is not removable; error: could not execute pmount

Though, for the IDE drive, I left 50GB of unallocated space at the start of the drive for the Ubuntu install - might be messing things up...

Does this give anyone any clues?
Steve

---

### Post by Malta paul on 2006-09-27
Hi, I may be doing this all wrong but I use Windows XP on my SATA drive and Ubuntu on my older IDE drive. Running Ubuntu I can then access (read only) my windows NTFS files, for viewing Photos, documents, PDF files, Play video ISO files and listen to my music files.

How? I go into the BIOS on computer start up, then to 'Intergrated periphals' where I change the drive from 'Both SATA and IDE' to SATA only. F10 to save and the system now boots into Ubuntu on the IDE drive. To change back to windows I reboot and change back to 'Both SATA an IDE' F10 and the system starts in windows.

Well this procedure works good for me! :) maybe it would work for you?
cheers Paul.

---

### Post by slockton on 2006-09-27
Hi,

Thanks for the reply.

I can already change the drive order in my BIOS from "Intel RAID1" (XP) to the IDE drive (ubuntu) to swap which OS boots. I really am looking for a solution that will install grub on the IDE drive and load Windows from the SATA RAID by default.

The problem is, Ubuntu does seem to recognise RAID arrays...

Steve

---

### Post by gn2 on 2006-09-27
With my motherboard, MSI, pressing F8 at boot time gives a list of devices to boot from.
In the Bios I have the default Linux OS (IDE slave) first in the boot order, and when I need the other OS I re-boot, press F8 and choose the drive with the other OS (XP home) on it (IDE master)

---

### Post by slockton on 2006-09-27
I think if I had two IDE drives like you it wouldn't be a problem.

There's something wierd going on between Ubuntu and recognising my two SATA drives as a RAID1 array.

](*,) 

Thanks,
Steve

---

### Post by gn2 on 2006-09-27
So the problem is trying to access files on the SATA raid array then?

would this help: [http://www.ubuntuforums.org/showthread.php?t=2557&highlight=mount+sata+raid+array](http://www.ubuntuforums.org/showthread.php?t=2557&highlight=mount+sata+raid+array)

---

### Post by slockton on 2006-09-27
Kind of.

I need grub to be able to recognise that I have windows on a SATA RAID1 array and boot from that as default.

So, I want to IDE drive to boot first, load grub, then have the option of booting Windows or Ubuntu.

Because grub doesn't see the RAID array, it cannot load Windows.

Steve

---

### Post by confused57 on 2006-09-27
Maybe you've already tried this, but you can open your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```

and add a Windows entry similar to this at the very end of the file:

```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

