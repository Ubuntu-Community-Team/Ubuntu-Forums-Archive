---
title: "Slow system after restoring with Norton Ghost"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-01-23
Hi,

I created an image of my Ubuntu system a while ago using Norton Ghost 2003. NG2003 is supposed to handle ext2/ext3 partition but it's only recently that I saw NG could screw up ext3 partitions! Well this is probably what happened: after restoring my system, it boots correctly but seems a bit slow. On the second boot, fsck is ran and find a Inode error (fixed) but then the system stop and is restarted because fsck found errors (fsck died with exit status 3). Then I can reboot correctly but the whole system feels slower than before, the desktop takes longer to appear etc...

I will never use Ghost again with Linux but is there anything I can do to fix the filesystem to restore its speed?? For now I'm trying to copy the system in a TAR, format the filesystem and copy the system back on the partition. Don't know if this will improve speed. If you have any other suggestion, please let me know.

Thanks

---

### Post by smoker on 2007-01-23
i think if you can back up at least your essential data, then i would opt for a reinstall. you will probably never be able to get your system back to the way it was, and even if so, what unforseen errors may lie ahead!

---

### Post by kilou on 2007-01-23
But since I can boot and access all files (at least this is what I think) then wouldn't it be possible to backup all the system in a tar file, moving the archive on an external drive or partition and reformat the Ext3 filesystem with GParted to restore all things??? My understanding is that Ghost creates an image of the whole partition, including the underlying filesystem and this is where the problem lies: it is not able to rebuild the filesystem properly (I've read that Ghost 2003 thinks Ext3 is a damaged Ext2 filesystem so it is likely that the "only" problem I have is because of a broken journalling maybe). Since this doesn't prevent me from accessing all files, why not just rebuild the Ext3 filesystem by reformatting the partition and moving back all the data from the tarball???? A reformat would rebuilt the Ext3 filesystem correctly then..and moving the files from the archive would no reinsert the problem, right?

---

### Post by ardchoille42 on 2007-01-23
If you do opt for a re-install, I would recommend you download and burn [this]("http://www.sysresccd.org/Main_Page") LiveCD. It comes with an app called [PartImage]("http://www.partimage.org/Main_Page"), among a lot of other nice tools, which is a like a Nortan Ghost clone for Linux and is very easy to use. I have been using it for a while and it is fast. Cloning my 6Gb partition takes about 9 minutes and restoring from the image takes less time.

---

### Post by kilou on 2007-01-23
Yes I've already tried this system rescue Live CD along with PartImage. Those are nice but I personally prefer the tar archive because it's more convenient since you can backup/restore a system while using it as well as exclude things you don't want to backup. 

So would restoring from a tar archive also restore a problematic Ext3 filesystem if I first reformat it correctly and then move the file back???

---

