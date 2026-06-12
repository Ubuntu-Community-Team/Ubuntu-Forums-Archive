---
title: "updating GPT from MBR ?"
date: 2007-09-02
forum: Apple Intel Users
---

### Post by karl_kashofer on 2007-09-02
Hi !

I have decided my Ubuntu needs more space and I have resized the Ubuntu partition /dev/sda4 by deleting and recreating a bigger partition using fdisk from the ubuntu install cd.

This works fine, parted, fdisk and cfdisk show the partition with the new size. However this is only in the MBR partition table, resize2fs does not see the new size most probably because its reading the gpt partition table.

So my question is:
Is there a way to sync the gpt partition table to be the same as the MBR one ?
gptsync only does GPT to MBR not the other way round...

Help highly appreciated,
Cheers,
Karl
Macbook 13.3 2.16Ghz

---

### Post by benanzo on 2007-09-02
If OS X was the first system to partition the disk, the MBR will just be a protected block in the GPT.  The GNU Parted version in Feisty is supposed to recognize the presence of the GPT and update it automatically.  This is why we shouldn't have to do any tricky GPT/MBR syncing when first installing Ubuntu on a GPT disk (unlike on Edgy.)

Just to clarify, you're using Feisty+ right?  Not Edgy or Dapper?  Older versions don't see the GPT and it therefore doesn't get updated when using the partioners on Ubuntu.

At this time I'm unaware of a way to sync GPT -> MBR.  You might poke around with Apple's Disk Utility to see if anything can be done.

Good Luck!

---

### Post by cyberdork33 on 2007-09-02
> **karl_kashofer said:**
> Hi !

I have decided my Ubuntu needs more space and I have resized the Ubuntu partition /dev/sda4 by deleting and recreating a bigger partition using fdisk from the ubuntu install cd.

This works fine, parted, fdisk and cfdisk show the partition with the new size. However this is only in the MBR partition table, resize2fs does not see the new size most probably because its reading the gpt partition table.

So my question is:
Is there a way to sync the gpt partition table to be the same as the MBR one ?
gptsync only does GPT to MBR not the other way round...

Help highly appreciated,
Cheers,
Karl
Macbook 13.3 2.16Ghz

Those tools do not update the gpt. gparted does.

---

### Post by karl_kashofer on 2007-09-03
Hi !

You are right, I have downloaded the gparted livecd. I had to realise that apple refuses to boot gparted from usb so I burnt a cd. After using an external keyboard to select gparted-macbook i was then able to resize the ext3 partition.

After reboot I started the partitioning tool from refit and had the mbr updated.

After the next reboot it now refuses to boot with "Missing operating system"......

I have checked /dev/sda4 from gparted lifecd, it contains all files.
I also tested booting into macos, that works as well.

Something seems to be wrong with refit, it now displays a different icon for the ubuntu partition, there is no longer the penguin, it now is a generic hdd symbol. (same is true for the gparted lifecd)....

Any hints anyone ?

Thanks,
Karl

---

### Post by karl_kashofer on 2007-09-03
Hi !

I solved this, seems i lost my mbr somewhere down the road, including the grub stage 1.5. Maybe gptsync destroyed it after the resizing of the partition with parted ?

so, to solve this problem you have to reinstall grub in the mbr as follows:

start from the live-cd
open a terminal

>sudo grub
>find /boot/grub/stage1
>=> this should say something like (hd0,3)
>root (hd0,3)
>setup (hd0,3)

reboot, and voila the penguin is back !!

Thanks for your help guys,
Cheers,
Karl

---

### Post by pxwpxw on 2007-09-03
> **karl_kashofer said:**
> Hi !

I solved this, seems i lost my mbr somewhere down the road, including the grub stage 1.5. Maybe gptsync destroyed it after the resizing of the partition with parted ?

so, to solve this problem you have to reinstall grub in the mbr as follows:

start from the live-cd
open a terminal

>sudo grub
>find /boot/grub/stage1
>=> this should say something like (hd0,3)
>root (hd0,3)
>setup (hd0,3)

reboot, and voila the penguin is back !!

Thanks for your help guys,
Cheers,
Karl

There grub is being  installed in hd0,3 partition 4 boot sector, away from the MBR (hd) at the start of the disk. I went through the same sort of procedure here, but grub on partition 3 ( windows XP on p4).

---

