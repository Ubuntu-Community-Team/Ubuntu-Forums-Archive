---
title: "converting root partition to xfs"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by kurian on 2006-09-29
any method for converting root partition to xfs without lossing data and installed kubuntu on it??????

---

### Post by kidders on 2006-10-03
Hi there,

Afaik, the most reliable solution is to copy your filesystem someplace else, reformat the original and copy it back.

---

### Post by pay on 2006-10-03
I was just wondering, what are the advantages over using XFS than reiserFS or EXT3?

---

### Post by K.Mandla on 2006-10-03
There are some folks who think [XFS is much faster]("http://www.ubuntuforums.org/showthread.php?t=246969") than ReiserFS or ext3, or ReiserFS is somehow more reliable than the other two, while ext3 is easier on the processor than either of the others. There's plenty of discussion (with benchmarks) [here]("http://www.debian-administration.org/articles/388") and [here]("http://fsbench.netnation.com/").

From my own experience, ReiserFS is reliable, but taxing on early processors, meaning it slowed things down for me. XFS, on the other hand, is speedy, but I've had file system errors while using it (and never on any others). ext3 is my favorite, but that's mostly because I work primarily with older, slower machines (like 1Ghz or less).

It's something you'll have to try out for yourself and see what works best. As far as converting a file system on the fly, you could start [here]("http://gentoo-wiki.com/HOWTO_Convert_Filesystems"), but that page is fairly advanced. Basically you boot into a live CD, copy everything off, run [convertfs]("http://packages.ubuntu.com/dapper/admin/convertfs"), then copy everything back. I only tried it once, a long time ago.

The easiest and most trustworthy way that I know of to change file systems is ... a reinstall. :(

---

### Post by pay on 2006-10-04
Thanks for the benchmark links K.Mandla. Reading now.

---

### Post by kidders on 2006-10-04
Hi pay,

You may have already gathered this, but XFS is really only intended for servers. K.Mandla's comment is odd, considering XFS is transactionalised, effectively guaranteeing that your filesystem will never find itself in an inconsistent state. It's very RAM-intensive, so you should **never** use it unless you have a UPS.

Other than benchmarking, one important distinction between filesystems is their upper limits on things like file sizes, file*system* sizes, etc. By and large though, Ext3, ReiserFS, etc. easily meet most users' needs in that regard.

---

### Post by sbergman27 on 2006-10-04
> **kidders said:**
> . K.Mandla's comment is odd, considering XFS is transactionalised, effectively guaranteeing that your filesystem will never find itself in an inconsistent state.

Where did you get that idea?

XFS is a *metadata only* journalling filesystem which features delayed allocation and nulls out unwritten data blocks (for security reasons) upon mounting.

Unfortunately, these ingredients combine to make it the most *fragile* of the Linux filesystems in the face of an unclean shutdown.

Yes, I know that in the project's FAQ, they say that this problem was fixed as of 1.1.  Unfortunately, though it may be better, it is *not* fixed, and really can't be, since it is not a bug, per say, but a consequence of the filesystem's design.

XFS is good for streaming large files, but you are only going to see a siginifacnt difference on raid arrays.

Ext3 has 3 journalling modes, all of which offer greater data integrity guarantees than does XFS.

Just to compare the guarantees:

Ext3 (data=journal):  After an unclean shutdown, Fileysystem and
metadata are guaranteed to be consistent.  If the application was told
that a data write occurred, it did. (Slowest writes.)

Ext3 (data=ordered): The default.  After a power outage, the filesystem and metadata
are guaranteed to be consistent.  The file contents are guaranteed not
to be garbage.  BUT, the data might not be the latest written. (Medium
speed writes.)

Ext3 (data=writeback): This is the level that most journaled filesystems
give you.  After an unclean shutdown, filesystem and metadata are
guaranteed to be consistent.  Files can contain garbage. (Fastest
writes.)

XFS: Same as data=writeback for ext3, but due to the way XFS nulls out data blocks, and also delays allocation, data loss is more likely.  Files will not contain garbage, per se, but they may well contain blocks that are completely filled with null characters.

For nonroot filesystems, you can simply specify data=mode in the /etc/fstab.

For root, it is more involved.  The attempt to reset the journalling mode will silently fail.

It can be done, but you have to fiddle with the initrd.

---

### Post by kidders on 2006-10-04
> Unfortunately, these ingredients combine to make it the most *fragile* of the Linux filesystems in the face of an unclean shutdown.

Yep, exactly ... that's why a UPS is important when using XFS.

---

### Post by sbergman27 on 2006-10-04
> **kidders said:**
> Yep, exactly ... that's why a UPS is important when using XFS.

I often hear that.  And I always wonder, if having a UPS is good enough protection from potential severe data loss, then why wouldn't it be good enough to protect from a long fsck process?

i.e., if a UPS is adequate protection, then why aren't we running the blazingly fast ext2, which is likely faster than *any* of the journalled filesystems?

The answer is, of course, that power failure is only one thing that can bring a machine down uncleanly.

Jounalling filesystems were written for a reason.

---

### Post by kidders on 2006-10-04
Hehe... a discussion for another day, I think!

---

