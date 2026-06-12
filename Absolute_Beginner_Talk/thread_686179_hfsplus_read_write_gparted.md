---
title: "hfsplus read write gparted"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by lance bermudez on 2008-02-03
using kernel 2.6.23 i have the modules hfs and hfsplus that let me read/write to a  hard drive formated on a power mac g3 running os 9.2.2. the linux is installed on a pc computer. i was told looking around this forum that i need to install the diskdev_cmds-332.14 and ists patch to format a hard drive in linux using hfsplus from gparted they do not work i get an error and it only makes the fsck.hfs but not the mkfs.hfsplus. in gparted i have the format hfs and hfsplus listed but can only use the hfs becuse the hfsplus is grayed out to ungray it i was told i need to get the diskdev_cmds-332.14 to work. i have build-essential gcc gcc-3.3 gcc-3.4 gcc-4.1 and the cpp that match the gcc. i have tried using the make -f Makefile.lnx command with and with out the sudo and i still get the error. is there a .deb out their for diskdev_cmds? please help me out

---

### Post by spiderbatdad on 2008-02-03
you should be doing this as root...so sudo is not needed.

```
sudo bash
cd /usr/src
mkdir hfsplus_support
wget http://darwinsource.opendarwin.org/tarballs/apsl/diskdev_cmds-332.14.tar.gz
wget http://www.ecl.udel.edu/~mcgee/diskdev_cmds/diskdev_cmds-332.14.patch.bz2
tar zxf diskdev_cmds-332.14.tar.gz
bunzip2 -c diskdev_cmds-332.14.patch.bz2 | patch -p0
cd diskdev_cmds-332.14
make -f Makefile.lnx
cp fsck_hfs.tproj/fsck_hfs /sbin/fsck.hfsplus
cd /sbin
ln -s fsck.hfsplus fsck.hfs
```
There does not appear to be a deb package. Perhaps you could post the error you are receiving? Also what version are you running?

---

### Post by lance bermudez on 2008-02-03
below is the output i get

lance@linuxwin2k:~/Programs/hfsplus_support/diskdev_cmds-332.14$ make -f Makefile.lnx
for d in newfs_hfs.tproj fsck_hfs.tproj; do make -C $d -f Makefile.lnx all; done
make[1]: Entering directory `/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/newfs_hfs.tproj'
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o hfs_endian.o hfs_endian.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o makehfs.o makehfs.c
makehfs.c:54:25: error: openssl/sha.h: No such file or directory
makehfs.c: In function â€˜InitMDBâ€™:
makehfs.c:571: warning: pointer targets in passing argument 1 of â€˜strlenâ€™ differ in signedness
makehfs.c: In function â€˜GenerateVolumeUUIDâ€™:
makehfs.c:2058: error: â€˜SHA_CTXâ€™ undeclared (first use in this function)
makehfs.c:2058: error: (Each undeclared identifier is reported only once
makehfs.c:2058: error: for each function it appears in.)
makehfs.c:2058: error: expected â€˜;â€™ before â€˜contextâ€™
makehfs.c:2074: warning: implicit declaration of function â€˜SHA1_Initâ€™
makehfs.c:2074: error: â€˜contextâ€™ undeclared (first use in this function)
makehfs.c:2080: warning: implicit declaration of function â€˜SHA1_Updateâ€™
makehfs.c:2141: warning: implicit declaration of function â€˜SHA1_Finalâ€™
make[1]: *** [makehfs.o] Error 1
make[1]: Leaving directory `/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/newfs_hfs.tproj'
make[1]: Entering directory `/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/fsck_hfs.tproj'
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o fsck_hfs.o fsck_hfs.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o strings.o strings.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o utilities.o utilities.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o cache.o cache.c
make -C dfalib -f Makefile.lnx libdfa.a
make[2]: Entering directory `/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/fsck_hfs.tproj/dfalib'
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o hfs_endian.o hfs_endian.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BlockCache.o BlockCache.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTree.o BTree.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTreeAllocate.o BTreeAllocate.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTreeMiscOps.o BTreeMiscOps.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTreeNodeOps.o BTreeNodeOps.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTreeScanner.o BTreeScanner.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTreeTreeOps.o BTreeTreeOps.c
BTreeTreeOps.c: In function â€˜InsertLevelâ€™:
BTreeTreeOps.c:436: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o CatalogCheck.o CatalogCheck.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o HardLinkCheck.o HardLinkCheck.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SBTree.o SBTree.c
SBTree.c: In function â€˜SearchBTreeRecordâ€™:
SBTree.c:96: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
SBTree.c: In function â€˜GetBTreeRecordâ€™:
SBTree.c:193: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
SBTree.c: In function â€˜InsertBTreeRecordâ€™:
SBTree.c:225: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
SBTree.c: In function â€˜ReplaceBTreeRecordâ€™:
SBTree.c:287: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
SBTree.c: In function â€˜SetEndOfForkProcâ€™:
SBTree.c:326: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
SBTree.c: In function â€˜CheckBTreeKeyâ€™:
SBTree.c:424: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SControl.o SControl.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SVerify1.o SVerify1.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SVerify2.o SVerify2.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SRepair.o SRepair.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SRebuildCatalogBTree.o SRebuildCatalogBTree.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SUtils.o SUtils.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SKeyCompare.o SKeyCompare.c
SKeyCompare.c: In function â€˜CompareAttributeKeysâ€™:
SKeyCompare.c:475: warning: initialization discards qualifiers from pointer target type
SKeyCompare.c:476: warning: initialization discards qualifiers from pointer target type
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SDevice.o SDevice.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SExtents.o SExtents.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SAllocate.o SAllocate.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SCatalog.o SCatalog.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SStubs.o SStubs.c
gcc -g3 -Wall -I/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o VolumeBitmapCheck.o VolumeBitmapCheck.c
ar rc libdfa.a hfs_endian.o BlockCache.o BTree.o BTreeAllocate.o BTreeMiscOps.o BTreeNodeOps.o BTreeScanner.o BTreeTreeOps.o CatalogCheck.o HardLinkCheck.o SBTree.o SControl.o SVerify1.o SVerify2.o SRepair.o SRebuildCatalogBTree.o SUtils.o SKeyCompare.o SDevice.o SExtents.o SAllocate.o SCatalog.o SStubs.o VolumeBitmapCheck.o
make[2]: Leaving directory `/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/fsck_hfs.tproj/dfalib'
gcc   fsck_hfs.o strings.o utilities.o cache.o dfalib/libdfa.a   -o fsck_hfs
make[1]: Leaving directory `/home/lance/Programs/hfsplus_support/diskdev_cmds-332.14/fsck_hfs.tproj'
lance@linuxwin2k:~/Programs/hfsplus_support/diskdev_cmds-332.14$

