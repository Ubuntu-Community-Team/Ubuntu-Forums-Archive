---
title: "Uninstalling WinXP ?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by kozak on 2005-12-23
As far as I know,   I did not delete or remove Windows XP before I
installed Ubuntu. I may have setup partitions, I can't remember.
Does anyone know how to check or remove windows xp ?
As I would like to free up the space, I don't need it anymore.

---

### Post by kwaanens on 2005-12-23
Use gparted or qtparted to partition the XP space.

They can be found from Applications > System Tools if they are installed. Use Synaptic if they're not. (or "sudo apt-get install gparted" or "qtparted")

- Ketil

---

### Post by kozak on 2005-12-23
I got Gparted.
I tried, but it doesn't let me partition anything.
I think I am mounted or something.
But it won't let me un-mount.

---

### Post by kwaanens on 2005-12-23
That's probably because you're trying to format something that is mounted. That is generally not a good idea... (Because Ubuntu is using it, so it's probably necessary)
If you want to fomat something that is mounted when you boot up Ubuntu, try sysresccd.org.

However, listing your partition table here may make it easier to help you what is going on. (sudo fdisk -l)

- Ketil

Edited to be a little clearer.
Edited once more with the command to list partitions

---

### Post by kozak on 2005-12-23
I am a noob.
I like ubuntu better,
so I don't really need WinXP at all,
thats why I want to remove it.
Does ubuntu require WinXP to run ?

Is this what you would like to see ?
kozak@S0106000ea6e06f1e:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            7054        9729    21494970    5  Extended
/dev/hda5            7299        9729    19527007+  83  Linux
/dev/hda6            7055        7297     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order
kozak@S0106000ea6e06f1e:~$

---

### Post by kwaanens on 2005-12-23
If you did a clean install of Ubuntu, without keeping your XP, XP should be gone.

I don't know everything about this, but it looks like your only partitions are the Swap partition and your Ubuntu partition.

Me thinks: XP gone :)

And, no Ubuntu doesn't require XP, of course.

The limit to partitioning after having booted up Ubuntu from your hard drive is (AFAIK):
- You can't screw aroun with your mounted partitions
- Which means, that you can't do anything with logical volumes that contain Linux either.

In Gparted you will be able to see used and unused space. This should amount to about 80 gigs on your system.

- Ketil

---

### Post by kwaanens on 2005-12-23
For reference: My partition table looks like this:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        1934    15454530    7  HPFS/NTFS
/dev/sda3           11803       12161     2883667+  db  CP/M / CTOS / ...
/dev/sda4            1935       11802    79264710    f  W95 Ext'd (LBA)
/dev/sda5            1935        9471    60540921    c  W95 FAT32 (LBA)
/dev/sda6            9472        9662     1534176   83  Linux
/dev/sda7            9663       11802    17189518+  83  Linux

Partition table entries are not in disk order


And it has XP, Dell system restore, Dell Media Crap (R), Ubuntu (and swap), and a shared fat32 partition to use with Ubuntu and XP.

- Ketil

---

### Post by kozak on 2005-12-23
Is there any way I can get this 55,325 MB Unallocated space,
into my main linux partition ? 
[IMG]http://i18.photobucket.com/albums/b145/kozak420/Screenshot.png[/IMG]

---

### Post by kozak on 2005-12-23
I am so confused lol.

---

### Post by kwaanens on 2005-12-23
That's going to pose a problem, maybe. But try sysresccd.org. Boot with it and see what you can do. But back up your essentials first!

The only other solution I can think is to do a clean install, overwriting everything.

Good luck!

PS. Good thing you posted this image, because unallocated stuff doesn't show up in fdisk -l, and I don't like adding every number :)

- Ketil

---

### Post by kwaanens on 2005-12-23
Two more ways to use this space:

First, back up your essentials.

- Boot with Ubuntu live

- Try to copy hda1 to unallocated space

- Restart, click esc in grub so you can manually boot from your newly created partition. Booting will take a while. 

Open Gparted to see what partitions you use right now.

- Edit /boot/grub/menu.lst in order to point to your newly created partition.

- If you get error messages after a new reboot, just fix the things they throw at you (probably not a lot)


-----

2nd option:

Make a new partition in unallocated space, in whatever file system you'd like. (I like ext3)
Put it in /etc/fstab, making it mount as /mnt/storage, for instance

Probably the easiest, reinstalling everything is probably the second easiest.

- Ketil

---

