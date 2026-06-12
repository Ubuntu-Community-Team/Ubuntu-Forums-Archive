---
title: "No ISO9960 support in 10.04 PowerPC"
date: 2010-06-19
forum: Apple Hardware Users
---

### Post by JoeMac42 on 2010-06-19
I have been troubleshooting another issue when I noticed I couldn't mount certain types of CD media from the command line.  when I tried:
    cat /proc/filesystems
the output returned:

nodev	sysfs
nodev	rootfs
nodev	bdev
nodev	proc
nodev	cgroup
nodev	cpuset
nodev	tmpfs
nodev	devtmpfs
nodev	debugfs
nodev	securityfs
nodev	sockfs
nodev	pipefs
nodev	anon_inodefs
nodev	inotifyfs
nodev	devpts
	ext3
	ext2
	ext4
nodev	ramfs
nodev	fuse
	fuseblk
nodev	fusectl
nodev	mqueue
nodev	binfmt_misc
	hfsplus
	udf

Shouldn't this report an available iso9660 filesystem?

---

