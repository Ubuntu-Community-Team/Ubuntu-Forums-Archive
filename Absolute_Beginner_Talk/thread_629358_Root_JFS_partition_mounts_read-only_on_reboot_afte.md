---
title: "Root JFS partition mounts read-only on reboot after crash - system unusable!"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by JPorter on 2007-12-02
Greetings all, I hope someone can help me.  I've been using Gutsy with JFS partitions since the release with no problems.  

Yesterday I experienced an unusual system hang (freeze) and after reboot, x failed to start.  When booting in recovery mode, nothing was able to load due to my root filesystem being suddenly "read-only".

The only thing I could find on the web was this:  [http://bugs.archlinux.org/task/537](http://bugs.archlinux.org/task/537)   I'm not certain that the issue is related.


Can anyone help?  Does anyone know how to fix this one?  I can't use a LiveCD since I have an ATI video chip in the laptop, so I'll have to use an AlternateCD to get a command line.

Thanks for any help you can provide!


-JPorter

---

### Post by PmDematagoda on 2007-12-02
Did you try:-

```
reboot
```

I know it sounds crazy, but it did fix up my problem when I faced an error on my system which ran on a JFS file system an error I believe which was quite similar to yours.

---

### Post by JPorter on 2007-12-02
> **PmDematagoda said:**
> Did you try:-

```
reboot
```

I know it sounds crazy, but it did fix up my problem when I faced an error on my system which ran on a JFS file system an error I believe which was quite similar to yours.

I just tried it.  No dice.


This may be related to:  [http://www.nabble.com/Corruption-in-JFS-t4630872.html](http://www.nabble.com/Corruption-in-JFS-t4630872.html)

Any thoughts? 


I'm torrenting the alternate CD on another box so I can try fsck.jfs from that... not sure how to proceed.

---

### Post by PmDematagoda on 2007-12-02
If it is possible, could you please post the exact error messages you get when Ubuntu is trying to mount the Root File System?

---

### Post by JPorter on 2007-12-02
> **PmDematagoda said:**
> If it is possible, could you please post the exact error messages you get when Ubuntu is trying to mount the Root File System?

How can I capture the startup log?  The root partition is read-only.

---

### Post by PmDematagoda on 2007-12-02
No, I was talking about the errors you get on the screen.

---

### Post by JPorter on 2007-12-02
I did notice this advice in more than one place...
> Sometimes /etc/mtab does not represent the contents of /proc/mounts. 

Relevant?  Do I need to edit fstab or mtab?





I also tried booting into Windows and shutting down again, hoping it might just be an issue where my dual boot install of XP failed to unmount a drive properly... No dice with that either.

---

### Post by PmDematagoda on 2007-12-02
I don't think that it is relevant since mtab is the record of the volumes and how they are mounted.

But fstab may have something since it is what governs how the root file system is mounted on the start of Ubuntu.

---

### Post by JPorter on 2007-12-02
> **PmDematagoda said:**
> No, I was talking about the errors you get on the screen.


Examples are things like:

```
 * Starting NFS common utilities                   [ OK]
rm: cannot remove '.X0-lock': Read-only file system
/etc/init.d/bootclean:  143: cannot create /tmp/.clean: Read-only file system
 * Setting up console font and keymap....                 [ OK]
chown: changing ownership of '/tmp/.X11-unix': Read-only file system
rm: cannot remove '/var/log//dmesg.4.gz': Read-only file system
mv: cannot move '/var/log//dmesg.3.gz' to '/var/log//dmesg.4.gz': Read-only file system
mv: cannot move '/var/log//dmesg.2.gz' to '/var/log//dmesg.3.gz': Read-only file system
mv: cannot move '/var/log//dmesg.1.gz' to '/var/log//dmesg.2.gz': Read-only file system
gzip: /var/log//dmesg.0.gz: Read-only file system
mv: cannot stat '/var/log//dmesg.0.gz': No such file or directory
touch: cannot touch '/var/log/dmesg.new': Read-only file system
chown: cannot access '/var/log/dmesg.new': No such file or directory
chmod: cannot access '/var/log/dmesg.new': No such file or directory
ln: cannot remove '/var/log//dmesg.0': Read-only file system
Error hardlinking /var/log/dmesg to /var/log//dmesg.0
/etc/rcS.d/S80bootmisc.sh: 81: cannot create /var/log/dmesg: Read-only file system
chgrp: changing group of '/var/log/dmesg': Read-only file system
rm: cannot remove '/var/lib/urandom/random-seed': Read-only file system

```
Then I get the standard root prompt.

---

### Post by PmDematagoda on 2007-12-02
Try doing:-

```
fsck
```

---

### Post by spydon on 2007-12-02
I had a similar problem before and I tried this from a live cd and my filesystem wasn't read only anymore.

```

sudo e2fsck -f -y -v /dev/hda2

```
and then
```

sudo e2fsck -C0 -f -p -v /dev/hda2

```

Do it from a live cd.

I think it only works on ext filesystems :/

---

### Post by JPorter on 2007-12-02
> **PmDematagoda said:**
> I don't think that it is relevant since mtab is the record of the volumes and how they are mounted.

But fstab may have something since it is what governs how the root file system is mounted on the start of Ubuntu.

The reason why I asked is that in the first link I posted above, someone suggested deleting mtab and rebooting.  I'm not sure if that's prudent or not.

Torrent is almost done, I'll boot it up with the alternate CD.  Any suggestions on how I should proceed with fsck, etc?


Thanks for your help, by the way!  It's greatly appreciated!

---

### Post by JPorter on 2007-12-02
> **PmDematagoda said:**
> Try doing:-

```
fsck
```

Output from fsck (on recovery console):
```
fsck 1.40.2 (12-Jul-2007)
```

fsck.jfs wants a target... not sure if I should do this with the file system mounted.  Maybe from the Alternate CD?

---

### Post by PmDematagoda on 2007-12-02
From what I have heard, fsck is not damaging to read-only file systems, but you better wait for confirmation by someone else.

---

### Post by JPorter on 2007-12-02
Well, this is frustrating.

How do I boot to a command line using a 7.10 Alternate CD?

---

### Post by JPorter on 2007-12-02
I fixed it.  What a freaking stupid error, nobody should have to do this.


All it took was a 
```
sudo fsck.jfs -a -f /dev/sda3
```

It repaired the filesystem and everything worked normally on reboot.

Now, why isn't the system set up to fsck automatically instead of trying to boot the root filesystem with it set to read-only?  Isn't it obvious that that won't work, ever?


I'm just glad I didn't totally lose all of my data.

---

### Post by JPorter on 2007-12-02
Ok, the plot thickens.  Apparently there is still filesystem corruption.

With the system back up and running, executing **sudo fsck.jfs -n /dev/sda3** at console delivers these results:

```
fsck.jfs version 1.1.11, 05-Jun-2006
processing started: 12/2/2007 13.26.4
Filesystem is currently mounted.
WARNING: Checking a mounted filesystem does not produce dependable results.
The current device is:  /dev/sda3
Block size in bytes:  4096
Filesystem size in blocks:  8353800
**Phase 1 - Check Blocks, Files/Directories, and  Directory Entries
**Phase 2 - Count links
**Phase 3 - Duplicate Block Rescan and Directory Connectedness
**Phase 4 - Report Problems
**Phase 5 - Check Connectivity
**Phase 6 - Perform Approved Corrections
**Phase 7 - Verify File/Directory Allocation Maps
Errors detected in the Fileset File/Directory Allocation Map control information. (F)
**Phase 8 - Verify Disk Allocation Maps
Incorrect data detected in disk allocation structures.
Incorrect data detected in disk allocation control structures.
 33415200 kilobytes total disk space.
    40234 kilobytes in 12461 directories.
 20240920 kilobytes in 94873 user files.
        0 kilobytes in extended attributes
   137062 kilobytes reserved for system use.
 13077452 kilobytes are available for use.
File system checked READ ONLY.
Filesystem is dirty.
Filesystem is dirty but is marked clean.  In its present state,
the results of accessing /dev/sda3 (except by this utility) are undefined.
```

How do I get to a command line without mounting the root filesystem?  I didn't see anything useful on the Alternate CD.  I expected a recovery console option there but didn't see one.

Thanks for your help in advance!

---

### Post by JPorter on 2007-12-03
Bump.

---

### Post by spydon on 2007-12-07
Have you checked if you have badblocks on your harddrive?

```
badblocks /dev/hda
``` or something like that...

Try to download another cd like Trinity Rescue Kit maybe.

---

