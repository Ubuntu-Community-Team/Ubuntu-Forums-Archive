---
title: "Which file system to use for 'storage' partition."
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Gijith on 2006-02-03
Hi everyone.

I have a very beginner type question. I've found some answers, but they seem to be in conflict, so I thought I'd ask you guys. 

I'm just finishing setting up a new computer. I already have a small partition running Windows and a small partition running Kubuntu. The next thing I have to do is transfer the bulk of my files from my old PC. Mostly multimedia and photos. I love (k)ubuntu to death, but still use Windows pretty regularly because I use a lot of Windows only software for my job and I'm not yet comfortable running Wine. At the moment, my time is split pretty 50/50 between the 2 OSes. So I'm going to transfer this large batch of files onto a new partition. My question is, what file system should I use for that partition? ext3? NTFS? Ideally, I'd like something that can be both read from and written to by both Linux and Windows. If that can't be done, than at the very least, something that can be read and written by Linux and read by Windows. 

Sorry if this sort of thing is common knowledge. I haven't had to deal with it before.

Thanks for any info.

Gijith

:-D

---

### Post by AndyCooll on 2006-02-03
For ease, you should use fat32.

I'm assuming your Windoze, Kubuntu and "storage" is all going to be on the same box. Linux can read but can't write at the moment to NTFS.

:cool:

---

### Post by GTvulse on 2006-02-03
Your best bet is FAT32 (search the forums for tips on how to set up your /etc/fstab file). If you create the partition and format it with MS Windows you won't have problems at all. If you do it from Ubuntu, then make sure to tag the partition as  0x0B, that is, a Win95 FAT32 partition. The latter is very easy to do if you use either fdisk or cfdisk.

A second possibiity is using EXT2/3. There is a MS Windows filesystem driver available at [http://fs-driver.org/](http://fs-driver.org/) that will allow you to mount ext2/3 partitions in read/write mode under MS Windows. Yet, the driver is flaky sometimes and you can lose data if you move files instead of copying them to and from the Windows partition.

---

### Post by Gijith on 2006-02-03
Thanks guys.

Cheers.

---

