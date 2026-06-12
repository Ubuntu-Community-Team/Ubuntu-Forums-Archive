---
title: "access hfs+ partitions"
date: 2004-10-26
forum: Apple PPC Users
---

### Post by vj2k on 2004-10-26
Can we access hfs+ partitions from ubuntu.
Is there any Graphical tool for this purpose?
thanks
vijay

---

### Post by diabolo on 2004-10-27
I've never tried to mount hfs+ so I don't know but I'll make a guess:
Have you tried to mount with the **-t hfsplus** option?
That might not work, but it appears there's a hfs+ tool included, check it out: **man hfsplus**

---

### Post by batman on 2004-10-29
Yes there is "hfsplus". Just do a "sudo mount /dev/hda3 /mnt/MacOSX -thfsplus" (example) and that will do the trick. Before that you have to create the mount point (in this example /mnt/MacOSX). To save this settings edit /etc/fstab. Bye.

---

### Post by vj2k on 2004-10-29
[QUOTE=batman]Yes there is "hfsplus". Just do a "sudo mount /dev/hda3 /mnt/MacOSX -thfsplus" (example) and that will do the trick. Before that you have to create the mount point (in this example /mnt/MacOSX). To save this settings edit /etc/fstab. Bye.[/QUOTE]
Will try this.
Thanks
vj

---

### Post by chascon on 2005-02-22
I used to mount panther to /mnt/macos but you can't do anything with it because of permissions problems.  You can't even drag things to Users/Shared this way.
If you create the macos file in on your ubuntu user dir, then you can cp to Shared on OS X.

This is my command,
"sudo mount -t hfsplus /dev/hda3 /home/mauro/macOSX"
so what is "-thfsplus" doing at the end of your command?
Is that correct syntax?
Just wondering.

To unmount, just replace "mount" to "umount" and make sure you quit any folders that might be viewing "macOSX" or inside of it via a gui window, else then you'll get a "busy" message.  Even if you get a "busy" message after closing windows, try the command again.  If then it still persists as busy, you'll have to reboot rather than forcing it (which in my experience on another *nix can do funny things).

---

### Post by linuxfanatic1024 on 2005-07-25
Here's a valuable tip for users who are having trouble mounting hfsplus disks/partitions in Linux because of a paranoid message telling you to fix the drive. You need to download the two attachments, a patch and a source archive, and patch the source archive, so you can use Apple's official fsck and newfs commands on Linux.

Download these to the same directory. Then, type these into a shell as a **normal user** (do **not** use the root account for this):

```

tar zxvf diskdev_cmds-208.11.tar.gz
gunzip diskdev_cmds.diff.gz
cd diskdev_cmds-208.11/
patch -p1 < ../diskdev_cmds.diff
make -f Makefile.lnx
sudo cp newfs_hfs.tproj/newfs_hfs /sbin/mkfs.hfs
sudo cp fsck_hfs.tproj/fsck_hfs /sbin/fsck.hfs
cd /sbin
sudo ln -s mkfs.hfs mkfs.hfsplus
sudo ln -s fsck.hfs fsck.hfsplus

```

---

### Post by calum on 2005-07-26
[QUOTE=chascon]I used to mount panther to /mnt/macos but you can't do anything with it because of permissions problems.  You can't even drag things to Users/Shared this way.[/QUOTE]

You should be able to get around this by setting your (numerical) Ubuntu user id to that of your (numerical) OSX user id.  E.g. if I do:

> ls -l /mnt/macosx/Users
total 0
drwxr-xr-x  1  501  501 55 2005-07-26 01:10 calum
drwxrwxrwt  1 root root  8 2005-06-04 15:28 Shared

I can see that my Ubuntu uid needs to be 501 to allow me access to my OSX homedir.  You can check or change your current uid in System->Administration->Users and Groups.  Or you could change your OSX ID to match your Ubuntu one... I forget if OSX gives you a GUI for that, or if you have to do it on the commandline.  Either way, remember that changing uids may affect access to any other network filesystems you have mounted.

---

### Post by autocrosser on 2005-07-26
Well-if you edit /etc/fstab & then reboot--there will be a /mnt directory in your / directory--I just put the /osx (thats what I named it in fstab) on my upper menu panel--you can browse it as your normal user--if you find locked/no access files, you can--
1. log in as root in Ubuntu & change the permissions
2. boot OSX & as your normal user & change permissions

I wouldn't open up OSX too much [-X --It's real easy to bork OSX from Linux--too easy to change/modify the wrong file & make it un-bootable--I log-in as Root in Linux if I want to change things--this still keeps checks in place--If you want a un-limited file area--remember in your OSX users area there is a "Shared" area--remove all permissions there & use it as the swap between the two....


I was one of the beta testers for OSX & well remember the "fun" we had to even get it working right :-| 

My two cents worth...


Cheers!!
Dean

---

### Post by BoneKracker on 2006-05-20
That is indeed a valuable tip from linuxfanatic1024.  There's also an updated version of those utilities out for testing. 

