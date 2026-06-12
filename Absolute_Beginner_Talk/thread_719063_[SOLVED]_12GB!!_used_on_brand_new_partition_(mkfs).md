---
title: "[SOLVED] 12GB!! used on brand new partition (mkfs)"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by alphaniner on 2008-03-08
I'm running the Ubuntu 7.10 Live CD and I used mkfs.ext3 to reformat an existing ext3 partition.  After formatting I mounted and opened it through Nautilus, right clicked on a blank area in the window, and chose 'Properties'.  This brought up the window with the little pie chart illustrating used/unused space.  The 'Used Space' shows up as 12.1 GB.  The 'Total Capacity' of the partition says 234.3 GB.  Can someone please explain to me what is taking up those 12 GB?

I also have a somewhat related question about mkfs.  It requires you to enter the number of blocks to use, so I just used the total reported by fdisk.  Would there be any reason to enter a smaller number of blocks, or is this information only necessary because mkfs cannot determine the number of blocks on its own?  Thanks.

a9

---

### Post by Inxsible on 2008-03-08
> **alphaniner said:**
> I'm running the Ubuntu 7.10 Live CD and I used mkfs.ext3 to reformat an existing ext3 partition.  After formatting I mounted and opened it through Nautilus, right clicked on a blank area in the window, and chose 'Properties'.  This brought up the window with the little pie chart illustrating used/unused space.  The 'Used Space' shows up as 12.1 GB.  The 'Total Capacity' of the partition says 234.3 GB.  Can someone please explain to me what is taking up those 12 GB?

I also have a somewhat related question about mkfs.  It requires you to enter the number of blocks to use, so I just used the total reported by fdisk.  Would there be any reason to enter a smaller number of blocks, or is this information only necessary because mkfs cannot determine the number of blocks on its own?  Thanks.

a9I am not sure if this is just a hard drive or a drive in your laptop computer shipped by your vendor? Computer drives do have additional partitions for recovery. Maybe the 12 gigs are a different partition.

I could be wrong though !

---

### Post by alphaniner on 2008-03-08
> **Inxsible said:**
> I am not sure if this is just a hard drive or a drive in your laptop computer shipped by your vendor? Computer drives do have additional partitions for recovery. Maybe the 12 gigs are a different partition.

I could be wrong though !

No, this is a specific partition (/dev/sdb2 mounted as /media/disk) on one hard drive.  Here is a screenshot of the windows.  The lost+found folder is the only thing on the disk, and it is (apparently) empty .

[IMG]http://i145.photobucket.com/albums/r208/AshFooYoung/f.png[/IMG]

---

### Post by yabbadabbadont on 2008-03-08
It is most likely the journal.  I believe that, by default, the journal takes up 5% of the total size of the filesystem.  I'm not talking about the 5% that is reserved for use by root, but the actual size of the journal used by the ext3 filesystem.  I don't know if it can be changed.

Edit: Especially since 12.1 is 5% of 234.3

---

### Post by yabbadabbadont on 2008-03-08
OK, after looking around a bit, it seems that you can adjust the journal parameters using the tune2fs command.  From the manpage:
```
       -J journal-options
              Override  the  default  ext3  journal  parameters. Journal options are comma separated, and may take an argument using the equals
              ('=')  sign.  The following journal options are supported:

                   size=journal-size
                          Create a journal stored in the filesystem of size journal-size megabytes.   The size of the journal must be at  least
                          1024  filesystem blocks (i.e., 1MB if using 1k blocks, 4MB if using 4k blocks, etc.)  and may be no more than 102,400
                          filesystem blocks.  There must be enough free space in the filesystem to create a journal of that size.

                   device=external-journal
                          Attach the filesystem to the journal block device located on external-journal.  The external journal must  have  been
                          already created using the command

                          mke2fs -O journal_dev external-journal

                          Note  that  external-journal  must  be  formatted with the same block size as filesystems which will be using it.  In
                          addition, while there is support for attaching multiple filesystems to a single external journal,  the  Linux  kernel
                          and e2fsck(8) do not currently support shared external journals yet.

                          Instead  of  specifying  a  device  name  directly,  external-journal  can also be specified by either LABEL=label or
                          UUID=UUID to locate the external journal by either the volume label or UUID stored in  the  ext2  superblock  at  the
                          start  of  the journal.  Use dumpe2fs(8) to display a journal device's volume label and UUID.  See also the -L option
                          of tune2fs(8).

              Only one of the size or device options can be given for a filesystem.

```
Note that it says that the journal must be *at least* 1024 filesystem blocks.  So, depending upon your block size, you may be stuck.

---

### Post by alphaniner on 2008-03-08
> **yabbadabbadont said:**
> It is most likely the journal.  I believe that, by default, the journal takes up 5% of the total size of the filesystem.  I'm not talking about the 5% that is reserved for use by root, but the actual size of the journal used by the ext3 filesystem.  I don't know if it can be changed.

Edit: Especially since 12.1 is 5% of 234.3

I noticed that too, so I googled 'ext3 5%' and 'ext3 5 percent' and didn't find anything enlightening. Plus it is not exactly 5% (would be 11.715) so I wrote it off as coincidence.  I used mkfs to reformat as ext2 but then the partition couldn't be mounted, so I'm trying parted.  Hopefully it will work and I will be able to see if there is any difference.  I might also try to reformat another partition and see if there is a similar percentage of used space.  In the meantime, I'm still open for advice and suggestions.  Thanks.

a9

edit:

> Note that it says that the journal must be at least 1024 filesystem blocks. So, depending upon your block size, you may be stuck.

Well, I feel dum.  After reading your post I went back and tried to figure out how many blocks there were and how much space 1024 blocks would be.  Not much, apparently.  However, I looked more closely at the output of mkfs and it turns out it actually *is* just the superuser reserved space:

```
62412525 blocks
3120626 blocks (5.00%) reserved for the super user
```

Sorry for wasting your time, yabbadabbadont.  Gonna mark this thread as solved.

---

### Post by yabbadabbadont on 2008-03-08
OK, yet more digging.  I take back what I said about the journal.  I think that it is most likely the space that is reserved by default for root only.  (which is ~5%)  When you create the filesystem, be sure to use the "-m 0" option to set the root reserved space to zero percent.

---

### Post by alphaniner on 2008-03-08
> **yabbadabbadont said:**
> OK, yet more digging.  I take back what I said about the journal.  I think that it is most likely the space that is reserved by default for root only.  (which is ~5%)  When you create the filesystem, be sure to use the "-m 0" option to set the root reserved space to zero percent.

Yuppers, the greedy (nonexistent) root user is in fact the culprit.  Is the '-m 0' tag for mkfs?  Beause I didn't see it the man page.

---

### Post by yabbadabbadont on 2008-03-08
```
man mke2fs
```
Since you are creating a ext3 filesystem.  mkfs -t ext3 just calls mke2fs.

---

### Post by alphaniner on 2008-03-08
I thought I had read that mkfs called mkfs.ext3.  Oh well.  Thanks again for the help, that was above-and-beyond.

---

### Post by yabbadabbadont on 2008-03-09
> **alphaniner said:**
> I thought I had read that mkfs called mkfs.ext3.  Oh well.  Thanks again for the help, that was above-and-beyond.

Technically, it does.  However, mkfs.ext3 is just a symbolic link to mkef2s...  ;)

---

