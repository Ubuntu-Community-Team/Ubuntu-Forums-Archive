---
title: "Cannot create file system"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by edmulroy on 2006-11-03
What things might I try to make Umbuntu's installer like this drive? 

I tried to install on a USB hard drive (80G Maxtor).  After formatting it comes back with a dialog box which says it cannot create file system. 

Under Windows I can make it an NTSB drive and copy files to and from it, even doing a chkdsk /f and it works well.  I also made it multiple-partition FAT32 and it worked well.

Dell Latitude D505 laptop, Pentium M, 512M RAM, XP Pro on the built in hard drive.

---

### Post by ReaderRat on 2006-11-03
Do you just want a file system and not to install Ubuntu? Or do you want to install Ubuntu? If so, can you go into the BIOS and set the USB drive to boot?

---

### Post by edmulroy on 2006-11-03
I am trying to install Ubuntu on the USB hard drive so that I can boot from it.  My machine is a Dell Latitude D505 laptop.  At boot time if I press F12 it gives me a boot menu allowing me to select the boot source from the CD, USB or the hard drive. 

During the install it partitions and formats the hard drive.  The cannot create file system complaint came during that operation. 

I'd appreciate it if you shared any ideas you had on what I might try to get around the problem.

---

### Post by CatKiller on 2006-11-03
What filesystem are you trying to make? Ext3?

---

### Post by edmulroy on 2006-11-04
> What filesystem are you trying to make? Ext3?

Yes. 

I am not trying to make it.  The installer is doing that as part of  what it does.  I didn't select ext3 or tell it format.  I just told it to use the hard drive. 

I know the disk formats and works as either of NTFS or multi-partition FAT32 (80G is too big for a single FAT32 partition).  What I don't understand is why it wouldn't work as ext3 and how I might identify the underlying problem and either fix or work around it.

---

### Post by K.Mandla on 2006-11-04
You might try prepartitioning the drive with something like GPartEd, and formatting it manually. When you get to the partitioner step of the installation process, you should be able to assign partitions to mount points. With any luck, it will ignore the formatting and partitioning part of the process and take you straight to setting up the system.

---

### Post by CatKiller on 2006-11-04
> **K.Mandla said:**
> You might try prepartitioning the drive with something like GPartEd, and formatting it manually. When you get to the partitioner step of the installation process, you should be able to assign partitions to mount points. With any luck, it will ignore the formatting and partitioning part of the process and take you straight to setting up the system.

Yes. The other options that I can see are: [LIST=1]
[*]Using the Alternate cd's text installer, which is reportedly less finicky
[*]Use a different filesystem - Reiser or whatever
[*]Fit the drive internally for the install and try to work out how to use it externally later.
[/LIST]

btw, 80 Gig isn't too big for a FAT32 partition - it's just that Microsoft would rather you used NTFS, so their tools won't let you do it. The actual limit for a FAT32 partition, IIRC, is 2 TiB.

---

