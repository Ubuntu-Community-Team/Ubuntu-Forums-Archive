---
title: "Seemingly serious failure message on boot up"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-17
I'm at a total loss, it just started this morning:
fsck.ext3: no such file or direcrory while trying to open /dev/sda1 dev/sda1: the superblock could not be read or does not describe a correct ext2 file system (and not swap or ufs or something else), the superblock is corrupt and you might try running e2fsck with an alternate superblock e2fsck <68193 device>

---

### Post by kliljedahl on 2007-01-17
OK, what do I do?
$ e2fsck 
Usage: e2fsck [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
                [-I inode_buffer_blocks] [-P process_inode_size]
                [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
                [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks lis

---

