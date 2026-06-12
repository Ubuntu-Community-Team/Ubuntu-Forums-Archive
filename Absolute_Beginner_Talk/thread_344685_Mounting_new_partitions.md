---
title: "Mounting new partitions"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by johnrh on 2007-01-23
Hello,

I realise that this problem is rather an old chestnut, other users have touched on it. However, the  replies given are a little obscure to me, so maybe Absolute Beginners is the right place to ask. Thanks for any simple instructions that anyone can give me, and sorry if this is a bit long!

I've been sharing a SATA hard disk between 6.10 and Xp, with GRUB bootloader. So far so good. I just had reason to reinstall Xp in the (reformatted) Windows partition, also to split an older IDE disk into two partitions, 1 NTFS and 1 FAT32. Xp is working fine, although I've lost GRUB from the new MBR.

I started 6.10 directly using the Super Grub Disk and found that the new partitions don't show up in 'Computer'. They show up correctly in 'Device Manager', and 'sudo fdisk -l' returns 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7114    57143173+   7  HPFS/NTFS
/dev/sda2            7115        7179      522112+  82  Linux swap / Solaris
/dev/sda3            7180        9729    20482875   83  Linux

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1044     8385898+   c  W95 FAT32 (LBA)
/dev/hda2            1045        4997    31752472+   7  HPFS/NTFS

Which is correct. So obviously /dev/sda1, /dev/hda1 and /dev/hda2 need to be mounted. I've read what threads I can find, tried 'sudo mount /dev/sda1' etc and get 'mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab'. OK, this accords with what I've read, but now I'm lost. Sorry!

Should I infer from the the threads that I need to manually edit the fstab file? This is what it reads now...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda2 -- converted during upgrade to edgy
UUID=8a544b42-7361-4a5e-b647-b17c42c1be58 / ext3 defaults,errors=remount-ro 0 1

# /dev/hda1 -- converted during upgrade to edgy
UUID=9A043B99043B76FB /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

# /dev/sda1 -- converted during upgrade to edgy
UUID=4890AF9B90AF8DCE /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

# /dev/sda3 -- converted during upgrade to edgy
UUID=4e85effc-d370-4e21-8432-f3cc889d3b6a none swap sw 0 0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I'd be very grateful if any expert out there could return me a new fstab showing what it should read so I can mount the new partitions. (I'd prefer to mount them in /media/ if poss). I have to say that that this seems to me a very cumbersome procedure for something that must be quite common. Anyone know a program or script that can automate it?

I suppose that when I finally crack this I can use SGD to restore GRUB to the new MBR. And once again, my thanks to any expert out there.....

---

### Post by bodhi.zazen on 2007-01-23
You either need to edit fstab or supply a mount point.

```
sudo mkdir /media/data
sudo mount /dev/sda1 /media/data
```

You also need to deal with permissions.

See here:

Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```[/list]

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by johnrh on 2007-01-23
Thanks a lot for your quick reply. Bit late now in my part of the world, so will look at it tomorrow and report back on results.

---

### Post by johnrh on 2007-01-26
Hi, just remembered I promised to report back on this one!

First, thanks to bodhi.zazen for his excellent and detailed reply, also his good links. Obviously a manual edit of fstab was needed. However I found his post rather daunting for a non-expert, so took another path. Having just completed a hardware upgrade (cpu, mboard, ram), which was the cause of my original problems, I found Ubuntu would no longer boot/shutdown reliably. So with some trepidation I decided on a complete reinstall from the Live CD.

To my pleasant surprise it all went rather smoothly! Also, of course, it picked up all my new drives/partitions, thus solving the original problem. It was also easy to move 10GB from my Windows partition over to Ubuntu.

Now to reinstall all of my non-Live CD packages. I found that the trick given by Arsgeek at

[http://72.14.203.104/search?hl=en&lr=&c2coff=1&q=cache%3Ahttp%3A%2F%2F](http://72.14.203.104/search?hl=en&lr=&c2coff=1&q=cache%3Ahttp%3A%2F%2F)
[www.arsgeek.com%2F%3Fp%3D564&btnG=Search](www.arsgeek.com%2F%3Fp%3D564&btnG=Search)

worked well. (This should be one long url). But expect a few broken dependencies, easily fixed using apt-get. So I've ended up pretty well back where I started.

bodhi.zazen's link to [http://www.fs-driver.org/](http://www.fs-driver.org/) is recommended. This program allowed me to access and copy many files from my 'home' to the FAT32 partition that I'd created for that purpose. It all took an entire afternoon down the tubes, but a darn sight easier than the same thing with Windows! (Need I say?)

I realise that this report doesn't give answers to the original question about mounting new partitions, but I thought I may as well write it in case there's something here that could be helpful to Absolute Beginners.

Actually, I do now have a bit of a problem with my SATA drive, but that's another story.....

---

