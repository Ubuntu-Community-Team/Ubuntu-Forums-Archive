---
title: "Can't install testdisk"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by datapusher on 2007-12-28
I am trying to recover some important data for my mother off of a drive.  it appears that the 4 or 5 partitions just merged into 1 partition.

It is my hope that test disk can find and fix the partition table and I will be able to grab some or all of the data off of her documents partition.

however, when I download the following file:
[http://archive.ubuntu.com/ubuntu/pool/universe/t/testdisk/testdisk_6.6.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/universe/t/testdisk/testdisk_6.6.orig.tar.gz)

I then untarred it and changed to that dir.  Here is where things get confusing:

```
**./configure**
[I]checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.[/I]

**make**
*make: *** No targets specified and no makefile found.  Stop.*
```

Any guidence would be greatly appreciated.  I will be at this location till tommorow.  Then I will have to give up on any data recovery.  So any input helps.  Thank you!

---

### Post by spiderbatdad on 2007-12-28
I believe you need to install the package build-essential from synaptic...also not all tarballs require ./configure or even make...sometimes you can just run sudo make install, but you should check the documentation in the main directory...a readme or install file perhaps. Though it looks like you're doing the right thing.

---

### Post by datapusher on 2007-12-28
Yeah I spaced build essentials.  I did it in the intsall an hour before hand so I over looked it.

I ran installed build essentials off the cd and also installed libncurses5 libncurses5-dev.

Since I am going to be trying to save an XP partition I assume some sort of NTFS library is required.  I am going to look through the config output and see.

Here we go:

[I]```
checking for ext2fs_open in -lext2fs... no
configure: WARNING: No ext2fs library detected
checking for jpeg_std_error in -ljpeg... no
configure: WARNING: No jpeg library detected
checking for ntfs_device_mount in -lntfs... no
checking for ntfs_libntfs_version in -lntfs... no
configure: **WARNING: No ntfs library detected**
checking for libreiserfs_get_version in -lreiserfs... no
configure: WARNING: No reiserfs library detected
checking for compress2 in -lz... no
configure: WARNING: Missing function: compress2 in library zlib
checking for MD5_Init in -lcrypto... no
configure: WARNING: Missing function: MD5_Init in library libcrypto
checking for uuid_generate in -luuid... no
configure: WARNING: Missing function: uuid_generate in library libuuid
checking for libewf_check_file_signature in -lewf... no
configure: WARNING: No ewf library detected
```[/I]

So I ran:
**```
sudo apt-get install libntfs9
```**

I am about to try make and mak install again.  I'll post what my results are.

Does anyone see any issues with my logic?

---

### Post by Irihapeti on 2007-12-28
I know this isn't what you are asking, but Testdisk is available on the GParted liveCD. Is using that an option?

---

### Post by datapusher on 2007-12-28
I ended up having to install any package that had ntfs in the title to get the ntfs warning to go away in the configure.

I still can't get this thing to install.

Tried it again and it installed

TestDrive is an amazing program.  Just the simple fact that it sees the XP partitions that Linux & Windows were reporting as a single partiton.  I am thinking this is a good start.

I was able to get a lot of information copied from the **Documents** partition.  or at least I think that it copied.

However, the TestDrive CAN see the **Pictures** partition, however I can not access it :-(

Apparently these are the files she want s to recover the most so I will keep plugging away.  learning as I go.  

Hopefully i will find a way to salvage the pictures on the **Pictures** partition.  Any advice is appreciated!

---

