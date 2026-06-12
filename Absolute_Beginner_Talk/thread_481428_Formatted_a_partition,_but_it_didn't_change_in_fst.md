---
title: "Formatted a partition, but it didn't change in fstab"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-06-22
Hi, here I am with another newbie question :)

I just made the big step and removed Windows. I booted into the live cd, started gparted, formatted the NTFS partition where Vista used to live and rebooted. Ubuntu started and everything is just fine, I found the empty partition in /media. But I can't put anything there, I only get an error message saying Access denied. Also, in fstab the partition is still NTFS. Why is this?

I copy/pasted the two lines in fstab containing the old Windows partition:

# /dev/sda2
UUID=84FA5246FA523520 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

Thanks in advance!
Joakim

---

### Post by LaRoza on 2007-06-22
You were dual booting?

Change you partitions, I would recommend using GParted live to do the following:

1. Delete the ntfs partition
2. Create a new partition OR Expand the Ubuntu partition to fill that area.

If you still have an NTFS partition, you didn't format it.

---

### Post by LaRoza on 2007-06-22
Note that if you expand, you will not format that unallocated space. Also, you will not have /dev/sda2 anymore.

---

### Post by bodhi.zazen on 2007-06-22
Two comments:

1. You need [ntfs-config (ntfs-3g)](http://ubuntuforums.org/showthread.php?t=337970) to write to a NTFS partition.

2. Why ntfs ? If yo do not have windows any longer format it to ext3 (or other) linux native file system.


Well 3 comments then :

3. If you re-format the partition the UUID will change and you will need to update fstab.

To list the partitions by UUID : ```
blkid
```

For an overview of fstab : [How to fstab](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by logos34 on 2007-06-22
> I booted into the live cd, started gparted, formatted the NTFS partition where Vista used to live and rebooted. Ubuntu started and everything is just fine, I found the empty partition in /media. But I can't put anything there, I only get an error message saying Access denied. Also, in fstab the partition is still NTFS. Why is this?

Sounds like you formatted it as NTFS--wiped out vista but left an empty partition.  You can't 'put anything there' because you can't natively write to ntfs from linux...need ntfs-3g driver for that. 

Why not do what LaRoza suggested, or reformat it as ext3 and turn it into a /home partition?

---

### Post by southernman on 2007-06-22
The /etc/fstab file is automatically created at installation time. After that, anytime you add or modify a partition you'll have to manually edit the file if you want the partition to auto mount by doing > sudo nano /etc/fstab or > gksudo gedit /etc/fstab

Would you post the output of > sudo fdisk -lsu

We'll proceed from that point by creating a mount point and manually adding the entry to your /etc/fstab and then chown the mount so that you can read, write, and delete files as needed.

---

### Post by Joakim Stokland on 2007-06-22
Wow, thanks for all the quick replies! :)

Yes, I was dual booting. I removed Windows by selecting "Format as reiserfs" in gparted. So the listing in fstab should have been changed, or so I hoped... As you mention UUID, I remember having a discussion about it in one of my previous threads. As you see, my intention wasn't to format as NTFS, I just did the whole thing wrong, because I didn't think about the UUID thing.

So, here are the outputs you requested:

blkid:
/dev/sda1: TYPE="ntfs" 
/dev/sda2: UUID="e8e1374f-8e86-490c-800e-0d3b05cbeac7" TYPE="reiserfs" 
/dev/sda5: UUID="a4943a22-0c42-4461-9b2e-4c77f381a856" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="72c58878-8014-48ce-8460-2a93cddcd4ec" TYPE="swap" 
/dev/sda7: UUID="886aa9f6-5ca8-4d2b-80f4-bd11789d7bf7" TYPE="reiserfs" 
/dev/sda8: UUID="09a20645-1186-465d-b2df-e8cbcd1e3c99" TYPE="reiserfs" 

fdisk -lsu:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    24578047    12288000   27  Unknown
/dev/sda2        24579450   126993824    51207187+  83  Linux
/dev/sda3       126993825   234436544    53721360    5  Extended
/dev/sda5       126993888   127170539       88326   83  Linux
/dev/sda6       127170603   131170724     2000061   82  Linux swap / Solaris
/dev/sda7       131170788   189759779    29294496   83  Linux
/dev/sda8       189759843   234436544    22338351   83  Linux

(Where /dev/sda2 is the partition I tried to format.)

Can you help me getting the partition up and running? I simply want it for storage, music and stuff.

Thanks again! :)

---

### Post by bodhi.zazen on 2007-06-22
If you do not mind using the command line :)

Add this to fstab (remove the old line)

> /dev/sda2 /media/sda2 auto auto,users 0 0

OR , If you want UUID :

> UUID=e8e1374f-8e86-490c-800e-0d3b05cbeac7 /media/sda2 auto auto,users 0 0

Now mount :

```
mount /media/sda2
sudo chmod 777 /media/sda2
```

Done.

---

### Post by Joakim Stokland on 2007-06-22
Yep! That did the trick! Thanks a lot! :) Now just a few questions...
Will this partition mount automatically when I reboot? (Everything in fstab mounts at bootup, right?)
Does Chmod 777 give all rights to all users?
And what exactly do the parameters in fstab do? (auto auto,users 0 0)
At the moment I have UUID's and /dev/*'s in fstab. Will this cause any trouble? Should I use only one type?

---

### Post by bodhi.zazen on 2007-06-22
> **Joakim Stokland said:**
> Yep! That did the trick! Thanks a lot! :)

woot !

>  Now just a few questions...
Will this partition mount automatically when I reboot?

Yes. That is what the "auto" in "auto,users" means

>  (Everything in fstab mounts at bootup, right?)

Not if you use "noauto" like this "unauto,users"

This users = regular users may mount. 

> Does Chmod 777 give all rights to all users?

Yes. You can chown and chmod all you like. If you want something more secure.

> And what exactly do the parameters in fstab do? (auto auto,users 0 0)

I'm glad you asked !

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

> At the moment I have UUID's and /dev/*'s in fstab. Will this cause any trouble? Should I use only one type?

You can mix and match. I think you know how to UUID or /dev now. You can also LABEL= which is helpful for removable devices (although you should not normally put removable devices like flash drives in fstab).

Enjoy :)

---

### Post by forestpixie on 2007-06-22
sorry to butt in, wouldn't normally - but I've got a similar problem

I reformatted a drive from NTFS to FAT32 and eventually  remounted it ( thanks to NeoLithium) but when I reboot it's gone.

I've changed fstab from ntfs-3g to vfat, gparted lets me mount it but then it's a no show.

sudo mount -t vfat /dev/sda5 /media/Media

mounts it so I can see it in tree view in nautilus

but it goes on reboot

---

### Post by bodhi.zazen on 2007-06-22
NP

You need to add/edit a line to fstab.

To edit fstab : ```
gksudo gedit /etc/fstab
```

Make it look like this :

> /dev/sda5 /media/Media auto auto,users,uid=1000,gid=100,umask=007 0 0

Now you can mount with ```
mount /media/Media
``` No sudo :)

And it should be there on reboot.

---

### Post by forestpixie on 2007-06-23
Thank you :D

---

### Post by Joakim Stokland on 2007-06-24
Thanks a lot! I'll read and get smarter! ;)

Joakim

---

