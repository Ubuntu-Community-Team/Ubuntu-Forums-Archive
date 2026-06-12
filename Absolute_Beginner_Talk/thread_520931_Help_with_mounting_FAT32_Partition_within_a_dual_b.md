---
title: "Help with mounting FAT32 Partition within a dual boot configuration"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by Galt on 2007-08-08
Hello,

I am a long time Windows user (since 1991) and I'm making the transition over to Linux. This is my first time attempting an install.

I installed Ubuntu 7.04 last night on my home computer and set my system up as a dual boot (with Windows XP Pro). I followed the directions provided at Hermanzone's [Ubuntu+NTFS](http://users.bigpond.net.au/hermanzone/p3.htm) guide. I wanted to create the same setup: separate partitions for each OS, a swap partition, and a FAT32 partition to share data between XP and Ubuntu. The only thing I did differently was that I specified different sizes for my partitions.

The installation went fine with no major problems. I can see the FAT32 drive just fine in XP, but cannot see it within Ubuntu. I tried following the [Mounting Linux Partitions](http://www.psychocats.net/ubuntu/mountlinux) guide at psychocats.net, but couldn't get it to work.

I added the following line to fstab: /dev/sda5 /storage fat32 defaults 0 0
and got the following error when using the command "sudo mount -a": 
  mount: unknown filesystem type 'fat32'
  mount: maybe you meant 'vfat'?

-------------------------

Info from fdisk:

```

user@mycomputer:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536    7  HPFS/NTFS
/dev/sda2            6080       10942    39062047+  83  Linux
/dev/sda3           10943       24321   107466817+   5  Extended
/dev/sda5           11192       24321   105466725    b  W95 FAT32
/dev/sda6           10943       11190     1991997   82  Linux swap / Solaris

Partition table entries are not in disk order

```

Screenshot from gparted:

[img]http://img.villagephotos.com/p/2004-2/630990/Screenshot-GParted.jpg[/img]

I'm sure I am screwing something up easy, but cannot figure out what it is. I suppose this isn't a show stopper; I will probably move over to a complete Ubuntu install in a few months.

More questions:

1) Is the "Partition table entries are not in disk order" message a cause for concern? Is there an easy way to resolve this?

2) Is the sliver of unallocated space in gparted a cause for concern?

2) After I get my FAT32 partition mounted, I'd like to unmount my Windows NTFS /dev/sda1 partition (it appears on the desktop. I assume its as easy as commenting out the relevant line in fstab? I won't screw anything up royally if I do that?


Thanks in advance for any help. I really appreciate it!
Galt

---

### Post by yabbadabbadont on 2007-08-08
Try changing:
```
/dev/sda5 /storage fat32 defaults 0 0
```
To:
```
/dev/sda5 /storage vfat defaults 0 0
```

---

### Post by AlexenderReez on 2007-08-08
referring to your screenshot....i see all your partitions already mount and you should find it...in /media/


your fat32 partition (which is windows partition) should be in /media/windows

1.1) Is the "Partition table entries are not in disk order" message a cause for concern? Is there an easy way to resolve this?

hm....because you when you make linux partition,you did format your sda3 and divide it....so this may cause the table is not in disk order:)

2) Is the sliver of unallocated space in gparted a cause for concern?

no,that just spare space ...some sort like linux swap in linux(not really....but it is not important)

3.After I get my FAT32 partition mounted, I'd like to unmount my Windows NTFS /dev/sda1 partition (it appears on the desktop. I assume its as easy as commenting out the relevant line in fstab? I won't screw anything up royally if I do that?

you can unmount manually or using terminal for that...with editing that fstab:)

---

### Post by Galt on 2007-08-08
OK, I am a moron. :)

@AlexenderReez:

The partition is actually in "File System/Windows". Its been there all along.

I think the issue with the partitions being out of order was due to me selecting "place partition at the end of Free Space" when setting up /sda5.

I can't seem to unmount /sda1 by right clicking > unmount, so I will try it via fstab.

@yabbadabbadont:

Looks like I don't need to mount it after all. Thank you for your help, though.

---

### Post by logos34 on 2007-08-08
You should do as AlexanderReez just suggested and change the mount point to the /media dir.
> 
1) Is the "Partition table entries are not in disk order" message a cause for concern? Is there an easy way to resolve this?

Nothing to worry about--it's merely referring to the order of your logical paritions (sda6-->sda5).  I have some like that.

As for ntfs sda1, you can simply 'umount' it.  If you do not want it to mount each time at boot, put a 'noauto' option in the sda1 entry in /etc/fstab.

---

### Post by Al3xK3aton on 2007-08-08
Why not just use NTFS instead of FAT32? It is superior, and more reliable.

---

### Post by logos34 on 2007-08-08
> 
I can't seem to unmount /sda1 by right clicking > unmount, so I will try it via fstab.

just use the terminal

**sudo umount /media/sda1**

---

### Post by Galt on 2007-08-08
> **logos34 said:**
> You should do as AlexanderReez just suggested and change the mount point to the /media dir.

Good call. I changed it over.

---

### Post by Galt on 2007-08-08
> **Al3xK3aton said:**
> Why not just use NTFS instead of FAT32? It is superior, and more reliable.

I thought I had read somewhere (in preparation for my install) that NTFS read/write support was still experimental / in beta, so I opted for FAT32 instead. That info might of been a bit outdated.

---

### Post by logos34 on 2007-08-08
yeah, that 'experimental' bit is best ignored.  Go to the ntfs-3g home page and you'll see it's been fairly exhaustively tested.  A lot of people in this forum will attest to its reliability.  

Using Partimage to clone/restore ntfs partitions--now that's experimental (you can't trust it).

---

