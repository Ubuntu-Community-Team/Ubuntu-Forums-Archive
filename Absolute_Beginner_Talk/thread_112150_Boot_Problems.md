---
title: "Boot Problems"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by UncleBulgaria on 2006-01-03
Hi!

After toying with the idea of having a go with Linux for a while I have taken the plunge and given it a go using Ubuntu 5.04 distribution that was given away with the February 2006 edition of Computer Shopper magazine.  I am dual-booting with Windows XP Pro x64 edition and I have installed Linux on a partition that is on a different hard drive to the XP installation.

The problem I have is that I can install and boot 2 or 3 times but then I get error messages and Ubuntu refuses to boot.  The first time it happened I was using kernel 2.6.10-5-386.  I then did a fresh install and ran the various updates (using Ubuntu Update Manager and Synaptic) and this brought it up to kernel 2.6.10-6-386, and now the same thing has happened again.

The error messages I get when trying to boot into Linux are:

[INDENT]EXT3-fs error (device sdb2): ext3_check-descriptors: Inode bitmap for group 384 not in group (block 2147483647)![/INDENT]
[INDENT]EXT3-fs: group descriptors corrupted![/INDENT]
[INDENT]EXT2-fs error (device sdb2): ext2_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)![/INDENT]
[INDENT]Cramfs: wrong magic[/INDENT]
[INDENT]EXT2-fs error (device sdb2): ext2_check_descriptors: Inode bitmap for group 384 not in group (block 2147483647)![/INDENT]
[INDENT]Pivot_root: no such file or directory[/INDENT]
[INDENT]/sbin/init: 428: cannot open dev/console: no such file[/INDENT]
[INDENT]Kernel panic - not syncing: Attempted to kill init![/INDENT]

I don't know if this information matters but I had problems with which file system to use on the partition where Ubuntu was being installed, and used EXT2 file system.

I hope somebody can help as I liked the 'feel' of Linux when it was up and running and would like to keep experimenting with it (perhaps with the latest distribution / 64-bit edition).

Thanks for any help and apologies for the length of this post.

Regards,

Robert

---

### Post by LaSSarD on 2006-01-03
The most recommended filesystems are ext3 and reiserfs. I guess both are great, neither reiserfs nor ext3 gave me errors... To be honest, reiserfs used to produce some strange errors, but I guess the fault was mine :P

anyway, good luck

---

### Post by steve.horsley on 2006-01-04
Using ext3 or reiserfs might help since they are both "journalling" file systems that maintain some crash-recovery data on the disk, but I'm afraid this liiks like it could be a flakey hard drive or controller since it keeps happening.

If you have a live CD, you might be able to run fsck (equiv to chkdisk) on the corrupt partition to fix it.

---

### Post by Tiede on 2006-01-18
I am having the same problem on a brand-new acer laptop. Every 3nd or 3rd boot, it complains about not being able to mount the root partition because of a missing /sbin/init. I then Alt+Ctrl+Del and at reboot, it asks me for the password to run fsck, which I provide, it fixes some inode that had an error, reboots normally 3 or 3 times, then it begins all over again.
I wanna add that my XP partition also complained about a corrupted filesystem, but the corrupted folder was in a directory I use in Ubuntu (My music folder), since I don't run XP unless ubuntu is being a girly girl. (not to offend the ladies :D)
My question now is this: Is there any possibility that the problem might be software related, since my hdd is so new... I bought the laptop the day after christmas (December 26) and the mfg date on the bottom says August 2006!

PS:my XP partition's filesystem is FAT32 and ubuntu's is EXT3

---