Sadly, I couldn't either version to compile.  I would really appreciate any help from someone who got this working.  Would this compile in gcc 4.0? (I'm using dapper.)  Also, I notice there was no "configure" script; could I be lacking dependencies and how can I tell?

If it's of use, here's the (long-winded) output of the make (after patching it of course):
```
john@typhoon:/usr/local/src/diskdev_cmds-208.11$ make -f Makefile.lnx
for d in newfs_hfs.tproj fsck_hfs.tproj; do make -C $d -f Makefile.lnx all; donemake[1]: Entering directory `/usr/local/src/diskdev_cmds-208.11/newfs_hfs.tproj'gcc -g -O2 -Wall -I/usr/local/src/diskdev_cmds-208.11/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64   -c -o newfs_hfs.o newfs_hfs.c
In file included from hfs_endian.h:32,
                 from newfs_hfs.h:28,
                 from newfs_hfs.c:55:
/usr/local/src/diskdev_cmds-208.11/include/architecture/byte_order.h:17:1: warning: "__BIG_ENDIAN__" redefined
<built-in>:1:1: warning: this is the location of the previous definition
newfs_hfs.c: In function ‘hfsplus_params’:
newfs_hfs.c:573: warning: pointer targets in assignment differ in signedness
newfs_hfs.c:576: warning: pointer targets in passing argument 1 of ‘__builtin_strncpy’ differ in signedness
newfs_hfs.c: In function ‘hfs_params’:
newfs_hfs.c:709: warning: pointer targets in passing argument 1 of ‘__builtin_strncpy’ differ in signedness
gcc -g -O2 -Wall -I/usr/local/src/diskdev_cmds-208.11/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64   -c -o makehfs.o makehfs.c
In file included from hfs_endian.h:32,
                 from makehfs.c:55:
/usr/local/src/diskdev_cmds-208.11/include/architecture/byte_order.h:17:1: warning: "__BIG_ENDIAN__" redefined
<built-in>:1:1: warning: this is the location of the previous definition
makehfs.c: In function ‘make_hfs’:
makehfs.c:219: warning: pointer targets in passing argument 3 of ‘WriteReadMeFile’ differ in signedness
makehfs.c:226: warning: pointer targets in passing argument 3 of ‘WriteSystemFile’ differ in signedness
makehfs.c: In function ‘InitMDB’:
makehfs.c:534: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
makehfs.c: In function ‘InitCatalogRoot_HFSPlus’:
makehfs.c:1147: warning: pointer targets in passing argument 1 of ‘ConvertUTF8toUnicode’ differ in signedness
makehfs.c:1178: warning: pointer targets in passing argument 1 of ‘ConvertUTF8toUnicode’ differ in signedness
makehfs.c: In function ‘InitFirstCatalogLeaf’:
makehfs.c:1271: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
makehfs.c: In function ‘InitCatalogRoot_HFS’:
makehfs.c:1494: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
gcc   newfs_hfs.o makehfs.o   -o newfs_hfs
make[1]: Leaving directory `/usr/local/src/diskdev_cmds-208.11/newfs_hfs.tproj'
make[1]: Entering directory `/usr/local/src/diskdev_cmds-208.11/fsck_hfs.tproj'
gcc -g -O2 -Wall -I/usr/local/src/diskdev_cmds-208.11/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64   -c -o fsck_hfs.o fsck_hfs.c
gcc -g -O2 -Wall -I/usr/local/src/diskdev_cmds-208.11/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64   -c -o strings.o strings.c
gcc -g -O2 -Wall -I/usr/local/src/diskdev_cmds-208.11/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64   -c -o utilities.o utilities.c
gcc -g -O2 -Wall -I/usr/local/src/diskdev_cmds-208.11/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64   -c -o cache.o cache.c
make -C dfalib -f Makefile.lnx libdfa.a
make[2]: Entering directory `/usr/local/src/diskdev_cmds-208.11/fsck_hfs.tproj/dfalib'
gcc -g -O2 -Wall -I/usr/local/src/diskdev_cmds-208.11/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64   -c -o BlockCache.o BlockCache.c
In file included from hfs_endian.h:32,
                 from SRuntime.h:38,
                 from BlockCache.c:23:
/usr/local/src/diskdev_cmds-208.11/include/architecture/byte_order.h:17:1: warning: "__BIG_ENDIAN__" redefined
<built-in>:1:1: warning: this is the location of the previous definition
gcc -g -O2 -Wall -I/usr/local/src/diskdev_cmds-208.11/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64   -c -o BTree.o BTree.c
In file included from hfs_endian.h:32,
                 from SRuntime.h:38,
                 from BTree.h:37,
                 from BTree.c:37:
/usr/local/src/diskdev_cmds-208.11/include/architecture/byte_order.h:17:1: warning: "__BIG_ENDIAN__" redefined
<built-in>:1:1: warning: this is the location of the previous definition
gcc -g -O2 -Wall -I/usr/local/src/diskdev_cmds-208.11/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64   -c -o BTreeAllocate.o BTreeAllocate.c
In file included from hfs_endian.h:32,
                 from SRuntime.h:38,
                 from BTree.h:37,
                 from BTreePrivate.h:39,
                 from BTreeAllocate.c:36:
/usr/local/src/diskdev_cmds-208.11/include/architecture/byte_order.h:17:1: warning: "__BIG_ENDIAN__" redefined
<built-in>:1:1: warning: this is the location of the previous definition
gcc -g -O2 -Wall -I/usr/local/src/diskdev_cmds-208.11/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64   -c -o BTreeMiscOps.o BTreeMiscOps.c
In file included from hfs_endian.h:32,
                 from SRuntime.h:38,
                 from BTree.h:37,
                 from BTreePrivate.h:39,
                 from BTreeMiscOps.c:36:
/usr/local/src/diskdev_cmds-208.11/include/architecture/byte_order.h:17:1: warning: "__BIG_ENDIAN__" redefined
<built-in>:1:1: warning: this is the location of the previous definition
gcc -g -O2 -Wall -I/usr/local/src/diskdev_cmds-208.11/include -DDEBUG_BUILD=0 -D_FILE_OFFSET_BITS=64   -c -o BTreeNodeOps.o BTreeNodeOps.c
In file included from hfs_endian.h:32,
                 from SRuntime.h:38,
                 from BTree.h:37,
                 from BTreePrivate.h:39,
                 from BTreeNodeOps.c:36:
/usr/local/src/diskdev_cmds-208.11/include/architecture/byte_order.h:17:1: warning: "__BIG_ENDIAN__" redefined
<built-in>:1:1: warning: this is the location of the previous definition
BTreeNodeOps.c: In function ‘InsertKeyRecord’:
BTreeNodeOps.c:645: error: invalid lvalue in increment
make[2]: *** [BTreeNodeOps.o] Error 1
make[2]: Leaving directory `/usr/local/src/diskdev_cmds-208.11/fsck_hfs.tproj/dfalib'
make[1]: *** [dfalib/libdfa.a] Error 2
make[1]: Leaving directory `/usr/local/src/diskdev_cmds-208.11/fsck_hfs.tproj'
make: *** [all] Error 2
john@typhoon:/usr/local/src/diskdev_cmds-208.11$
```

