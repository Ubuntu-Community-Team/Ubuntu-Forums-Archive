---
title: "unable to chown or chmod on USB drive"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Xichtli on 2006-05-13
I discovered that root is the owner of all of the files on my USB drive. I also discovered that I cannot change the ownership or permissions on any of the files stored on this USB drive.

Has anyone else experienced this, and more importantly, is able to offer to me the solution?

Thanks

---

### Post by aysiu on 2006-05-13
USB drives tend to be FAT16 or FAT32.
These filesystems cannot be *chown*ed or *chmod*ed.

Read this for more details: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Xichtli on 2006-05-13
Thanks for the link. I read it. I didnt see any mention of USB drives on that page, However I will accept what you state on face value. I cannot chmod or chown any files on the USB drive. How unfortunate for me.

I cant think of a course of action right now. information overload from learning too much too quickly. Yet I do have to come up with a solution soon.

I keep my financial files on a USB drive, typically accessed for modification, using a ms excel. I am planning an extended trip to Canada soon. I was thinking of taking my Ubuntu-installed old laptop with me. I was hoping to track my expenses in the same manner as I have been doing. I can open the .xls file in Openoffice-2.0 calc and read it, but it is in read-only permission and will not save any modifications I make. 

sorta bummed out.

---

### Post by aysiu on 2006-05-13
Sorry. I should have explained a bit more.

First of all, something is wrong. USB drives should be automounted with the correct permissions. Usually, when I stick in a USB stick or external hard drive (or iPod), Ubuntu plops it on to my desktop and it's mounted with read/write permissions.

So, something's not functioning properly.

That tutorial I linked you to allows you to force Ubuntu to behave properly for that particular link. Mounting USB drives is the same procedure as mounting other partitions. You find the location, create a mount point, and edit the /etc/fstab file with the proper mount parameters.

The only difference is that partitions tend to be things like /dev/hda1 and /dev/hdb1. USB drives tend to be /dev/sda1 and /dev/sde1.

---

### Post by Xichtli on 2006-05-13
Thank You for your time and valuable guidance. And for offering a solution. 

The two linux classes i attended in college barely covered mounting and failed to include varying devices such as USB drives. It was mostly about Red hat, which IMHO, runs horribly on my laptop. I love using UBUNTO Breezy Badger instead.

once again thank you

---

### Post by steve.horsley on 2006-05-13
Pretty-much all USB sticks are FAT. And FAT was invented for DOS - it doesn't store information on file ownership because DOS wasn't multi-user.

FAT does have a read-only flag, and if for some reason your files are all marked read-only, chmod +w should fix it. But I suspect that Aysiu is right and the stick is being mounted read-only (the **mount** command might tell you if this is so). If so, I don't know what to do except remount it rw by hand or maybe make an fstab entry for it with umode=000.

---

