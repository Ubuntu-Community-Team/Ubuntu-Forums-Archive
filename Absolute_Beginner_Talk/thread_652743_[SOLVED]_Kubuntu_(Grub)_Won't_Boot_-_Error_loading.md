---
title: "[SOLVED] Kubuntu (Grub) Won't Boot - Error loading OS"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by eternicode on 2007-12-29
Intro:
I had my Dell E1705 dual-booting XP and Kubuntu Feisty perfectly - XP on a primary partition, linux root and swap and FAT32 share partitions inside an extended partition.  Recently, I've decided to move my /boot and /home to separate partitions, as well as making a separate partition for my music files (so my NTFS isn't in use all day by Amarok ;) ).

As for why I want to repartition....just because :) good experience.

Original partitioning:
```

|   |                     |[|       |                   |    |]|       |
|-1-|---------NTFS--------|[|-share-|-------ext3--------|swap|]|---2---|
|   |                     |[|       |                   |    |]|       |

1 = Dell diagnostics partition
2 = Dell System Restore partition
[] = extended partition

```

The Process:
So, I boot up the latest version of SysRescCD (version 0.4.2 Stable) on a CD-RW.  startx, load up GParted, do a little paper math, and settle on a scheme.  First thing I do is shrink my NTFS by 10GiB, move the beginning of my extended partition to the left to take the space, and create a new 10GiB ext3 partition in the space inside the extended partition.  So far so good.

Next, I mount my linux root partition and the new home partition and copy over all the files with the line

```

cp -aRv /mnt/root/home/* /mnt/home/

```

I'm fairly certain that the -a switch is sufficient to take care of symlinks and such.  After that, I "du -sh --block-size=M" both the old and new directories, and they're the same size.  On the root partition, I move home to old_home and make a new /home directory there.

The new home partition is /dev/sda8.  Next, using "tune2fs -l /dev/sda8", I get the device's UUID and modify the fstab on the root accordingly ("UUID=***  /home  ext3  defaults,errors=remount-ro  0  1", just like the root).  Save, unmount everything, reboot.

The Problem:
The computer reboots, I take out the CD, and I get "Error loading OS". No grub or anything.  I'm assuming that this is because the partition I added is physically before the previously used root partition, so grub just can't find /boot/grub/stage* or menu.lst.

So I booted the rescue cd back up and tried "grub"
```

grub> find /boot/grub/stage1
(hd0,6)

grub> root (hd0,6)
  Filesystem is ext2fs, partition type 0x83

grub> setup (hd0)
  Checking if "/boot/grub/stage1" exists... yes
  Checking if "/boot/grub/stage2" exists... yes
  Checking if "/boot/grub/stage1_5" exists... yes
  Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
  Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,6)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub>

```

I reboot, and the same problem, error loading OS.

So I'm not quite sure what to do now.  I've made a backup before I started this, but I'd like to fix this and move forward with my genius partitioning XD

Thanks for any help (and for taking the time to read 8-[ ), and let me know if you need more info!

----------------------------

And, of course, as I typed this I tried something that worked #-o

I booted back into SysRescCD, re-entered grub, and followed the *exact same* process I used before...except at the end, instead of "quit" to get out of grub, I typed "reboot".

"shutdown -r now" at the prompt, remove the cd, and presto, it boots right up...

The new home partition seems to be working perfectly, just have an issue with my System Tray Icons having their own windows....

Anyways, I'll post this for others' reference. :lolflag:

---