---

### Post by JacksSmolderingServer on 2006-06-22
Same issue here as BoneKracker :( Also using dapper.  Is there a new way of doing this?

Scott

---

### Post by BoneKracker on 2006-06-24
Yeah, it's called Darwin

---

### Post by BoneKracker on 2006-06-24
No, seriously I don't know.

Oh, but I did get newfs_hfs to compile.  It was only fsck that didn't work.

Of course, that's the piece I really wanted.

---

### Post by mvip on 2006-08-19
I was googling a little bit for this, since in ran into the same compiling issues as other people did (btw, make sure you install gcc [apt-get install gcc], else you wont even get there).
However, when I was googling I found this: [http://gentoo-wiki.com/HOWTO_hfsplus#Compiling_Apple.27s_Filesystem_Tools]("http://gentoo-wiki.com/HOWTO_hfsplus#Compiling_Apple.27s_Filesystem_Tools")

In that guide, they use a newer version of the sofware. However, since the opendarwin site seems to be down when I tried, I cannot say wheter it worked or not, but I thought that I just wanted to mention it.

Here's their steps:
> wget [http://darwinsource.opendarwin.org/tarballs/apsl/diskdev_cmds-332.14.tar.gz](http://darwinsource.opendarwin.org/tarballs/apsl/diskdev_cmds-332.14.tar.gz)
wget [http://www.ecl.udel.edu/~mcgee/diskdev_cmds/diskdev_cmds-332.14.patch.bz2](http://www.ecl.udel.edu/~mcgee/diskdev_cmds/diskdev_cmds-332.14.patch.bz2)
tar zxf diskdev_cmds-332.14.tar.gz
bunzip2 -c diskdev_cmds-332.14.patch.bz2 | patch -p0
cd diskdev_cmds-332.14
make -f Makefile.lnx
cp newfs_hfs.tproj/newfs_hfs /sbin/mkfs.hfsplus
cp fsck_hfs.tproj/fsck_hfs /sbin/fsck.hfsplus
cd /sbin
ln -s mkfs.hfsplus mkfs.hfs
ln -s fsck.hfsplus fsck.hfs

Enjoy.

---

### Post by gromm on 2006-10-01
> **BoneKracker said:**
> No, seriously I don't know.

Oh, but I did get newfs_hfs to compile.  It was only fsck that didn't work.

Of course, that's the piece I really wanted.


I got everything to compile correctly on Dapper by simply using gcc-3.4 instead of gcc-4.0.  If you have both installed, you should see both listed when doing:  ls -l /usr/bin/gcc*     You will also note that in dapper, /usr/bin/gcc is symlinked to /usr/bin/gcc-4.0.  Change the symlink to point to /usr/bin/gcc-3.4, and you should be good to go.

---

