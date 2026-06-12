---
title: "Question about Partitioning"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-04-29
I installed Ubuntu onto a fairly small chunk (20gb) of my 80gb hard drive, because i though i was going to install WIndows on it too. But i love Ubuntu too much so im just going to stick with that.

Now i am wanting to expand the space that Ubuntu is installed on. Can i just resize the hda1 partition and keep all my files or do i need to create a secondary partition?

---

### Post by ajmorris on 2007-04-29
> **bobbocanfly said:**
> I installed Ubuntu onto a fairly small chunk (20gb) of my 80gb hard drive, because i though i was going to install WIndows on it too. But i love Ubuntu too much so im just going to stick with that.

Now i am wanting to expand the space that Ubuntu is installed on. Can i just resize the hda1 partition and keep all my files or do i need to create a secondary partition?

I assume that 60gb is unpartitioned....
open gparted : not sure where it is in the menus, but press alt + F2 and type gparted into the dialog box that comes up. If it is not installed then go to synaptic : System >> administration >> Synaptic Package Manager and install gparted. Then do the run command ^^. Then open gparted and right click on your ubuntu partition (ext3 probably) and click resize, then just drag the partition over the unpartitioned space.

---

### Post by ahaslam on 2007-04-29
You'll need the Gparted Live CD as the partition to be  resized is mounted. The above will only work as root, on unmounted drives.

---

### Post by lukew on 2007-04-29
> **bobbocanfly said:**
> I installed Ubuntu onto a fairly small chunk (20gb) of my 80gb hard drive, because i though i was going to install WIndows on it too. But i love Ubuntu too much so im just going to stick with that.

Now i am wanting to expand the space that Ubuntu is installed on. Can i just resize the hda1 partition and keep all my files or do i need to create a secondary partition?

You should just format your window partition(s) using mkfs.ext3 and then add the new paritions into fstab?

---

### Post by lukew on 2007-04-29
> **lukew said:**
> You should just format your window partition(s) using mkfs.ext3 and then add the new paritions into fstab?

Forgot to add upgrade-grub afterwards to remove then windows entry.

---

### Post by jmartrican on 2007-04-29
ajmorris,  
Why isn't fdisk needed?  Also, whats the cli version of what you said.

I would of thought it'd be fdisk to partition, mke2 to create the filesystem, mount to create the mount point, fstab so that the mount point is there on boot up, and grub if is windows is in it.

thanks

---

### Post by az on 2007-04-29
If your free partition comes after the Ubuntu partition, yes, you can just resize the partition (and the filesystem too!).  If the free space is before the Ubuntu partition, you are going to have to copy the partition to the beginning of the free space and then extent it from the end. 

You cannot expand a partition from the beginning.

You can use the Ubuntu live cd.  You just have to boot it and unmount your swap before you run gparted from it.

---

### Post by Malta paul on 2007-04-29
I agree with Lukew. It is safer to use a separate partition, so as to protect your files on the other :)

---

### Post by lukew on 2007-04-30
> **jmartrican said:**
> ajmorris,  
Why isn't fdisk needed?  Also, whats the cli version of what you said.

I would of thought it'd be fdisk to partition, mke2 to create the filesystem, mount to create the mount point, fstab so that the mount point is there on boot up, and grub if is windows is in it.

thanks

You dont need fdisk because the parition is already there.
mount assigns that mount point; fstab is a cached version of known mount points. the only thing you would need to do is to create a dir where you want the mount point to be.

Luke

---

