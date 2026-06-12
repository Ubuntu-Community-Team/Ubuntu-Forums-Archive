---
title: "fsck failed"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Aberrix on 2007-05-11
So the other day I had to power go out and my system was hard shutdown, since then one of my disks has been giving me errors...

here is the output of my /etc/fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
/dev/hda2       /home           ext3    defaults,usrquota,grpquota        0       2
/dev/hda3       /var            ext3    defaults,usrquota,grpquota        0       2
/dev/hda4       none            swap    sw              0       0
/dev/hdc1       /media/storage  ext3    defaults        0       2
/dev/hdd1       /media/share    ext3    defaults        0       2
```

and fdisk -l
```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1216     9767488+  83  Linux
/dev/hda2            1217        3648    19535040   83  Linux
/dev/hda3            3649        9727    48829567+  83  Linux
/dev/hda4            9728        9964     1903702+  82  Linux swap / Solaris

Disk /dev/hdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       36483   293049666   83  Linux
```

I am having a problem with /dev/hdd1, I unmounted it and tried to run a fsck on it but now I get the following error:

```

fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/hdd1
Could this be a zero-length partition?
```

Now if I try to mount it I get the following error;
```
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

could someone please provide some advice as to where to go from here? I'd really like to be able to get at my data on this disk. thanks in advance.

---

### Post by Aberrix on 2007-05-11
bump, this forum moves too fast :)

---

### Post by taurus on 2007-05-11
First, I would edit /etc/fstab and comment out the entry for /dev/hdd1 by placing a # in front of it for now.  Then, reboot your machine and go into the BIOS to see if the BIOS is happy with /dev/hdd1 (capacity).  Boot into Ubuntu and see what happens with this command again.

```
sudo fdisk -l
```
Otherwise, fsck it from a terminal with

```
sudo fsck /dev/hdd1
```

---

### Post by dstew on 2007-05-11
Your dev/hdd1 superblock may be corrupted. If so, you need to try to do e2fsck using an alternative superblock.  Try **e2fsck -b 8193 /dev/hdd1**. This is for 1K block size. See **man fsck** for more details.

---

### Post by Aberrix on 2007-05-11
> **dstew said:**
> Your dev/hdd1 superblock may be corrupted. If so, you need to try to do e2fsck using an alternative superblock.  Try **e2fsck -b 8193 /dev/hdd1**. This is for 1K block size. See **man fsck** for more details.

here are the results...

```
e2fsck 1.38 (30-Jun-2005)
e2fsck: Bad magic number in super-block while trying to open /dev/hdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

---

### Post by dstew on 2007-05-11
It might be that your file system is using a different block size than 1K, so the block at 8193 is not a superblock. You can try the same command using the numbers 16384 (for 2k blocks) and 32768 (for 4K blocks). You are, unfortunately, fishing for good superblock back-ups. Often there are backup superblocks at other locations. There are other ways to try to find them. Here is a post that shows one way of doing it:

[http://edseek.com/archives/2004/02/25/ext3-filesystem-bad-superblock-recovery/](http://edseek.com/archives/2004/02/25/ext3-filesystem-bad-superblock-recovery/)

---

### Post by Aberrix on 2007-05-14
I ran a 'sudo mke2fs -n /dev/hdd1' which from what I understand should tell me where the backup superblocks are stored, here is what I got back;

```
mke2fs 1.38 (30-Jun-2005)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30539776 inodes, 61049000 blocks
3052450 blocks (5.00%) reserved for the super user
First data block=0
1864 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424, 20480000, 23887872
```

I then ran a 'sudo e2fsck -b 32768 /dev/hdd1' except I keep getting stuff like this;

```
Error reading block 328030 (Attempt to read block from filesystem resulted in short read) while doing inode scan.  Ignore error<y>?

Force rewrite<y>? 
```

should I just answer yes to all these? or should I try another backup superblock? advice? thanks in advance.

---

### Post by Dr Small on 2007-05-14
So when is this happening?
At bootup or what?

I had fsck stop on me awhile back, and I had to run:
```
fsck /dev/sda3
```
to get mine working again ;)

Dr Small

---

### Post by Aberrix on 2007-05-14
> **Dr Small said:**
> So when is this happening?
At bootup or what?

I had fsck stop on me awhile back, and I had to run:
```
fsck /dev/sda3
```
to get mine working again ;)

Dr Small

read the whole thread before responding. :)

---

### Post by Aberrix on 2007-05-14
bump?

---

### Post by dstew on 2007-05-14
Let me see if I understand correctly what you are doing now. The command```
sudo mke2fs -n /dev/hdd1
```was to re-format the hard disk, so you have given up trying to recover your files. Next, you checked your new file system using```
sudo e2fsck -b 32768 /dev/hdd1
```When this command ran, it found a bad block at 328030, and asked permission to fix it.

I think you should give it permission to fix it (rewrite it). It looks like the drive is having some issues.

EDIT: I see now the -n switch that prevents the filesystem from being created. So, now you have a good idea where the superblock backups would be on your system. I think the e2fsck worked, at least it did not complain that the superblock you used was bad.

---

### Post by Aberrix on 2007-05-14
> **dstew said:**
> Let me see if I understand correctly what you are doing now. The command```
sudo mke2fs -n /dev/hdd1
```was to re-format the hard disk, so you have given up trying to recover your files.

no, that command was simply to show the location of the super block backups.

from the man;
```
-n     causes  mke2fs  to not actually create a filesystem, but display
              what it would do if it were to create a filesystem.  This can be
              used  to  determine the location of the backup superblocks for a
              particular filesystem, so long as  the  mke2fs  parameters  that
              were  passed when the filesystem was originally created are used
              again.  (With the -n option added, of course!)
```

---

### Post by Aberrix on 2007-05-14
during the 'e2fsck' is there a way to automatically answer 'yes' to all the prompts?

---

### Post by dstew on 2007-05-14
Yeah, I saw it (see EDIT in post).
Looking around at forum posts, it looks like e2fsck is trying to repair the disk. The option -c is one idea, to do the badblocks test. Some people have gotten their disks back by entering yes and yes to the questions, and rebooting.

---

### Post by psusi on 2007-05-14
Check the output of dmesg for any interesting error messages.  And add -y to the fsck command to say yes to all of the "fix this?" questions.  

And yea, running badblocks on the partition isn't a bad idea either.

---

