---
title: "PSP is read-only and nothing will change it's mind!!"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by xboxbman on 2007-04-06
I just got a 4 gig memstick for my PSP, and I'm trying to load it up will tons of goodies.  The problem is I can only write to it once, then after I unmount it to check and make sure everything transfered ok, remount it to find out I don't have permission to do anything to it.  I've found a number of posts here, and tried every solution mentioned, but nothing works.  I've tried chmod 777 on /dev/sdb , on the directory it mounts to, adding stuff to fstab, but nothing works.  While I can write to it once, I'm sending so much stuff that somethings don't send properly, so some of my games aren't working.

---

### Post by benerivo on 2007-04-06
Have you tried running nautilus as root and then navigating to it to see if you have write permissions?

---

### Post by xboxbman on 2007-04-06
> **benerivo said:**
> Have you tried running nautilus as root and then navigating to it to see if you have write permissions?

I don't have write permissions, but nothing i do will change that.  Also, dmesg gives me this :

[17194431.068000]  sdb: sdb1
[17194431.068000] sd 14:0:0:0: Attached scsi removable disk sdb
[17194431.068000] sd 14:0:0:0: Attached scsi generic sg2 type 0
[17194431.068000] usb-storage: device scan complete
[17194431.496000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17194437.368000] FAT: Filesystem panic (dev sdb1)
[17194437.368000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17194437.368000]     File system has been set read-only
[17194437.368000] FAT: Filesystem panic (dev sdb1)
[17194437.368000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17194437.368000] FAT: Filesystem panic (dev sdb1)
[17194437.368000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17194437.368000] FAT: Filesystem panic (dev sdb1)
[17194437.368000]     fat_get_cluster: invalid cluster chain (i_pos 0)
bman@wherewulf:~$ 


dunno if the filesystem panic is relevant.....

---

### Post by lukew on 2007-04-06
> **xboxbman said:**
> I don't have write permissions, but nothing i do will change that.  Also, dmesg gives me this :

[17194431.068000]  sdb: sdb1
[17194431.068000] sd 14:0:0:0: Attached scsi removable disk sdb
[17194431.068000] sd 14:0:0:0: Attached scsi generic sg2 type 0
[17194431.068000] usb-storage: device scan complete
[17194431.496000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17194437.368000] FAT: Filesystem panic (dev sdb1)
[17194437.368000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17194437.368000]     File system has been set read-only
[17194437.368000] FAT: Filesystem panic (dev sdb1)
[17194437.368000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17194437.368000] FAT: Filesystem panic (dev sdb1)
[17194437.368000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[17194437.368000] FAT: Filesystem panic (dev sdb1)
[17194437.368000]     fat_get_cluster: invalid cluster chain (i_pos 0)
bman@wherewulf:~$ 


dunno if the filesystem panic is relevant.....

your mount options will be ro; turn readonly when errors. Run fsck to check/fix them.

---

### Post by xboxbman on 2007-04-06
> **lukew said:**
> your mount options will be ro; turn readonly when errors. Run fsck to check/fix them.

cool, how would I go about doing that?  I tried a few things and fsck keeps saying no dice in different ways.  Also, how would I go about making sure these errors don't happen again?  I've formatted this stick a few times with the psp to clear it, you'd think the file system would be ok.

---

### Post by lukew on 2007-04-07
> **xboxbman said:**
> cool, how would I go about doing that?  I tried a few things and fsck keeps saying no dice in different ways.  Also, how would I go about making sure these errors don't happen again?  I've formatted this stick a few times with the psp to clear it, you'd think the file system would be ok.

For non root file system only!

Plug in the disc, identify device and unmount
	~$ df
	~$ mount
	~$ /sbin/fdisk -l

Unmount you usb connected disc. In my case:
	~$ umount /dev/sdc1

Perform a fsck.vfat check on your disc - (Check out man fsck.vfat for directions).
	$ /sbin/fsck --fy /dev/sdc1


For Root File System - need to go to run level 1. unmount all devices (except root) and check everything.
	~$ sudo init 1
	~$ sudo umount -a
	~$ fsck -fy


How to stop this in the future. Format in ext3. vfat and linux dont work too good. I had an external hd which was vfat which i would have liked accessed from my g/f's laptop. I used to back up with rsynch. Change any dir names resulting in a reasonable amount of datashitf and i would always have to run fsck. Saying that it was one of these very cheap ext ide caddys off of ebay.

Any problems get back to me.

Luke

---

### Post by Origin415 on 2007-04-07
I'm pretty sure PSP does not read ext3, so formatting is probably not a good suggestion.

---

### Post by xboxbman on 2007-04-07
> **Origin415 said:**
> I'm pretty sure PSP does not read ext3, so formatting is probably not a good suggestion.

yup, found that out the hard way.  It turns out the mem stick is a fake, so the write speed is lower.  I have to copy files one at a time.  It is extremely annoying, to say the least.  And it looks like only 2 gigs of the 4 gig stick is usable.

---

### Post by Fittersman on 2007-04-07
well i dont know if this will solve your problem or not, but you could upgrade to a custom firmware on the psp (allowing you to run homebrew and isos)

check out these sites:

lots of info updated daily --> [http://pspupdates.qj.net/](http://pspupdates.qj.net/)

help forum much like this one --> [http://forums.qj.net/f-qjnet-sony-psp-forums-48.html/](http://forums.qj.net/f-qjnet-sony-psp-forums-48.html/)

they are really good sites and will help you with any psp problems you might have 

by the way, you need a firmware of 1.50 to install hte custom firmware, but there are downgraders for those people who have anything up to 3.03, if yours is higher than 3.03, you cant downgrade as of now, but NEVER upgrade to a higher one, downgraders are always being released for higher firmwares!!

honestly, you will get so much more out of hte psp if you do this.

---

### Post by xboxbman on 2007-04-08
> **Fittersman said:**
> well i dont know if this will solve your problem or not, but you could upgrade to a custom firmware on the psp (allowing you to run homebrew and isos)

check out these sites:

lots of info updated daily --> [http://pspupdates.qj.net/](http://pspupdates.qj.net/)

help forum much like this one --> [http://forums.qj.net/f-qjnet-sony-psp-forums-48.html/](http://forums.qj.net/f-qjnet-sony-psp-forums-48.html/)

they are really good sites and will help you with any psp problems you might have 

by the way, you need a firmware of 1.50 to install hte custom firmware, but there are downgraders for those people who have anything up to 3.03, if yours is higher than 3.03, you cant downgrade as of now, but NEVER upgrade to a higher one, downgraders are always being released for higher firmwares!!

honestly, you will get so much more out of hte psp if you do this.

I already have the custom firmware, which is why i want the 4 gig stick to work.  Homebrew and isos take up a lot of room.

---

