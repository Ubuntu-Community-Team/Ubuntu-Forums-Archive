---
title: "Get back HD space from Linux + Windows Vista"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by X40nick on 2008-01-07
Hi.

I did install Ubuntu for a friend on his laptop, he doesn't want it. I have tried to keep him but no luck.

How can I use the 40GB partition to get it back into the main one? He is using Windows Vista, so that there is only 1 partition not 2. 

Can I do it for him, or do I need to just re-install Windows.

Thank you, please help! I know it is Windows help. But I did try to keep him with us!

I will use Ubuntu forever!

Nick

---

### Post by taurus on 2008-01-07
Use Gparted from GParted LiveCD to delete Ubuntu partition(s).  Then, merge the unused space into windows partition.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by The Cog on 2008-01-07
Nooooooo!
Deleting the Ubuntu partition will leave both OSs un-bootable. You must replace the GRUB bootloader with a different one before deleting the partition. I'm not sure how you would do that.

Once the bootloader is replaces, the machine should just boot straight into windows. Then you can delete the Ubuntu partitions with gparted (on the live installer CD). Vista has its own disk manager that can then expand the NTFS partition to fill the rest of the disk.

---

### Post by X40nick on 2008-01-08
With the previous versions of Windows you can "fixmbr" it wipes the old MBR away, and a new one comes.

If it is too difficult I will just re-install Windows.

Thanks, is there any tutorials about how to do it?

Nick

---

### Post by bumanie on 2008-01-08
Before reinstalling, you could try a system restore with vista and see if that returns the hard drive to the state it was prior to the ubuntu install.
Otherwise (I think), vista is the same as xp, where you can put the cd into cdrom drive and choose recovery console. Once in recovery console type fix mbr. This, in theory will restore the vista mbr and overwrite any grub references.
I have tried this in xp and never found it to work, but it is, I believe, the method suggested by microsoft to restore a corrupt/missing/altered mbr.
After that you should be able to use the vista partition manager to change the partition size to what you desire. Unless it has changed recently, gparted does not work well with vista.

---

### Post by X40nick on 2008-01-08
I always the use command "fixmbr" and it works like a charm.

I knew Gparted wasn't going to work! I don't think that the Vista disc will be able to do that, will it just read it as Unknown Volume?

Thank you.

Nick

---

