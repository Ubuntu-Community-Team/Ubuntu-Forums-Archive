---
title: "Installing Breezy Badger"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-04-27
Hello, I downloaded the .iso of Breezy Badger,  checked the mdsum and all was well.  i burned to disk.

I have  new computer rack system. I have a spare cradle and a 200 gig hard drive partitioned to FAT32.  40 gig partitions.

Okay,  I insert the install disk, power down, slap in the partitioned HD, and commence to install Ubuntu to one of the 40 Gig partitions.
Okay, things go fine until we get to the drive partitioning area.  how confusing is this? all i want to do is select one of the drives and install Ubuntu.  the installation keeps wanting me to resize the partition, etc. when i go into the routine manually, i don't know which file format to use...ext2, ext3, etc.

What am I doing wrong?

---

### Post by iball on 2006-04-27
The file system format that most people use is ext3.  This is basically ext2, with journalling support so if your computer shuts down uncleanly, it is less likely that you will lose data.  Therefore, choose ext3.

If you select "Manually edit the partition table", you should be able to erase one of your 40G partitions, and create one partition for root (mount point / and format ext3), and one partition for swap space (formatted swap).  The size of your swap should be roughly 2x your RAM.  See [Here]("http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apa.html") for more.

Post back here if you need more help
--Ian

---

### Post by confused57 on 2006-04-27
Here's a link for dual-booting, but there are some excellent screenshots of partitioning, /home separate partition, etc that you may be able to use:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by jazzmuzik on 2006-04-27
Just to amplify what iball is saying, you don't install Linux on a fat32 partition. Linux wants its own filesystem, which these days is generally ext3. The install program can create this partition for you along with any other partitions you want. You can create fat32 and other partition types, it's just that the OS part of Linux needs to be on one of the Linux filesystems, not fat32 which is a Microsoft thing.

---

### Post by georgetoon on 2006-04-28
[QUOTE=jazzmuzik]Just to amplify what iball is saying, you don't install Linux on a fat32 partition. Linux wants its own filesystem, which these days is generally ext3. The install program can create this partition for you along with any other partitions you want. You can create fat32 and other partition types, it's just that the OS part of Linux needs to be on one of the Linux filesystems, not fat32 which is a Microsoft thing.[/QUOTE]
Thanks for the replies and info guys.:)  Yes, I understand that Linux requires a different file system. I wasn't sure which is best for optimal performance.

My situation is this:  I already have this 200 gig hard drive formatted and partitioned via Seagate's DiscWizard software.  Okay, so, I have have 5 partitions, FAT32, each 40 gigs in size.  

I understand, in order for Ubuntu to use one of these partitions, it needs to be change to ext3.  Fine.  Is this the only change that I need to make?  Because there are many options on this screen.

Please understand, I'm already using Linspire 5.0.  When  I installed Linspire on my older system, I merely partitioned the windows drive in half and then loaded Linspire.  It found the partition and changed everything automatically.  I wish Ubuntu had this kind of installer.

I guess I could just erase the drive's partitions and let Ubuntu install on the full 200 gigs.  But I want to run multiple distros on this drive.  I already have partitions set to go.  Would it be easier to do it this way? Automatically have Ubuntu install on a 200 gig drive and then partition it after this initail install?  Or should I go with a distro that has an easier installer?

---

### Post by Rinzwind on 2006-04-28
Easiest is to delete one of those partitions. 
If Ubuntu finds unused hdd space it'll suggest that as default ;)

So Ubuntu does the same as Linspire. You just created another situation compared to the Lispire situation :)

---

### Post by georgetoon on 2006-04-28
[QUOTE=Rinzwind]Easiest is to delete one of those partitions. 
If Ubuntu finds unused hdd space it'll suggest that as default ;)

So Ubuntu does the same as Linspire. You just created another situation compared to the Lispire situation :)[/QUOTE]

Okay, so what is the easiest method to delete that partition?

---

### Post by Rinzwind on 2006-04-28
[QUOTE=georgetoon]Okay, so what is the easiest method to delete that partition?[/QUOTE]
I think fdisk in windows.

---

### Post by Iowan on 2006-04-28
There ARE some versions of Lunux which can be installed on a vfat partition - but Ubuntu isn't one of them.

---

### Post by georgetoon on 2006-04-28
[QUOTE=Iowan]There ARE some versions of Lunux which can be installed on a vfat partition - but Ubuntu isn't one of them.[/QUOTE]

Dang.  Sure wish Ubuntu had this.:)  It would make it a bit more accessible for me.:):) 

I think perhaps I'll re-run Seagate's DiscWizard and see if this utility will remove the partition.


As I understand what you are saying:  if I remove a partition and just have unformatted space on the hard drive, the Ubuntu install routine will see that unused space, format it, partition it, install on it, etc.  It will ignore the FAT32 partitions.  Am I correct?

---

### Post by confused57 on 2006-04-28
Disk Drake may be an option, I've not personally used it:

[http://www.ubuntuforums.org/showthread.php?t=114142](http://www.ubuntuforums.org/showthread.php?t=114142)

---

### Post by iball on 2006-05-01
Yes, simply delete one Fat32 partition, and leave it unformatted.  Ubuntu will detect this, and partition it automatically for you.  Basically it will create 1 ext3 partition for /, and one swap partition.

It should be able to access the other FAT32 partitions if you want to use one for data sharing between Linux and Windows.  Even versions of linux that *can* be installed to a FAT32 partition will perform better on an ext3.  Ext3 is a good format, because it guards against data loss in the event of a power failure.

Let Ubuntu install its boot loader (GRUB) onto the MBR, and you will be able to dual boot.

--Ian

---

### Post by georgetoon on 2006-05-01
[QUOTE=iball]Yes, simply delete one Fat32 partition, and leave it unformatted.  Ubuntu will detect this, and partition it automatically for you.  Basically it will create 1 ext3 partition for /, and one swap partition.

It should be able to access the other FAT32 partitions if you want to use one for data sharing between Linux and Windows.  Even versions of linux that *can* be installed to a FAT32 partition will perform better on an ext3.  Ext3 is a good format, because it guards against data loss in the event of a power failure.

Let Ubuntu install its boot loader (GRUB) onto the MBR, and you will be able to dual boot.

--Ian[/QUOTE]

Yes, I did this.:)  Seems a bit much, though. Khave a 200 gig drive with nothing but ubuntu. I'd like ot resize and install other Linux distros. Not sure how they will be integrated with MBR.

but thanks to everyone for all the help.:) ubuntu is running and I've got my HDs enabled and al is well.:) Just havd one more question abut automatix which I wil post in a new thread.

---