---

### Post by spiderbatdad on 2008-02-03
you are not root! you should be following the commands from the previous post one by one ;)

---

### Post by lance bermudez on 2008-02-03
i get the same output even when i use sudo su

---

### Post by spiderbatdad on 2008-02-03
have you read this how to from start to finish?[http://sudan.ubuntuforums.com/showthread.php?t=392287&highlight=hfsplus](http://sudan.ubuntuforums.com/showthread.php?t=392287&highlight=hfsplus)

---

### Post by lance bermudez on 2008-02-03
this time i did the build from /usr/src/hfsplus_support and used sudo bash and i still get the fsck_hfs in the fsck_hfs.tproj folder but not the newfs_hfs in the newfs_hfs.tprojfolder so what im i still doing wrong because im still getting the error? below is my output. i will also attach the files im using for the build

root@linuxwin2k:~/test# cd /usr/src/hfsplus_support
root@linuxwin2k:/usr/src/hfsplus_support# ls
diskdev_cmds-332.14.patch.bz2  diskdev_cmds-332.14.tar.gz
root@linuxwin2k:/usr/src/hfsplus_support# tar -zxf diskdev_cmds-332.14.tar.gz
root@linuxwin2k:/usr/src/hfsplus_support# ls
diskdev_cmds-332.14  diskdev_cmds-332.14.patch.bz2  diskdev_cmds-332.14.tar.gz
root@linuxwin2k:/usr/src/hfsplus_support# bunzip2 -c diskdev_cmds-332.14.patch.bz2 | patch -p0
patching file diskdev_cmds-332.14/Makefile.lnx
patching file diskdev_cmds-332.14/diskdev_cmds-332.11/Makefile.lnx
patching file diskdev_cmds-332.14/diskdev_cmds-332.11/fsck_hfs.tproj/Makefile.lnx
patching file diskdev_cmds-332.14/fsck_hfs.tproj/Makefile.lnx
patching file diskdev_cmds-332.14/fsck_hfs.tproj/cache.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/BTree.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/BTreeTreeOps.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/BlockCache.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/Makefile.lnx
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SBTree.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SControl.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SDevice.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SKeyCompare.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SRepair.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SRuntime.h
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SUtils.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SVerify2.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/SVerify2.c.orig
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/Scavenger.h
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/Scavenger.h.orig
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/hfs_endian.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/dfalib/hfs_endian.h
patching file diskdev_cmds-332.14/fsck_hfs.tproj/fsck_hfs.c
patching file diskdev_cmds-332.14/fsck_hfs.tproj/utilities.c
patching file diskdev_cmds-332.14/include/bitstring.h
patching file diskdev_cmds-332.14/include/hfs/hfs_format.h
patching file diskdev_cmds-332.14/include/hfs/hfs_mount.h
patching file diskdev_cmds-332.14/include/missing.h
patching file diskdev_cmds-332.14/include/sys/appleapiopts.h
patching file diskdev_cmds-332.14/newfs_hfs.tproj/Makefile.lnx
patching file diskdev_cmds-332.14/newfs_hfs.tproj/hfs_endian.c
patching file diskdev_cmds-332.14/newfs_hfs.tproj/hfs_endian.h
patching file diskdev_cmds-332.14/newfs_hfs.tproj/makehfs.c
patching file diskdev_cmds-332.14/newfs_hfs.tproj/newfs_hfs.c
patching file diskdev_cmds-332.14/newfs_hfs.tproj/newfs_hfs.h
root@linuxwin2k:/usr/src/hfsplus_support# cd diskdev_cmds-332.14
root@linuxwin2k:/usr/src/hfsplus_support/diskdev_cmds-332.14# make -f Makefile.lnx
for d in newfs_hfs.tproj fsck_hfs.tproj; do make -C $d -f Makefile.lnx all; done
make[1]: Entering directory `/usr/src/hfsplus_support/diskdev_cmds-332.14/newfs_hfs.tproj'
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o hfs_endian.o hfs_endian.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o makehfs.o makehfs.c
makehfs.c:54:25: error: openssl/sha.h: No such file or directory
makehfs.c: In function â€˜InitMDBâ€™:
makehfs.c:571: warning: pointer targets in passing argument 1 of â€˜strlenâ€™ differ in signedness
makehfs.c: In function â€˜GenerateVolumeUUIDâ€™:
makehfs.c:2058: error: â€˜SHA_CTXâ€™ undeclared (first use in this function)
makehfs.c:2058: error: (Each undeclared identifier is reported only once
makehfs.c:2058: error: for each function it appears in.)
makehfs.c:2058: error: expected â€˜;â€™ before â€˜contextâ€™
makehfs.c:2074: warning: implicit declaration of function â€˜SHA1_Initâ€™
makehfs.c:2074: error: â€˜contextâ€™ undeclared (first use in this function)
makehfs.c:2080: warning: implicit declaration of function â€˜SHA1_Updateâ€™
makehfs.c:2141: warning: implicit declaration of function â€˜SHA1_Finalâ€™
make[1]: *** [makehfs.o] Error 1
make[1]: Leaving directory `/usr/src/hfsplus_support/diskdev_cmds-332.14/newfs_hfs.tproj'
make[1]: Entering directory `/usr/src/hfsplus_support/diskdev_cmds-332.14/fsck_hfs.tproj'
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o fsck_hfs.o fsck_hfs.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o strings.o strings.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o utilities.o utilities.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o cache.o cache.c
make -C dfalib -f Makefile.lnx libdfa.a
make[2]: Entering directory `/usr/src/hfsplus_support/diskdev_cmds-332.14/fsck_hfs.tproj/dfalib'
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o hfs_endian.o hfs_endian.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BlockCache.o BlockCache.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTree.o BTree.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTreeAllocate.o BTreeAllocate.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTreeMiscOps.o BTreeMiscOps.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTreeNodeOps.o BTreeNode
Ops.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTreeScanner.o BTreeScanner.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o BTreeTreeOps.o BTreeTreeOps.c
BTreeTreeOps.c: In function â€˜InsertLevelâ€™:
BTreeTreeOps.c:436: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o CatalogCheck.o CatalogCheck.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o HardLinkCheck.o HardLinkCheck.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SBTree.o SBTree.c
SBTree.c: In function â€˜SearchBTreeRecordâ€™:
SBTree.c:96: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
SBTree.c: In function â€˜GetBTreeRecordâ€™:
SBTree.c:193: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
SBTree.c: In function â€˜InsertBTreeRecordâ€™:
SBTree.c:225: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
SBTree.c: In function â€˜ReplaceBTreeRecordâ€™:
SBTree.c:287: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
SBTree.c: In function â€˜SetEndOfForkProcâ€™:
SBTree.c:326: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
SBTree.c: In function â€˜CheckBTreeKeyâ€™:
SBTree.c:424: warning: pointer targets in passing argument 1 of â€˜DebugStrâ€™ differ in signedness
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SControl.o SControl.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SVerify1.o SVerify1.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SVerify2.o SVerify2.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SRepair.o SRepair.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SRebuildCatalogBTree.o SRebuildCatalogBTree.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SUtils.o SUtils.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SKeyCompare.o SKeyCompare.c
SKeyCompare.c: In function â€˜CompareAttributeKeysâ€™:
SKeyCompare.c:475: warning: initialization discards qualifiers from pointer target type
SKeyCompare.c:476: warning: initialization discards qualifiers from pointer target type
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SDevice.o SDevice.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SExtents.o SExtents.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SAllocate.o SAllocate.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SCatalog.o SCatalog.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o SStubs.o SStubs.c
gcc -g3 -Wall -I/usr/src/hfsplus_support/diskdev_cmds-332.14/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64 -D LINUX=1 -D BSD=1   -c -o VolumeBitmapCheck.o VolumeBitmapCheck.c
ar rc libdfa.a hfs_endian.o BlockCache.o BTree.o BTreeAllocate.o BTreeMiscOps.o BTreeNodeOps.o BTreeScanner.o BTreeTreeOps.o CatalogCheck.o HardLinkCheck.o SBTree.o SControl.o SVerify1.o SVerify2.o SRepair.o SRebuildCatalogBTree.o SUtils.o SKeyCompare.o SDevice.o SExtents.o SAllocate.o SCatalog.o SStubs.o VolumeBitmapCheck.o
make[2]: Leaving directory `/usr/src/hfsplus_support/diskdev_cmds-332.14/fsck_hfs.tproj/dfalib'
gcc   fsck_hfs.o strings.o utilities.o cache.o dfalib/libdfa.a   -o fsck_hfs
make[1]: Leaving directory `/usr/src/hfsplus_support/diskdev_cmds-332.14/fsck_hfs.tproj'
root@linuxwin2k:/usr/src/hfsplus_support/diskdev_cmds-332.14# ls
clri.tproj           fsck.tproj          mount_nfs.tproj      quot.tproj
dev_mkdb.tproj       include             mount_synthfs.tproj  repquota.tproj
diskdev_cmds-332.11  Makefile            mount.tproj          restore.tproj
disklib              Makefile.include    newfs_hfs.tproj      showmount.tproj
dumpfs.tproj         Makefile.lnx        newfs_msdos.tproj    tunefs.tproj
dump.tproj           mount_cd9660.tproj  newfs.tproj          ufs.tproj
edquota.tproj        mount_devfs.tproj   PB.project           umount.tproj
fdisk.tproj          mountd.tproj        quotacheck.tproj     vndevice.tproj
fsck_hfs.tproj       mount_fdesc.tproj   quotaon.tproj        vsdbutil.tproj
fsck_msdos.tproj     mount_hfs.tproj     quota.tproj
root@linuxwin2k:/usr/src/hfsplus_support/diskdev_cmds-332.14# cd newfs_hfs.tproj
[email]root@linuxwin2k:/usr/src/hfsplus_support/diskdev_cmds-332.14/newfs_hfs.tpro[/email]j# ls
hfsbootdata.img  hfs_endian.o  Makefile.postamble  newfs_hfs.8  PB.project
hfs_endian.c     Makefile      Makefile.preamble   newfs_hfs.c  readme.h
hfs_endian.h     Makefile.lnx  makehfs.c           newfs_hfs.h
[email]root@linuxwin2k:/usr/src/hfsplus_support/diskdev_cmds-332.14/newfs_hfs.tpro[/email]j# cd ..
root@linuxwin2k:/usr/src/hfsplus_support/diskdev_cmds-332.14# cd fsck_hfs.tproj
[email]root@linuxwin2k:/usr/src/hfsplus_support/diskdev_cmds-332.14/fsck_hfs.tpro[/email]j# ls
cache.c  fsck_hfs    fsck_hfs.o          Makefile.preamble  strings.o
cache.h  fsck_hfs.8  Makefile            makestrings        utilities.c
cache.o  fsck_hfs.c  Makefile.lnx        PB.project         utilities.o
dfalib   fsck_hfs.h  Makefile.postamble  strings.c

---

### Post by lance bermudez on 2008-02-03
i installed libssl0.9.8-dbg and libssl-dev and it worked thankyou for your help.

---

### Post by KaOS-bEat on 2008-04-15
thanks 

I needed that one ;)

KaOS

---

