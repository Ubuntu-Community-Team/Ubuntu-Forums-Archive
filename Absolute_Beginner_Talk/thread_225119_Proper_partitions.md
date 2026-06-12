---
title: "Proper partitions?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by Matsu on 2006-07-29
So far this forum has been helpful. With a floppy I've been able to boot into the Ubuntu LiveCD. Only problem was when I came to manually setting the partitions (because I want to keep Windows), Ubuntu completely crashed trying to repartition. I suppose that this is fine, given as how it did absolutely nothing (and therefore Windows remained bootable heh), but now that I don't trust the installer to be stable, I want to do it in PartitionMagic. Is this an acceptable partition setting?:

[IMG]http://img.photobucket.com/albums/v238/TerraMatsu/Screenshots/partition2.png[/IMG]

I don't know if I should set the ext3 to primary or logical, nor what the linux swap partition should be.. I'm so lost at this ._.

I also don't know if I should install to the second hard drive instead (50GB free), but in that case I don't know how I'd make the Windows bootloader recognise the Linux one as to dualboot properly.. @_@

---

### Post by Apple 101 on 2006-07-29
Do not create the partitions for Ubuntu in Partition Magic.  Just create the space you will use - it is easier this way.

If you need more information or help, just ask.

---

### Post by wieman01 on 2006-07-29
PartitionMagic is the right tool, I am using it as well for my Dual Boot.

I would partition my drives as follows:

1. /[root] : primary partition, ext3, 8 GB
2. /home : logical partition, ext3, 5 GB
3. /swap : twice the size of your RAM (e.g. 2 x 512 MB = 1 GB)

Having a dedicated partition for "home" is advantageous later on should you ever have to reinstall your system as your settings (stored on home) won't get lost.

---

### Post by wieman01 on 2006-07-29
> **Apple 101 said:**
> Do not create the partitions for Ubuntu in Partition Magic.  Just create the space you will use - it is easier this way.

If you need more information or help, just ask.

Interesting advice... You could be right, using PartitionMagic requires a certain "Linux" knowledge/expertise that users may not have. But generally it works.

---

### Post by Apple 101 on 2006-07-29
I prefer to use:
1. / : logical, ext3, 8 GB
2. /home : logical, ext3, 8 GB
3. [swap] : 2 x RAM

@Matsu: How are you planning to share files between Ubuntu and other operating systems?  You can read/write directly to the ext3 filesystem from Windows, but I find it easier to work with a FAT32 partition for this process.

---

### Post by confused57 on 2006-07-29
It is difficult to install using the Desktop Live CD with less than 256 Mb ram...the alternate CD is used to install on low memory systems.  Also, you need to defrag your Windows a couple of times if you're planning on resizing the Windows partition.
Here's a couple of excellent guides:

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

The gparted LiveCD is a good partitioning tool:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by Matsu on 2006-07-29
> **Apple 101 said:**
> I prefer to use:
1. / : logical, ext3, 8 GB
2. /home : logical, ext3, 8 GB
3. [swap] : 2 x RAM

@Matsu: How are you planning to share files between Ubuntu and other operating systems?  You can read/write directly to the ext3 filesystem from Windows, but I find it easier to work with a FAT32 partition for this process.

Well I was planning on using my second physical hard drive as a file share between the two OSes with some an app to read/write from NTFS, though as I presume NTFS -write- support is rather shaky in Linux. Though perhaps I should just create a 50GB FAT32 partition on that drive, move everything I have over onto it, and then give the resize it to take the rest of the drive?

---

### Post by Matsu on 2006-07-29
> **confused57 said:**
> It is difficult to install using the Desktop Live CD with less than 256 Mb ram...the alternate CD is used to install on low memory systems.  Also, you need to defrag your Windows a couple of times if you're planning on resizing the Windows partition.
Here's a couple of excellent guides:

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)
Huh, well, I have 256Mb exactly, though I'll read into those guides.

---

### Post by Apple 101 on 2006-07-29
> **wieman01 said:**
> Interesting advice... You could be right, using PartitionMagic requires a certain "Linux" knowledge/expertise that users may not have. But generally it works.Yes, that's true.  I just find it easier to let the installer create the partitions in the free space.

I also found that whenever I use Partition Magic for working with ext2/3 and swap partitions it caused corruption.

---

### Post by confused57 on 2006-07-29
> **Matsu said:**
> Huh, well, I have 256Mb exactly, though I'll read into those guides.

Check out the gparted Live CD I added to my previous post...

---

### Post by Apple 101 on 2006-07-29
> **Matsu said:**
> Well I was planning on using my second physical hard drive as a file share between the two OSes with some an app to read/write from NTFS, though as I presume NTFS -write- support is rather shaky in Linux. Though perhaps I should just create a 50GB FAT32 partition on that drive, move everything I have over onto it, and then give the resize it to take the rest of the drive?Linux can ONLY read NTFS partitions.  You can read/write to ext3 from Windows by installing a driver.

The FAT32 partition is safe to read/write from Linux and (obviously) Windows.  You could create a FAT32 partition on it if you wanted to, or convert the entire drive to FAT32 depending what it has on it.  If it holds Windows system files then I wouldn't do that.

---

