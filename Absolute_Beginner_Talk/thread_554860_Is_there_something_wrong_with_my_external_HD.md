---
title: "Is there something wrong with my external HD"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by emband on 2007-09-19
Hello I think it is something wrong with my external HD a MyBook 500 GB. I recently  had some problems moving files from this external HD to another external HD.

I get a mv: input/output error or something like that when I try to move some files.
And some avi files will not start to play in VLC, this has worked perfectly until today.

I did a ls -la and discovered that my music directory and backup directory has got some ? 

What is happening, is my External HD starting to die? Is there something I can do to check it or fix it without loosing my data?  My disk is formated in ext3


anders@anders-dell:/media/disk$ ls -la
total 5638916
drwxr-xrwx 22 root   root         4096 2007-09-19 19:18 .
drwxr-xr-x  8 root   root         4096 2007-09-19 19:25 ..
drwxr-xr-x  5 anders anders       4096 2007-09-19 18:35 audiobooks
?---------  ? ?      ?               ?                ? backup
drwxr-xr-x  2 anders anders       4096 2007-06-14 16:42 battlefield_patch
drwxr-x---  7 anders admin        4096 2007-08-30 18:25 div
drwx------  2 root   root        16384 2007-04-10 23:53 lost+found
drwxr-xr-x 51 anders anders       4096 2007-08-22 23:05 movies
?---------  ? ?      ?               ?                ? Music
drwxr-xr-x  2 root   root         4096 2007-05-01 18:18 rescue
drwxr-xr-x 23 anders anders       4096 2007-09-19 19:39 series
-rw-r--rw-  1 root   root         6144 2007-06-14 16:58 Thumbs.db
drwx------  2 anders anders      28672 2007-07-21 11:20 .Trash-anders

----
Anders

---

### Post by alienexplorers on 2007-09-19
you could try running fsck on the drive to check the file system.
Here is some info on fsck.
> terminator@terminator-desktop:~$ fsck --help
fsck 1.38 (30-Jun-2005)
fsck.ext3: invalid option -- h
Usage: fsck.ext3 [-panyrcdfvstDFSV] [-b superblock] [-B blocksize]
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
 -L bad_blocks_file   Set badblocks list


---

### Post by emband on 2007-09-19
hello i tried fsck /mediai/disk and got this:

anders@anders-dell:~$ fsck /media/disk/
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: Is a directory while trying to open /media/disk/

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


i don't know if I have done it correctly or not.

---

